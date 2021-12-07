---
layout: post
title: Controlador LQR em robô real
subtitle: Implementação do LQR em robô real via ROS e testes de sustentação by Lucas Souza 
cover-img: assets/img/bbot/equilibrium.jpeg
thumbnail-img: assets/img/bbot/bbot.png
share-img: assets/img/rosa-logo-redondo.png
comments: true
tags: [bbot]
---

<!------------------------------------------------------------------- 
>  Intro:
>    - O que foi feito?
>    - O que foi testado?
>
>  Implementação:
>    - Como foi implementado no ROS
>    - Problemas encontrados
>    - Quais mudanças foram feitas em relação á simulação
>
>  Testes:
>   - Mostrar vídeos dos testes
>
>  Conclusão:
>   - Perspectivas de resultados futuros 
>   - Ações a serem tomadas para chegar lá
------------------------------------------------------------------->

No último post, mostramos como nós projetamos um controlador LQR baseado em um modelo matemático do robô e os resultados de algumas simulações que fizemos com este controlador. Desde então, fizemos a implementação do controlador no robô real e realizamos vários testes de sustentação. Hoje, contaremos um pouco sobre esse processo de implementação, quais resultados chegamos e quais nossas perspectivas com o projeto.

## Implementação do controlador no robô real

Como mostramos no último post, nós fizemos a implementação do controlador no ROS Noetic utilizando os recursos do pacote `ros_control`. O esquema que mostramos pode ser visto logo abaixo e, caso queira saber mais sobre ele, recomendamos checar [este link](https://mhar-vell.github.io/rasc/2021-09-22-bbot-modelo-matematico/).

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/bbot-dlqr-ros-control.png' | relative_url }}" alt="Final Schematic" width="750"/>
</p>

Este esquemático engloba tanto a situação real quanto a simulada. Um modelo mais específico do real pode ser visto abaixo.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/lqr_control_sch.png' | relative_url }}" alt="Final Schematic" width="750"/>
</p>

A estrutura principal continua a mesma. Criamos um plugin do controlador LQR que se comunica com o `controller_manager` do `ros_control` e atualiza os esforços de controle com base na leitura dos estados das juntas do robô e dos sensores instalados nele. No nosso caso, apenas o IMU. A juntas do robô são definidas e comandadas pela `hardware_interface`, que se comunica diretamente com os atuadores reais do robô, realizando tarefas de escrita de comandos e leitura dos estados atuais.

A primeira modificação que é possível notar é a frequência do loop de controle, que passou a ser 80 Hz. Essa alteração foi necessária para melhorar a performance do controle. Seria ainda melhor se pudéssemos aumentar ainda mais essa frequência, porém esse foi o mais rápido que conseguimos alcançar. Isso será discutido mais a fundo ao longo do post.

Todos os nossos atuadores são motores Dynamixel, portanto a  `hardware_interface` utiliza a biblioteca DynamixelSDK para realizar a comunicação com os motores. O canal de comunicação escolhido foi um U2D2, dispositivo da ROBOTIS que permite comunicação serial via porta USB. Esta foi a maneira mais simples que tivemos para usar os Dynamixels, porém ela se mostrou bastante lenta para a nossa aplicação, sendo um dos grandes limitadores da frequência de controle. Para atingir os 80 Hz, tivemos de isolar os motores das pernas. No início do programa, a  `hardware_interface` envia a angulação das juntas das pernas mas não realiza mais a leitura delas. Logo, o controle das pernas (ainda a ser implementado) se daria em outra malha de controle. Mantendo a comunicação de leitura e escrita apenas dos dois motores das rodas, foi possível chegar até 100 Hz. O motivo de baixarmos para 80 Hz, além de manter uma margem para atrasos na comunicação, será descrito mais adiante.

Para que o controle tenha uma boa performance, é necessária uma maneira de controlar os motores que seja estável, de rápida reação e o mais linear possível. Para isso, utilizamos o modo PWM dos Dynamixels.

O algoritmo de controle que mostramos no último post inclui apenas um controlador LQR, que envia o comandos de torque direto para as rodas do robô. Isso foi suficiente para termos um ótimo resultado na simulação, mas na prática, é necessário encontrar uma relação entre o sinal de PWM do motor e o torque que ele exerce. Para isso, optamos por gerar um modelo matemático linear dos motores. Este modelo seria a relação dinâmica entre a entrada (sinal de PWM) e a saída (torque) e que pode ser representada por uma função de transferência. Para gerar esse modelo, criamos uma bancada de testes que nos permite medir o torque gerado pelo motor após enviar um sinal de PWM a ele através de uma célula de carga. Abaixo está uma foto da bancada. Nós temos um post exclusivo sobre ela que recomendamos fortemente checar [neste link](https://mhar-vell.github.io/rasc/2021-11-26-bbot-strength-test-bench/).

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/Bancada_de_Teste.png' | relative_url }}" alt="Final Schematic" width="800"/>
</p>

Após coletar os dados, utilizamos uma biblioteca de identificação de sistemas em Python chamada [SIPPY](https://github.com/CPCLAB-UNIPI/SIPPY). Ela nos permite gerar vários modelos dinâmicos em tempo discreto, tanto em função de transferência quanto em espaço e estados e de maneira simples. Nós utilizamos o modelo ARX e geramos uma função de transferência de 1ª Ordem que pode ser vista abaixo.

$$\frac{0.00002648}{z-0.8444}$$

Com o modelo do motor em mãos, o incluimos no modelo matemático do robô e projetamos outro controlador LQR. Agora, a entrada do sistema não é mais o torque das rodas e sim o sinal de PWM que enviamos para o motor. Esta etapa foi crucial, pois além de termos a relação direta entre o sinal de PWM e o torque (sempre com algumas incertezas, porém se o modelo for bom o suficiente, estes podem ser compensados ajustando o controlador), podemos projetar um LQR que considera toda a dinâmica real do motor. Nossa bancada de testes utiliza como sensor uma célula de carga de 20 kg, que faz a interface com uma Raspberry via uma placa amplificadora Hx711. Esta placa opera a, no máximo, 80Hz, que foi a frequência que utilizamos para coletar os dados e gerar o modelo do motor. Como o período de amostragem do modelo do motor e do modelo do robô tinham de ser iguais, reduzimos o loop de controle de 100 para 80 Hz.

Após a inclusão da dinâmica do motor no modelo do robô, mais um ajuste foi necessário. Para utilizar o LQR, é necessário ter o valor atual de todos os estados do modelo. Contudo, não é possível medir diretamente o torque na roda do robô enquanto ele opera. Portanto, implementamos um filtro de Kalman para estimar o valor destes novos estados (no nosso caso foram 2, pois incluimos a dinâmica de dois modelos de 1ª Ordem, cada um contendo 1 estado) com base na leitura dos outros (velocidade linear, velocidade angular em pitch, velocidade angular em yaw e ângulo em pitch). 

<!-- Os gráficos de algumas simulações com este modelo final pode ser visto abaixo. Como é possível notar, o valor estimado pelo filtro de Kalman está muito próximo do valor real do modelo não-linear  -->

## Testes

Após realizar todas as correções descritas acima, conseguimos fazer o robô se equilibrar. Ele consegue se manter estável por vários minutos e ainda se recuperar após pequenas perturbações externas. A seguir você pode checar alguns vídeos dos testes.

<center>
<iframe width="360" height="315" src="https://www.youtube.com/embed/ZBc304Rp0nM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="360" height="315" src="https://www.youtube.com/embed/p4HWfqaTFYM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

## Perspectivas Futuras

Fazer o robô se equilibrar mostra um sucesso do nosso sistema de controle e da nossa implementação. Mas o Bbot foi pensado para ser um robô que pudesse ler TAGs utilizando visão computacional e ainda navegar de forma autônoma. Para isso, é necessário melhorar sua estabilidade. Ao longo de todo o projeto recebemos várias sugestões do nosso orientador e outros colegas de como fazer isso. Listamos a seguir as principais:

1. **Deixar a estrutura do robô mais leve, retirando alguns componentes, trocando outros e distribuindo melhor o peso pela estrutura**. Toda a carcaça pode ser redesenhada para utilizar a menor quantidade de material possível. Além disso, podemos trocar os motores das pernas por Dynamixels de modelos mais leves que se adequam muito melhor a esta aplicação. Quanto à distribuição de material, a nova estrutura pode ser feita de uma forma que cada componente seja acoplado respeitando mais a simetria do robô. Isso irá evitar o deslocamento do centro de massa em relação ao ponto em que a roda toca o chão.
   
2. **Utilizar motores mais rápidos nas rodas**. Dynamixels são excelentes atuadores, são precisos e possuem muito torque, mas são muito lentos. O modelo que utilizamos foi o XM430-W210, que chega a no máximo 90 rpm. De acordo com nossas simulações e o tamanho do raio da roda do Bbot, seriam necessários pelo menos 300 rpm para ter uma velocidade de reação rápida o suficiente mais deixar o robô bem estável. Além disso, acelerar a comunicação é fundamental. Para enviar um sinal de PWM para o Dynamixel, é necessário fazer uma comunicação serial via protocolo RS-485. Seria mais rápido enviar um sinal PWM direto ao motor. 

3. **Implementar o LQR em um microcontrolador**, a fim de deixá-lo o mais rápido e preciso possível. A RaspberryPi foi suficiente para suportar com uma boa precisão um loop de controle a 80Hz. Porém, um microcontrolador é mais adequado a essa tarefa, pois podemos alcançar frequências muito maiores, aumentando a precisão do modelo discretizado, o que melhora a performance.


Estes foram alguns detalhes da nossa implementação. Tivemos bons resultados, porém sabemos que há muitos pontos de melhoria no projeto. O Bbot é um projeto em andamento e voltaremos a postar quando houver novas atualizações.

Case você queira conhecer mais sobre o Bbot, não deixe de checar nossa [página inicial](https://mhar-vell.github.io/rasc/project-bbot/)!

----------------

<br>

<!-- **************************************** Autor **************************************** -->
<center><h3 class="post-title">Autor</h3><br/></center>

<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
            <th><center><a href="https://www.linkedin.com/in/lucas-lins-souza-51b1909a/" target="_blank">
                <p align="center">
                    <img src="{{ 'assets/img/people/lucaslins-1.png' | relative_url }}" alt="Not found" width="100" class="img-fluid rounded-circle" />
                </p>
            </a></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center; margin-top: 0">
          <td width="33.33%">Lucas Lins</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top;text-align: justify;"><small>Pesquisador Júnior (estagiário) no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia Elétrica.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>

<!-- **************************************** MATH script **************************************** -->
<style TYPE="text/css">
code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}
</style>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
    tex2jax: {
        inlineMath: [['$','$'], ['\\(','\\)']],
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'] // removed 'code' entry
    }
});
MathJax.Hub.Queue(function() {
    var all = MathJax.Hub.getAllJax(), i;
    for(i = 0; i < all.length; i += 1) {
        all[i].SourceElement().parentNode.className += ' has-jax';
    }
});
</script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-AMS_HTML-full"></script>