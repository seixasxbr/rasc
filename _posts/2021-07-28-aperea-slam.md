---
layout: post
title: SLAM na Simulação
subtitle: Localizar é Preciso; mapear também é Preciso by Matheus Anselmo
cover-img: /assets/img/aperea/post-week12-cover.png
thumbnail-img: /assets/img/aperea/slam-thumbnail.png
share-img: /assets/img/rosa-logo-redondo.png
comments: true
tags: [aperea]
---

## Aplicando a técnica SLAM Gmapping
<p style="text-align: justify;">
O robô APEREA para cumprir o seu objetivo precisa possuir dados sobre sua posição e orientação no espaço, localização, e também deter informações sobre o ambiente, mapeamento, pois para a navegação autônoma é crucial que os robôs tenham dados sobre sua posição e orientação.
</p>


Para obter o mapeamento e a localização do ambiente de simulação de forma simultânea,  foi utilizado o método SLAM, Simultaneous Localization And Mapping,  com  o uso do algoritmo [GMAPPING](https://iopscience.iop.org/article/10.1088/1757-899X/705/1/012037/pdf)  que utiliza os raios emitidos por uma fonte e refletidos por objetos do ambiente para criar  o mapa baseado em grade. O emissor, e também receptor, de raios que foi utilizado no APEREA é um Lidar que fornece dados para a realização do mapeamento e da localização.


<center>
  <img src="{{ 'assets/img/aperea/post_2/slam_esquematico.png' | relative_url }}" width="600" text-align=center alt="urdf1" />
</center>



Para inserir o Lidar no modelo de simulação do APEREA foi adicionado um plugin do gazebo que permite a realização da funcionalidade deste elemento sensorial e [o pacote do ROS GMAPPING](http://wiki.ros.org/gmapping) para realizar o processamento de dados. Um ambiente no gazebo foi montado para realizar os testes e verificar o resultado do SLAM no robô. O APEREA foi teleoperado, por um joystick, para navegar pelo ambiente, coletar dados do ambiente para gerar o mapa e verificar se a odometria estava correta.




<center>
  <img src="{{ 'assets/img/aperea/lidar-ray2.gif' | relative_url }}" width="600" height="400" text-align=center alt="urdf1" />
</center>



A implementação teve sucesso na geração do mapeamento e da localização simultânea. O [Frame](http://wiki.ros.org/geometry/CoordinateFrameConventions), referente ao mapa e a odometria (localização) foram correspondentes durante boa parte da simulação, o que indica que a localização e o mapeamento foram realizados de forma adequada.Nos próximos passos a localização no ambiente será usada para a realização de navegação autônoma.





<center>
  <img src="{{ 'assets/img/aperea/post_week_12.gif' | relative_url }}" width="600" height="400" text-align=center alt="urdf1" />
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