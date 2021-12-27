---
layout: post
title: Robôs antropomórficos - Introdução ao estudo do estado da arte
subtitle:  Principais características e comparativo entre modelos
thumbnail-img: assets/img/walker/naos.jpg
cover-img: assets/img/walker/humanoides.jpg
share-img: /assets/img/rosa-logo-redondo.png
author: Brenda Alencar
comments: true
tags: [walker]
---


Robô antropomórfico é o robô que possui uma estrutura parecida com os humanos, com cabeça, tronco, mãos, pernas e pés, sendo assim ele possui habilidades que se assemelham muito com o comportamento humano, que vão além de caminhar para sentar, correr ou até mesmo pular sobre dois pés. Além disso, é esperado que humanóides desempenhem tarefas no futuro que facilitem a vida humana, como cuidar de pessoas e realizar tarefas arriscadas.

<center><img src="{{ 'assets/img/walker/boston-dynamics-saltando-degraus.gif' | relative_url }}" alt="Robô Atltas (Boston Dynamics) saltando caixas." width="500"/>
</center>

A estrutura física de humanóides é complexa, pois por possuírem braços e pernas articulados há uma grande quantidade de graus de liberdade (DOF), *Degrees of liberty*. DOF diz respeito ao conjunto de deslocamentos e rotações que um corpo pode realizar, ou seja, uma rotação sobre um eixo caracteriza um grau de liberdade,  por exemplo, o movimento de subir e descer a palma da mão demonstrado no GIF abaixo. Os robôs atuais apresentam em média 6 graus de liberdade em cada perna e 3 em cada braço, além de 2 na cabeça e 1 no tronco. Ainda sobre a estrutura, a depender do porte do humanóide, a altura pode ir de 50 cm, pequeno porte, até 150 cm, para os de grande porte, e o peso pode variar entre 3 e 80 quilos.

<center><img src="{{ 'assets/img/walker/dof-hand.gif' | relative_url }}" alt="1 DOF na mão" width="300"/>
</center>

Para realizar o movimento das juntas, os robôs são equipados com atuadores, os mais comuns são servomotores e motores *brushless*, ambos DC, mas há exceções como o Atlas, da Boston Dynamics, apresentado no GIF acima, que é equipado com motores hidraulicos junto a servo válvulas.

Com o avançar das pesquisas, robôs de alta performance apresentam movimentos elaborados e são capazes de andar por terrenos irregulares, para isso é necessário que possuam um controle robusto. Este processo envolve o planejamento dos passos, a geração da trajetória do movimento e um controle de estabilidade, para evitar que o robô caia. Para tanto, surgiram diversas abordagens para modelar e estabilizar esses robôs, como os modelos de pêndulo invertido e pêndulo linear invertido. Neste contexto, ainda são envolvidos conceitos de Centro de massa (COM), ponto de momento zero (ZMP) para estabilização do robô e filtros para corrigir erros do processo, como o de Kalman.

Abaixo será apresentado uma tabela para fins comparativos entre os modelos de robôs antropomórficos disponíveis no mercado, abordando características físicas e de desempenho.


<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-3je9{background-color:#464646;border-color:#ffffff;color:#FFF;text-align:center;vertical-align:middle}
.tg .tg-7ogr{background-color:#464646;border-color:#ffffff;color:#ffffff;text-align:center;vertical-align:top}
.tg .tg-dbpp{background-color:#464646;border-color:#ffffff;color:#ffffff;text-align:left;vertical-align:top}
</style>

<table class="tg">
<thead>
  <tr>
    <th class="tg-7ogr"><span style="font-weight:bold">Robot</span><br></th>
    <th class="tg-7ogr"><span style="font-weight:bold">Model</span></th>
    <th class="tg-7ogr"><span style="font-weight:bold">DOFs</span></th>
    <th class="tg-7ogr"><span style="font-weight:bold">Height</span></th>
    <th class="tg-7ogr"><span style="font-weight:bold">Weight</span></th>
    <th class="tg-7ogr"><span style="font-weight:bold">Developer</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-dbpp"><img src="{{ 'assets/img/walker/robot_atlas.png' | relative_url }}" width="100" alt="atlas" ></td>
    <td class="tg-3je9">Atlas</td>
    <td class="tg-3je9">28</td>
    <td class="tg-3je9">150 cm</td>
    <td class="tg-3je9">80 kg</td>
    <td class="tg-3je9">Boston Dynamics</td>
  </tr>
  <tr>
    <td class="tg-dbpp"><img src="{{ 'assets/img/walker/robot_hubo2.png' | relative_url }}" width="100" alt="hubo2" ></td>
    <td class="tg-3je9">Hubo 2</td>
    <td class="tg-3je9">40 (Neck: 3 DoF; Arm: 7 DoF x 2; Hand: 5 DoF x 2; Torso: 1 DoF; Leg: 6 DoF x 2)</td>
    <td class="tg-3je9">125 cm  </td>
    <td class="tg-3je9">45 kg</td>
    <td class="tg-3je9">KAIST (Korea Advanced INstitute of Science and Technology)</td>
  </tr>
  <tr>
    <td class="tg-dbpp"><img src="{{ 'assets/img/walker/robot_darwin.png' | relative_url }}" width="100" alt="darwin" ></td>
    <td class="tg-3je9">Darwin-OP</td>
    <td class="tg-3je9">20 (Leg: 6 DoF x 2; Arm: 3 DoF x 2; Neck: 2 DoF)</td>
    <td class="tg-3je9">45.5 cm</td>
    <td class="tg-3je9">2.9 kg</td>
    <td class="tg-3je9">Robotis</td>
  </tr>
  <tr>
    <td class="tg-dbpp"><img src="{{ 'assets/img/walker/robot_nao.png' | relative_url }}" width="100" alt="nao"></td>
    <td class="tg-3je9">NAO</td>
    <td class="tg-3je9">25 (Head: 2 DoF; Arm: 5 DoF x 2; Pelvis: 1 DoF; Leg: 5 DoF x 2; Hand: 1 DoF x 2)</td>
    <td class="tg-3je9">58 cm</td>
    <td class="tg-3je9">5.5 kg</td>
    <td class="tg-3je9">SoftBank Robotics (originally created by Aldebaran Robotics, acquired by SoftBank in 2015)</td>
  </tr> 
  <tr>
    <td class="tg-dbpp"><img src="{{ 'assets/img/walker/robot_khr3.png' | relative_url }}" width="100" alt="khr3"></td>
    <td class="tg-3je9">KHR-3</td>
    <td class="tg-3je9">22 (max)</td>
    <td class="tg-3je9">40.1 cm</td>
    <td class="tg-3je9">1.5 kg</td>
    <td class="tg-3je9">Kondo Kagaku</td>
  </tr> 
</tbody>
</table>

<br>

---------------------
<br>

<!-- autor -->
<center><h3 class="post-title">Autora</h3><br/></center>
<div class="row">
  <div class="col-xl-auto offset-xl-0 col-lg-4 offset-lg-0 center">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><img src="{{ 'assets/img/people/brendaalencar-1.png' | relative_url }}" width="100" alt="felipemohr" class="img-fluid rounded-circle" /></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td>Brenda Alencar</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Estagiária no CC RoSA, graduanda em Eng. Elétrica. Participou de projetos de Robótica Subaquática e Manipuladores Subaquáticos</small></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>
