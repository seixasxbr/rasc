---
layout: post
title: Modelagem caixa preta para identificação de sistemas 
subtitle: Criação de bancada de testes para identificação do sistema de atuadores do Bbot by Matheus França
cover-img: assets/img/bbot/sistemas_wide.png
thumbnail-img: assets/img/bbot/iden.png
share-img: assets/img/rosa-logo-redondo.png
comments: true
tags: [bbot]
---

Identificação de Sistemas <a href="#COELHO">[COELHO, 2004]</a> é um termo genérico utilizado para descrever as ferramentas matemáticas e os algoritmos que permitem construir modelos dinâmicos a partir de dados medidos. Podemos identificar um sistema por meio de equações da física (chamado de caixa branca), podemos identificar sistemas sem conhecer o modelo prévio (modelo caixa preta) e ainda temos um método que é um meio termo entre a caixa branca e a caixa preta, chamado de caixa cinza. Para a identificação do modelo dos atuadores que serão usados no <a href="https://mhar-vell.github.io/rasc/project-bbot/"><font color="#fbb117">projeto Bbot</font></a>, vamos utilizar a modelagem caixa preta. 

## Modelo 3D

O modelo do Bbot utiliza torque como sinal de atuação das rodas, porém, o atuador do Bbot (**_Dynamixel xm430 w210_**) utiliza um sinal PWM como entrada. Então para fazer essa conversão foi necessário a criação de uma bancada de testes, no qual enviamos ao motor um sinal PWM e com uma célula de carga medimos o torque do sinal enviado. 

Tendo o funcionamento em vista, temos que modelar a bancada de forma que seja possível realizar essas coletas. Abaixo mostramos as peças detalhadamente do modelo final da bancada.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/bancada-explode.png' | relative_url }}" alt="Bancada explode" width="800"/>
</p>

A bancada final comporta um HUB que suporta os atuadores Dynamixel. Acoplado a bancada está um display de 7’’ touchscreen para o Raspberry Pi 4, isso dá autonomia para que a bancada funcione sem o uso de um computador externo. A renderização do modelo final pode ser vista a seguir.  

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/Bancada_de_Teste-new-xm.png' | relative_url }}" alt="Bancada front view" width="900"/>
</p>

