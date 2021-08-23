---
layout: post
title: Montagem do APEREA 
subtitle: Uma construção de bases by Juliana Santana
cover-img: /assets/img/aperea/cover_post3.png
thumbnail-img: /assets/img/aperea/aperea-completo-rmv.png
share-img: /assets/img/rosa-logo-redondo.png
comments: true
tags: [aperea]
---
## Construindo o robô

Vimos nos posts anteriores que o Aperea possui um conjunto de sensores que irão compor o seu sistema de percepção. Estes componentes possuem diferentes formas de conexão e tipos de cabos que serão conectados na Jetson Nano.

Por conta desta característica, assim como considerando uma maior facilidade no acesso aos componentes, optou-se por construir a estrutura do robô dividida em três bases. Os desenhos destas peças foram feitas no Onshape, um software CAD, e as peças foram impressas em uma impressora 3D.

A primeira base construída foi a base 3, está base é uma das mais simples, pois nesta estarão conectados apenas o lidar e a câmera V2.

<center>
  <img src="{{ 'assets/img/aperea/base3-superior-frontal-rmv.png' | relative_url }}" width="600" text-align=center alt="urdf1" />
</center>

A conexão do lidar é feita utilizando uma interface LDS-USB. Esta interface irá passar por dentro da estrutura da base 3 através de uma abertura localizada no centro da base e ficará fixo na parte inferior desta base. Já o cabo flat, que faz a conexão da câmera V2 com a Jetson Nano, será posicionado por baixo da base 3.

<center>
  <img src="{{ 'assets/img/aperea/base3-inferior-rmv.png' | relative_url }}" width="300" text-align=center alt="urdf1" />
</center>

Na segunda base ficará a Jetson Nano, pois o seu posicionamento na base central facilita as conexões com os outros componentes. A câmera Mynt Eye também ficará nesta base, e o seu cabo será posicionado por baixo da estrutura.

<center>
  <img src="{{ 'assets/img/aperea/base2-superior-inferior-rmv.png' | relative_url }}" width="600" text-align=center alt="urdf1" />
</center>

A última base construída foi a base 1 pois nesta ficarão posicionados os componentes que estavam em processo de compra e, por conta disto, o seu design poderia sofrer modificações. Nesta base ficarão posicionados o sensor ultrassônico, os motores, o arduíno Nano, e os shields dos motores e das baterias.

<center>
  <img src="{{ 'assets/img/aperea/base1-frontal-rmv.png' | relative_url }}" width="400" text-align=center alt="urdf1" />
</center>

Para reduzir os erros de posicionamento dos furos e facilitar a organização dos componentes optou-se por construir cases para estes componentes. Desta forma, os componentes são encaixados nos cases e fixados na base por meio de parafusos.

<center>
  <img src="{{ 'assets/img/aperea/base1-superior-rmv.png' | relative_url }}" width="400" text-align=center alt="urdf1" />
</center>

Por fim, as bases são conectadas por meio das pilastras através de parafusos. Na parte inferior da estrutura além das rodas, foi colocada a bola-boba para dar estabilidade ao robô.

<center>
  <img src="{{ 'assets/img/aperea/aperea-completo-rmv.png' | relative_url }}" width="300" text-align=center alt="urdf1" />
</center>

O resultado final apresenta bons resultados no deslocamento e na praticidade dos ajustes das peças, carregamento das baterias e manutenção ou troca de componentes, caso necessário.

<!-- <center>
  <img src="{{ 'assets/img/aperea/aperea-full.gif' | relative_url }}" width="300" text-align=center alt="urdf1" />
</center> -->

<center>
  <img src="{{ 'assets/img/aperea/aperea-full2.gif' | relative_url }}" width="300" text-align=center alt="urdf1" />
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
          <th><img src="{{ 'assets/img/people/juliana-1.png' | relative_url }}" width="100" alt="juliana" class="img-fluid rounded-circle" /></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td>Juliana Santana</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Pesquisadora Jr. do projeto <br>Engenheira Eletricista.</small></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>