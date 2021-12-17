---
layout: post
title: Cinemática do Walker
subtitle: Como o robô poderá dar os passos? by Felipe Mohr
thumbnail-img: assets/img/walker/walker_kinematics_thumb.png
cover-img: assets/img/walker/walker_kinematics_cover.jpg
share-img: /assets/img/rosa-logo-redondo.png
comments: true
tags: [walker]
---

A cinemática de um robô é o estudo de seus movimentos, levando em conta apenas posição e velocidade, desconsiderando as forças e massas envolvidas. Então, o estudo da cinemática tem basicamente o objetivo de definir a posição do robô 

Em robôs antropomórficos, que possuem uma grande quantidade de juntas, como é o caso do Walker, o entendimento da cinemática é muito importante, pois precisamos definir a posição de cada um dos motores de cada perna do robô, para que ele possa assumir uma posição definida, ou dar um passo, por exemplo. 

A cinemática pode ser dividida em: 

- **Cinemática Direta:** Definimos as posições de cada uma das articulações do robô, e a partir disso calculamos a posição e orientação do que queremos (por exemplo, a posição e orientação do pé do robô) 

- **Cinemática Inversa:** A partir de uma posição e orientação desejada (por exemplo, para o pé do robô), calculamos e definimos a posição de cada junta/articulação


Através da Cinemática Direta, nós já conseguimos definir posições para cada uma das juntas, para que o robô reproduza uma postura desejada.

<center><img src="{{ 'assets/img/walker/walker_ini_pose_1.gif' | relative_url }}" alt="Cinemática Direta" width="400"/>
</center>
<center> Cinemática Direta</center>

Em conjunto com a Cinemática Inversa, há também diversos parâmetros que definimos para a geração da trajetória dos pés do robô, para que ele possa dar um passo sem se desequilibrar, como o tamanho do passo, a distância entre os pés, o quanto ele deverá levantar o pé para dar o passo, em quanto tempo o passo será dado, e diversos outros.

<center><img src="{{ 'assets/img/walker/walker_kinematics_params.jpg' | relative_url }}" alt="Cinematica inversa do passo" width="400"/>
</center>
<!-- <center> Planejamento de passos.</center> -->


No momento, o controle de passos do Walker está sendo implementado, e em breve poderemos vê-lo caminhar!

---------------------

<!-- autor -->
<center><h3 class="post-title">Autor</h3><br/></center>
<div class="row">
  <div class="col-xl-auto offset-xl-0 col-lg-4 offset-lg-0 center">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><img src="{{ 'assets/img/people/felipemohr-1.jpg' | relative_url }}" width="100" alt="felipemohr" class="img-fluid rounded-circle" /></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td>Felipe Mohr</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Estagiário no CC RoSA, graduando em Eng. Elétrica. Participou de projetos de Robótica Subaquática e Robótica Móvel</small></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>