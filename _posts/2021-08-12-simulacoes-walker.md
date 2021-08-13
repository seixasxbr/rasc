---
layout: post
title: Modelo e Simulação do robô Walker
subtitle: Construção do URDF e implementações by Felipe Mohr
thumbnail-img: assets/img/walker/walker_urdf_thumb.png
cover-img: assets/img/walker/walker_footstep_cover.png
share-img: /assets/img/rosa-logo-redondo.png
tags: [walker]
---

Durante o desenvolvimento de um projeto de robótica, é muito comum que haja uma etapa de simulação, que geralmente ocorre em paralelo com o desenvolvimento do projeto. Isso economiza tempo e custos, possibilitando o desenvolvimento, aplicação e teste dos algoritmos do robô sem a necessidade de um protótipo físico.

Para que possamos simular um robô, precisamos primeiro de um modelo que o descreva, com todas suas partes e juntas. Então, a primeira etapa para simulação do robô Walker foi a construção de seu **[URDF](http://wiki.ros.org/urdf)** (Unified Robot Description Format).

<center><img src="{{ 'assets/img/walker/walker_urdf.png' | relative_url }}" alt="URDF do Walker" width="600"/>
</center>
<center> URDF do Walker.</center>

No URDF, podemos também adicionar a transmissão dos motores do robô e plugins para seus sensores, como é o caso do IMU, câmera e sensores ultrassônicos que utilizamos. Para que possamos visualizar todas essas informações, utilizamos o **[RViz](http://wiki.ros.org/rviz)**, uma ferramenta de visualização 3D execelente para o ROS.

<center><img src="{{ 'assets/img/walker/walker_rviz.jpeg' | relative_url }}" alt="Visualização do Walker" width="600"/>
</center>
<center> Visualização do Walker no RViz.</center>

Após criarmos o modelo para a simulação do Walker, começamos a implementar nele suas funcionalidades. Inicialmente, controlamos a posição de cada um dos 12 motores do robô, através de Cinemática Direta, para definir uma posição inicial a ele. Com isso, conseguimos definir angulações para cada uma das juntas do robô e um tempo de deslocamento, para que ele assuma a posição que desejamos de forma suave.

<center><img src="{{ 'assets/img/walker/walker_ini_pose.gif' | relative_url }}" alt="Controle de posição" width="600"/>
</center>
<center> Controle de posição do Walker.</center>

Além disso, nós utilizamos os pacotes do **[Vigir Footstep Planning](http://wiki.ros.org/vigir_footstep_planning)** (adaptando, é claro, para as dimensões e características do nosso robô) para que o Walker possa planejar seus passos, dado uma coordenada, ou melhor, um "ponto de chegada", aonde queremos que ele chegue.

<center><img src="{{ 'assets/img/walker/walker_footstep.png' | relative_url }}" alt="Planejamento de passos" width="720"/>
</center>
<center> Planejamento de passos.</center>

A próxima etapa da simulação é a implementação do balanço e das passadas do robô, fazendo com que ele possa andar e seguir o planejamento feito pelo footstep planner.


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