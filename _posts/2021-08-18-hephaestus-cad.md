---
layout: post
title: CAD Hephaestus 
subtitle: A construção do desenho mecânico do Hephaestus
cover-img: assets/img/hefesto/hephaestus_wide.png
thumbnail-img: assets/img/hefesto/hephaestus.png
share-img: assets/img/rosa-logo-redondo (180).png
author: Matheus França
comments: true
tags: [hephaestus]
---

Com o dimensionamento da estrutura e o motor escolhidos, foi iniciada a parte do desenho técnico do projeto. O desenho foi todo feito no software _Fusion 360_ e exportado para o _Onshape_, o modelo serviu para a produção na impressora 3D, para os testes de liberdade de movimentação que o corpo teria e a simulação (Gazebo ROS), corrigindo eventuais erros. Depois do desenho ser feito ele é processado pelo programa da impressora 3D, que neste caso será utilizado o _Cura_, para gerar o código de máquina (código g) e assim fazer a peça propriamente dita.

<hr>

<!-- ******************************************************************************** -->
### Pé

O projeto foi iniciado pela simplificação dos dedos do pé pela sua complexidade, porém não comprometendo a marcha, assim sendo o pé vai ser uma placa sem eixos de movimentação para os dedos. 

<p align="center">
    <img id="myImg" src="{{ 'assets/img/hefesto/post-2/h-pe.png' | relative_url }}" alt="Not Found" width="400"/>
</p>

<!-- ******************************************************************************** -->
### Tornozelo

Para comportar os dois atuadores de movimentos do pé, de forma a maximizar os espaços, desenhamos um atuador na parte do tornozelo e o outro logo atrás. Podemos ver a disposição do tornozelo com o pé na figura seguinte.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/hefesto/post-2/h-tornozelo.png' | relative_url }}" alt="Not Found" width="400"/>
</p>

<!-- ******************************************************************************** -->
### Tíbia

A tíbia irá comportar tanto o motor do movimento do pé quanto o do joelho. Isso fará com que ocorra a otimização do espaço no humanoide. Para enrijecer a estrutura, utilizamos blocos que conectam as duas placas externas.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/hefesto/post-2/h-tibia.png' | relative_url }}" alt="Not Found" width="400"/>
</p>

<!-- ******************************************************************************** -->
### Joelho

No joelho é necessário apenas um grau de liberdade, portanto o sistema foi mais simples do que no tornozelo. Como já citado, o motor é alojado na tíbia. Sua transmissão é feita diretamente no eixo do motor, o que mantém uma relação de 1:1 para não mudar o torque nem a velocidade do mesmo. Apesar de sua simplicidade, o joelho é uma articulação muito demandada pela estrutura do robô.

<!-- ******************************************************************************** -->
### Coxa

A coxa utiliza o mesmo sistema do tornozelo, porém, essa junta contém um motor de alta demanda (torque maior, _Dynamixel MX-106_).

<p align="center">
    <img id="myImg" src="{{ 'assets/img/hefesto/post-2/h-coxa.png' | relative_url }}" alt="Not Found" width="400"/>
</p>

<!-- ******************************************************************************** -->
### Quadril

O quadril necessita comportar dois graus de liberdade para a perna e uma bateria para o sistema de potência do robô. 

<p align="center">
    <img id="myImg" src="{{ 'assets/img/hefesto/post-2/h-pelvis.png' | relative_url }}" alt="Not Found" width="400"/>
</p>

<!-- ******************************************************************************** -->
### Tronco

O tronco vai ser um grande bloco (sem graus de liberdade) e vai comportar a eletrônica do projeto. Terá um Giroscópio, uma Raspberry Pi e uma OpenCR, além dos atuadores da parte da cabeça e dos braços.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/hefesto/post-2/h-base-fora.png' | relative_url }}" alt="Not Found" width="300"/>
    <img id="myImg" src="{{ 'assets/img/hefesto/post-2/h-base-dentro.png' | relative_url }}" alt="Not Found" width="300"/>
</p>

<!-- ******************************************************************************** -->
### Braço

O braço vai conter 4 graus de liberdade. A mão (gripper), apesar de não ter dedos, vai ser fundamental para tarefas de manipulação de objetos. 

<p align="center">
    <img id="myImg" src="{{ 'assets/img/hefesto/post-2/h-arm.png' | relative_url }}" alt="Not Found" width="300"/>
    <img id="myImg" src="{{ 'assets/img/hefesto/post-2/h-gripper.png' | relative_url }}" alt="Not Found" width="300"/>
</p>

<!-- ******************************************************************************** -->
### Cabeça

O pescoço contém 2 graus de liberdade e comporta o sensor de visão (mynt eye s1030), uma câmera estéreo.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/hefesto/post-2/h-cabeca.png' | relative_url }}" alt="Not Found" width="400"/>
</p>

### Resultados

Nesta etapa do projeto, apresentamos o detalhamento do desenho mecânico do robô. 

<p align="center">
    <img id="myImg" src="{{ 'assets/img/hefesto/hephaestus.png' | relative_url }}" alt="Not Found" width="400"/>
</p>

Para as próximas etapas, serão apresentados a impressão e montagem do robô, assim como sua simulação e controle.

<br>
<hr>
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
          <td style="vertical-align: top;text-align: justify;"><small>Estagiário no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia de Controle e Automação.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>
