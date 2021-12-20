---
layout: post
title: Desenvolvimentos dos Drivers
subtitle: Integração dos Drivers no Arduino
cover-img: assets/img/hunter/post-drivers/progra.jpg
thumbnail-img: https://p1.pxfuel.com/preview/622/928/1003/wall-e-robot-toy-cute.jpg 
share-img: /assets/img/rosa-logo-redondo.png
author: Mateus Seixas
comments: true
tags: [hunter]
---

## Introdução
<p style="text-align: justify;">
Nessa etapa do desenvolvimento do projeto foram desenvolvidos os drivers dos componentes que serão conectados a unidade de processamento auxiliar do robô. Foi feita uma busca na internet dos drivers já existentes e feitas as devidas alterações para o correto funcionamento dos mesmos no projeto.
<br>

Os pinos de comunicação da Jetson Nano, que é a unidade principal de processamento do robô Hunter aonde estará operando o ROS, funcionam para níveis de tensão de até 3,3 V. Para o correto funcionamento do sensor ultrassônico HCSR-04 e o driver ponte H dupla L9110s, que alimenta os motores, é necessário que os pinos de comunicação funcionem para um nível de tensão de até 5 V. Como solução, foi decidido utilizar uma placa Arduino Pro Mini, mostrada na figura abaixo, como unidade de processamento auxiliar, pois ela possui pinos de comunicação que operam para uma tensão de até 5 V, aonde estarão conectados o sonar e a ponte H. 
</p>

<center>
  <img src="{{ 'assets/img/hunter/post-drivers/Arduino_Pro_Mini2-removebg-preview.png' | relative_url }}" width="450" text-align=center alt="img1" />
</center>

## Integração do ROS com Arduino
Para estabelecer a comunicação entre as duas unidades de processamento, é necessário utilizar um pacote chamado [rosserial](http://wiki.ros.org/rosserial), que permite que o Arduino se comunique com o ROS operando na placa Jetson Nano através da comunicação serial. A conexão entre as duas placas se da através de um  conversor FTDI, mostrado na figura abaixo. A partir disso é possível que o Arduino publique e se subscreva em tópicos. Os tópicos de comando de velocidade que o Arduino se subscreve e o tópico de distância medida pelo sensor ultrassônico  que o Arduino publica se encontram no mesmo nó, por isso é necessário que a programação do sensor ultrassônico seja feita de tal forma que não ocorra interrupção, como acontece com a função delay, encontrada na maioria das bibliotecas disponíveis.

<center>
  <img src="{{ 'assets/img/hunter/post-drivers/Screenshot_from_2021-08-10_16-12-59-removebg-preview.png' | relative_url }}" width="450" height="300" text-align=center alt="img2" />
</center>

## Resultados
Para testar o funcionamento do driver do motor junto ao sensor ultrassônico, foi conectado um joystick ao Jetson Nano e através da publicação dos comandos de velocidade vindos do controle no tópico foi possível observar o robô se deslocando de acordo com os movimentos esperados e publicando as medidas de distância calculadas. Com este teste descrito foi verificado o correto funcionamento tanto do driver do motor como do driver do sonar.

<center>
  <img src="{{ 'assets/img/hunter/post-drivers/img3.jpg' | relative_url }}" width="800" height="500" text-align=center alt="img3" />
</center>



<br>

---------------------
<br>

<!-- autor -->
<center><h3 class="post-title">Autor</h3><br/></center>
<div class="row">
  <div class="col-xl-auto offset-xl-0 col-lg-4 offset-lg-0 center">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><img src="{{ 'assets/img/people/mateusseixas-1.png' | relative_url }}" width="100" alt="mateusseixas" class="img-fluid rounded-circle" /></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td>Mateus Seixas</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Pesquisador Jr. do projeto <br>Engenheiro Eletricista</small></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>