A bancada pode ser facilmente modificada para acoplar outros modelos de atuadores, basta copiar o modelo feito no software **_Onshape_** neste [LINK](https://cad.onshape.com/documents/01cdebe787723337d2d1b1ac/w/ce70b1c60790b8abc436805b/e/980676df2978221cc57a94a0) e realizar as modificações desejadas. A seguir mostramos o motor do modelo Dynamixel MX-106 também acoplado a bancada. 

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/bancada.gif' | relative_url }}" alt="Bancada explode" width="800"/>
</p>

Tendo finalizado o modelo 3D da bancada, partimos agora para a modelagem do programa de identificação do sistema. 

## Identificação do sistema

A identificação do sistema está dividida em alguns passos que abordamos em seguida: 

### Coleta de dados

Com a bancada de testes montada, enviamos um sinal do tipo degrau para o atuador. O mesmo, com o HUB acoplado, faz um esforço na célula de carga. O programa então salva um arquivo (dataset) com o sinal de entrada, de saída e o tempo percorrido a cada sinal do teste. 

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/coleta-dados.png' | relative_url }}" alt="entrada" width="800"/>
</p>

### Processamento e refinamento dos dados

Com os dados coletados, carregamos num programa em Python ([LINK](https://github.com/Brazilian-Institute-of-Robotics/bir_strength-test-bench/blob/feature/dxl_command/ModelCurve/plotData.ipynb)) que vai tratar dos próximos passos. Para iniciar o refinamento, calculamos o sinal do sistema subtraindo o torque pela média dos seus valores. 

```signal = torque - np.mean(torque)```

Então, calculamos a transformada discreta de Fourier, pela biblioteca numpy ([LINK](https://numpy.org/doc/stable/reference/routines.fft.html)). A função ```np.fft.fft``` calcula a Transformada de Fourier Discreta (DFT) unidimensional com o algoritmo da Transformada Rápida de Fourier (FFT).

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/output_signal_fft.png' | relative_url }}" alt="fft" width="500"/>
</p>

Depois utilizamos o filtro FIR, que é um tipo de filtro digital caracterizado por uma resposta ao impulso que se torna nula após um tempo finito <a href="#OLIVEIRA">[OLIVEIRA, 2007]</a>. Então com o ```lfilter```, filtramos uma sequência de dados x usando um filtro digital. Para mais sobre o filtro, consultar [LINK](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.lfilter.html).

Ao final, fazemos o corte de sinais com valores abaixo de 0. Resultando no seguinte sinal:

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/output_torque_filtered.png' | relative_url }}" alt="filter" width="500"/>
</p>

### Modelo

Após os passos acima, usamos a biblioteca [SIPPY](https://github.com/CPCLAB-UNIPI/SIPPY) para identificar o sistema. O principal objetivo deste código é fornecer diferentes métodos de identificação para construir modelos lineares de sistemas dinâmicos. Para isso utilizamos como modelo interno dele o ARX (do inglês, Autoregressive with Extra Input) <a href="#RIBEIRO">[RIBEIRO]</a>. Então obtemos o seguinte modelo de primeira ordem:

<!-- MATH modelo -->
<p align="center">
$$
\frac{0.0006618}{z - 0.8444}, dt = 0.0125
$$
</p>

## Resultados 

O projeto 3D foi corretamente montado, resultando em uma bancada de autonomia própria para coleta de modelos no tipo **caixa preta**. O projeto final da bancada de teste, já montada, pode ser vista a seguir. 

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/bancada-montagem-final-1.jpeg' | relative_url }}" alt="bancada real" width="500"/>
</p>

O modelo final nos garantiu controlar o Bbot corretamente, que pode ser visto no post de controle ([LINK](https://mhar-vell.github.io/rasc/2021-11-26-bbot-first-time-standing/)). A figura a seguir mostra em laranja o sinal de entrada em torque e o azul o modelo identificado com a bancada de testes.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/output_model.png' | relative_url }}" alt="model" width="500"/>
</p>

Para baixar os códigos da bancada de testes, basta ir no [link do github](https://github.com/Brazilian-Institute-of-Robotics/bir_strength-test-bench/tree/feature/dxl_command) e seguir os passos no Readme.

### Referências

1. <a id="COELHO">COELHO, Antonio Augusto Rodrigues; DOS SANTOS COELHO, Leandro. **Identificação de sistemas dinâmicos lineares. 2004**.
1. <a id="OLIVEIRA">OLIVEIRA, EEC; CORREIA, SEN; MENDONÇA, L. M. Implementação do filtro de resposta finita (FIR) não recursivo através do método das janelas. In: **II CONGRESSO DE PESQUISA E INOVAÇÃO DA REDE NORTE NORDESTE DE EDUCAÇÃO TECNOLÓGICA**. 2007.
1. <a id="RIBEIRO">RIBEIRO, David A. et al. **Validação de modelo linear ARX com base em métodos clássicos de identificação**.


----------------

<br>
<br>

<!-- **************************************** Autor **************************************** -->
<center><h3 class="post-title">Autor</h3><br/></center>

<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
            <th><center><a href="https://www.linkedin.com/in/matheus-fran%C3%A7a-b62044150/" target="_blank">
                <p align="center">
                    <img src="{{ 'assets/img/people/matheusfrança-1.png' | relative_url }}" alt="Not found" width="100" class="img-fluid rounded-circle" />
                </p>
            </a></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center; margin-top: 0">
          <td width="33.33%">Matheus França</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top;text-align: justify;"><small>Pesquisador Júnior (estagiário) no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia de Controle e Automação.</small></td>
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