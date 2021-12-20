---
layout: post
title: Testes reais com o Bbot
subtitle: Implementação e testes do controlador PID no protótipo do Bbot 
cover-img: assets/img/bbot/bbot_wide.png
thumbnail-img: assets/img/bbot/bbot.png
share-img: assets/img/rosa-logo-redondo.png
author: Lucas Lins
comments: true
tags: [bbot]
---
<!-- ## Anteriormente
É importante que você tenha visto o post anterior [Simulação do Bbot](https://mhar-vell.github.io/rasc/2021-08-11-bbot-simulacao/), para um completo entendimento do desenvolvimento do projeto. -->

## Testes físicos

Na etapa sete do processo de construção do <a href="https://mhar-vell.github.io/rasc/project-bbot/"><font color="#fbb117">Bbot</font></a>, implementamos o controlador previamente mostrado ([Post sobre o PID](https://mhar-vell.github.io/rasc/2021-08-11-bbot-simulacao/)) no protótipo físico do robô, cuja montagem foi mostrada [aqui](https://mhar-vell.github.io/rasc/2021-08-18-bbot-processo-de-montagem/).

### Implementação do controlador

O controlador PID implementado na simulação do **Bbot** foi inteiramente baseado em ROS, o que facilitou bastante a migração para o robô físico, pois tendo um microcontrolador com o ROS instalado, basta criar uma interface entre o ROS e o *hardware* para dar vida ao robô. Na simulação, utilizamos um controlador pré-pronto do pacote **ros_control** para direção diferencial. Quando estamos simulando o sistema no Gazebo, esse controlador age via um *plugin* feito para que o Gazebo dê suporte ao **ros_control**. Contudo, no robô físico, é necessário implementar algum *software* que faça o papel deste *plugin*: transformar as informações publicadas nos tópicos em comandos para os atuadores do robô.

Como queremos que este *software* tenha suporte ao **ros_control**, utilizaremos a interface própria do pacote para esta função, que é a classe **hardware_interface**. Neste post, não iremos fazer um tutorial sobre como utilizar o **ros_control** ou como implementar uma **hardware_interface**, apenas abordaremos pontos importantes para a explicação do que foi feito no Bbot. Caso você queira saber mais sobre estes temas, pode dar uma olhada nos tutorias abaixo.

Tutoriais sobre **ros_control** e **hardware_interface**:
* [Video ROSCon 2014](https://vimeopro.com/osrfoundation/roscon-2014/video/107507546)
* [Wiki ros_control](http://wiki.ros.org/ros_control)
* [Wiki ros_control sobre **hardware_interface**](https://github.com/ros-controls/ros_control/wiki/hardware_interface)
* [Como implementar o diff_driver_controller](https://answers.ros.org/question/356894/help-to-understand-how-to-implement-diff_drive_controller/)

Quando utilizamos os controladores implementados para o **ros_control**, todos estes controladores são gerenciados pelo **controller_manager**. O **controller_manager** é responsável por criar todas as instâncias dos controladores, gerenciar todas as informações necessárias para que estes controladores funcionem devidamente e chamar a rotina de atualização dos controladores. Nesta rotina, os controladores usam as leituras fornecidas pelos sensores do robô para atualizar seus esforços de controle. Quem lê os sensores e, posteriormente, manda os novos esforços de controle para o *hardware* é a classe **hardware-interface**. Portando, devemos criar uma classe que herda as funcionalidades da **hardware-interface** e, nesta nova classe, associar cada controlador a uma junta do robô. Além disso, devemos implementar o método que faz a leitura dos sensores e o que manda o comando para o *hardware*. Nosso papel como desenvolvedores do robô é garantir o máximo possível que as leituras dos sensores estejam corretas e que o robô está respondendo adequadamente aos controles.  

Para o Bbot, nós criamos uma classe que herda a classe **hardware-interface**, registramos nela um controlador diferencial associado aos dois motores das rodas e outros 4 controladores de posição, cada um associado a um atuador nas juntas das pernas. A princípio, não fizemos uso destes controladores das pernas, apenas os utilizamos para mantermos cada junta em uma angulação fixa, como foi feito na simulação. Caso ainda não tenha ficado claro, aqui está a grande facilidade de usar ROS: como os controladores utilizam os tópicos para funcionar, todo o *software* testado em simulação pode ser trazido para a o mundo físico sem necessidade de adaptação dos códigos. Evidentemente que o mundo real é bem diferente do simulado, então ajustes de parâmetros ou configurações são sempre esperados. 

### Testes

Com o controlador devidamente implementado, começamos os testes de estabilidade. Para regular o ângulo de equilíbrio e os ganhos dos 2 PIDs, ajustamos manualmente cada um e observamos a resposta do robô. Para facilitar os testes e previnir quedas que poderiam danificar o robô, fizemos uma trilha com um arame e amarramos um gancho à cabeça do Bbot. Dessa forma, o arame irá segurá-lo, caso o controlador falhe. Abaixo estão alguns vídeos dos testes.

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/GAkndONq58M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/N26uo_ttn4Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

## Resultados

Após vários testes, mudanças de parâmetros, correção de erros... O robô não conseguiu se sustentar devidamente. A partir disso, nos surgiram muitas dúvidas:

1. Por que a simulação se mostrou tão diferente da prática?
2. Será que os motores nas rodas não possuem uma resposta rápida o suficiente para executar os esforços de controle?
3. Será que eles não possuem velocidade máxima suficiente para equilibrar o robô mais rapidamente do que ele cai?
4. Será que o robô está pesado demais?
5. Será que a implementação do nosso PID não tem um *timing* adequado ou nós que simplesmente não chegamos ainda na parametrização certa?

A princípio, apostamos na deficiência do motor. Como revisamos todos os parâmetros físicos passados no URDF, acreditamos que uma disparidade entre as juntas reais e simuladas do robô sejam a grande diferença entre nosso modelo físico e simulado. Porém esta é apenas uma hipótese e, para testá-la, devemos adotar uma abordagem mais analítica do sistema. Assim, saberemos com mais confiabilidade qual o torque e velocidade necessários para equilibrar o robô e compará-los com as especificações dos nossos motores. Portanto, decidimos interromper os testes físicos e estudar modelos matemáticos deste tipo de robô, baseado em um pêndulo invertido, para poder simulá-lo em *softwares* como Octave, MATLAB, ou até em python.

Nos próximos posts, traremos mais notícias sobre nosso estudo e as conlusões que chegamos a partir dele.

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
          <td style="vertical-align: top;text-align: justify;"><small>Estagiário no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia Elétrica.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>
