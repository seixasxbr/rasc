---
layout: post
title: Simulação do APEREA 
subtitle: Um desafio de navegação by Juliana Santana
cover-img: /assets/img/aperea/cover3.png
thumbnail-img: /assets/img/aperea/robot_model.png
share-img: /assets/img/rosa-logo-redondo.png
tags: [aperea]
---
## Modelando o robô
Neste post, iremos abordar sobre o [Unified Robot Description Format (URDF)](http://wiki.ros.org/urdf) ou descritivo do robô, o qual é um conjunto de arquivos em XML que descreve os elementos do robô.

A descrição do modelo do Aperea é formada por um repositório com os arquivos **meshes** correspondentes as bases, as quais foram implementadas no Onshape, e os arquivos STL dos sensores. No repositório dos **sensores** estão armazenados os arquivos XML que descrevem os sensores, os plugins e configurações do Gazebo para a simulação. Já o **modelo** refere-se ao arquivo XML que descreve todos os elementos do Aperea, como por exemplo, as sua bases, rodas e as posições dos sensores.

<center>
<img src="{{ 'assets/img/aperea/urdf1.png' | relative_url }}" text-align=center alt="urdf1" />
</center>


A partir do modelo desenvolvido no Onshape, ilustrado abaixo, foram feitas as declarações e configurações descrevendo as características do robô. O Onshape fornece algumas características como a inércia e o peso, as quais são adicionadas no arquivo do modelo do robô. 

<center>
<img src="{{ 'assets/img/aperea/assembly1.png' | relative_url }}" text-align=center alt="urdf1" />
</center>

Primeiramente, foi configurado o modelo conforme a junção das suas partes, sendo definidas as juntas e os links. A ilustração a seguir mostra, simplificadamente, os elementos do robô e a forma como estão conectados. Os retângulos correspondem aos elementos declarados como links, os quais estão conectados por meio de juntas fixas com exceção das juntas das rodas as quais são continuas. 

<center>
<img src="{{ 'assets/img/aperea/joints_and_links.png' | relative_url }}" text-align=center alt="urdf1" />
</center>

Em seguida, foram feitos ajustes nas dimensões, posicionamento e propriedades dos elementos de forma a garantir uma representação próxima a sua formatação real. Os sensores foram declarados no arquivo do modelo por meio de Xacros, os quais são macros utilizados para construir arquivos XML menores e mais legíveis.  



Por fim, o modelo obtido pode ser visualizado na imagem a seguir. Nas próximas etapas serão feitos testes com os sensores utilizando o ambiente de
simulação do Gazebo e visualizando a interação do robô com o ambiente no Rviz.

<center>
<img src="{{ 'assets/img/aperea/robot_model.png' | relative_url }}" width="500" text-align=center alt="urdf1" />
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