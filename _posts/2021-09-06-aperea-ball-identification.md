---
layout: post
title: Identificação da Esfera Colorida
subtitle: Identificando uma Esfera Colorida com visão computacional
cover-img: /assets/img/aperea/post_4/aperea_and_ball.jpg
thumbnail-img: /assets/img/aperea/slam-thumbnail.png
share-img: /assets/img/rosa-logo-redondo.png
author: Matheus Anselmo
comments: true
tags: [aperea]
---
## Visão computacional para identificação de uma esfera

<p style="text-align: justify;">
Dentro das funcionalidades que os sistemas autônomos são capazes de realizar estão inseridas a identificação e classificação de objetos. A identificação e classificação podem ser implementadas com o objetivo de realizar inspeções, acompanhamento de alguns estados e condições de elementos alvos, ao exemplo de tubos, linhas de transmissão ou até mesmo de elementos que devem ser evitados ou notados durante uma navegação/operação.
</p>
O robô  Aperea tem a capacidade de realizar identificação de tags e de uma esfera colorida.  Os dados que são coletados para processar a identificação são captados pela câmera V2 e técnicas de visão computacional são utilizadas para realizar o tratamento de dados. Para cumprir a tarefa da identificação da esfera laranja, assim como a tag, foram implementadas funcionalidades da biblioteca de visão computacional OpenCV.




A câmera v2 captura os dados da imagem  dentro do framework do ROS. Os dados coletados são passados para  o OpenCV através de uma Bridge, um tipo de  conversão para que os dados sejam tratados, e são passados por um filtro de HSV, já usando umas das funcionalidades  do OpenCV,  para coletar apenas um intervalo de cores, brilhos e saturação que corresponde  a da esfera laranja.


<center>
  <img src="{{ 'assets/img/aperea/post_4/identificacao_da_esfera.png' | relative_url }}" width="300" text-align=center alt="urdf1" />
</center>

Foi usado elementos, uma caneca azul e garrafa veremelha, com cores distintas da esfera para realizar o processo de filtragem usando  HSV.

<center>
  <img src="{{ 'assets/img/aperea/post_4/ball_and_cup.png' | relative_url }}" width="600" text-align=center alt="urdf1" />
</center>


Após o filtro, que também é comumente chamado de máscara,  tudo que está dentro dos intervalos são identificados, logo quando a esfera laranja está sendo captada pela câmera, esta será detectada. Caso contrário, nenhum elemento será demonstrado pela câmera.

<center>
  <img src="{{ 'assets/img/aperea/post_4/gif1.gif' | relative_url }}" width="900" text-align=center alt="urdf1" />
</center>  

No momento da identificação, um círculo é demonstrado  no frame da câmera. 

<center>
  <img src="{{ 'assets/img/aperea/post_4/gif2.gif' | relative_url }}" width="900" text-align=center alt="urdf1" />
</center>



A identificação da esfera é a parte final da missão que o robô Aperea tem que realizar, Logo é uma parte importante para a completude do projeto. A interseção entre as funcionalidades do ROS com OpenCV permitiu a implementação da identificação que pode ser expandida para outros objetos e que também pode ser usada para a realização de uma odometria visual, tema para um post futuro.


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
          <th><img src="{{ 'assets/img/people/matheusanselmo-1.png' | relative_url }}" width="100" alt="matheusanselmo" class="img-fluid rounded-circle" /></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td>Matheus Anselmo</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Pesquisador Jr. do projeto <br>Engenheiro de Controle e Automação.</small></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>