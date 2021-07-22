---
layout: page
title: APEREA
subtitle: Robô autônomo diferencial
---
{% assign date_format = site.date_format | default: "%B %-d, %Y" %}
{%- capture site_tags -%}
    {%- for tag in site.tags -%}
      {% if tag contains 'aum' %}
        {{- tag | first -}}{%- unless forloop.last -%},{%- endunless -%}
      {% endif %} 
    {%- endfor -%}
{%- endcapture -%}
{%- assign tags_list = site_tags | split:',' | sort -%}

<center><img style="border:5px solid black;" src="{{ 'assets/img/aperea/aperea.png' | relative_url }}" text-align=center width="500" alt="Mohan" /><br></center>

<div class="before-content">
  <center>
    {%- for tag in tags_list -%}
      <br>
      <a href="#{{- tag -}}" class="btn btn-primary tag-btn"><i class="fas fa-tag" aria-hidden="true"></i>&nbsp;{{- tag -}}-posts&nbsp;({{site.tags[tag].size}})</a>
    {%- endfor -%}
  </center>    
  <!--hr class="mark"-->
</div>

<center>
<img src="{{ 'assets/img/aperea/aperea.png' | relative_url }}" width="300" text-align=center alt="nvidiaJetbot" />
</center>

## Mobilidade
<p style="text-align: justify;">
A junção da mobilidade com ferramentas de visão computacional e inteligência artificial proporcionam aos robôs móveis uma grande variedade de aplicações e autonomia. As aplicações incluem navegação, localização e identificação de objetos, por exemplo.{% assign date_format = site.date_format | default: "%B %-d, %Y" %}
{%- capture site_tags -%}
    {%- for tag in site.tags -%}
      {% if tag contains 'aum' %}
        {{- tag | first -}}{%- unless forloop.last -%},{%- endunless -%}
      {% endif %} 
    {%- endfor -%}
{%- endcapture -%}
{%- assign tags_list = site_tags | split:',' | sort -%}

<center><img style="border:5px solid black;" src="{{ 'assets/img/aum/mohan-model.png' | relative_url }}" text-align=center width="500" alt="Mohan" /><br></center>

<div class="before-content">
  <center>
    {%- for tag in tags_list -%}
      <br>
      <a href="#{{- tag -}}" class="btn btn-primary tag-btn"><i class="fas fa-tag" aria-hidden="true"></i>&nbsp;{{- tag -}}-posts&nbsp;({{site.tags[tag].size}})</a>
    {%- endfor -%}
  </center>    
  <!--hr class="mark"-->
</div>

O Projeto Aperea Jetbot II almeja utilizar alguns dos benefícios gerados do elo entre robótica móvel, visão computacional e I.A. Para isso será utilizada a placa Nvidia Jetson Nano em conjunto com elementos sensoriais para coletar dados do meio externo.

Conforme ilustrado na Figura abaixo, o robô deverá ser capaz de buscar e reconhecer uma tag no ambiente. A tag indicará a localização de uma bola na cor laranja. E, a partir desta informação, o robô deverá encontrar esta bola.
</p>

<center>
<img src="{{ 'assets/img/aperea/jetbot_mission.png' | relative_url }}" text-align=center alt="missao" />
</center>

<p style="text-align: justify;">
O projeto teve início em 07/05/2021, possui uma duração estimada de 58 dias e tem sua conclusão prevista para 30/07/2021. A execução deste projeto irá propor, aos seus respectivos desenvolvedores, conhecimentos direcionados a robótica móvel, além de experiências voltadas ao gerenciamento de projetos. Ambos ganhos são importantes na formação de pesquisadores e desenvolvedores com alvo em sistemas robóticos.
</p>

## Detalhamento
<p style="text-align: justify;">
O Aperea, para cumprir a sua missão, precisa realizar deslocamentos para navegar no ambiente.Conforme ilustrado abaixo, o movimento do robô será proporcionado pelas atuações dos motores TT. A implementação também será focada para atribuir uma dinâmica de um robô móvel diferencial.
Durante a navegação, o robô deve encontrar obstáculos que podem dificultar a execução da missão. Para tratar os eventuais obstáculos serão implementados sensores que ajudarão na tarefa de evita-lós.
</p>

<center>
<img src="{{ 'assets/img/aperea/esquema.png' | relative_url }}" text-align=center alt="ga" />
</center>

<p style="text-align: justify;">
O sensor ultrassônico, implementado na parte frontal do robô, proverá informação da existência de obstáculos que podem estar a frente do robô.
Um Lidar 2d, juntamente com uma câmera de profundidade Mynteye serão utilizados para tornar este sistema robótico capaz de realizar a técnica SLAM, que irá permitir a construção do mapa e localização de forma simultânea.
Afim de identificar a TAG e a esfera colorida, a câmera V2 Raspberry Pi será utilizada para captar os dados visuais do ambiente. Os dados visuais serão processados com uso da biblioteca de visão computacional OpenCV.

O processamento dos dados que serão coletados pelos sensores e câmeras será realizado pela placa Nvidia Jetson Nano. A placa conterá o sistema operacional Ubuntu 20.04, que permitirá a instalação da plataforma ROS, Robot Operation System. Também será desenvolvido um sistema de gerenciamento de energia para monitorar a carga do sistema. A tabela abaixo apresenta mais informações com relação aos principais componentes que compõem o sistema do Aperea.
</p>

### Principais Componentes

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
    <th class="tg-7ogr"><span style="font-weight:bold">Componentes</span><br></th>
    <th class="tg-7ogr"><span style="font-weight:bold">Modelo</span></th>
    <th class="tg-7ogr"><span style="font-weight:700;font-style:normal">Fabricante</span></th>
    <th class="tg-7ogr"><span style="font-weight:700;font-style:normal">Aplicação</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-dbpp"><img src="{{ 'assets/img/aperea/jetson_nano.png' | relative_url }}" width="100" alt="jetson" ></td>
    <td class="tg-3je9">Jetson Nano</td>
    <td class="tg-3je9">NVIDIA</td>
    <td class="tg-3je9">Unidade de processamento</td>
  </tr>
  <tr>
    <td class="tg-dbpp"><img src="{{ 'assets/img/aperea/cameraV2.png' | relative_url }}" width="100" alt="camerav2" ></td>
    <td class="tg-3je9">Câmera Module V2</td>
    <td class="tg-3je9">RaspberryPi</td>
    <td class="tg-3je9">Detectar a TAG e a esfera</td>
  </tr>
  <tr>
    <td class="tg-dbpp"><img src="{{ 'assets/img/aperea/mynteye.png' | relative_url }}" width="100" alt="mynteye"></td>
    <td class="tg-3je9">Câmera Stereo S1030</td>
    <td class="tg-3je9">Mynt eye</td>
    <td class="tg-3je9">Detectar obstáculos, localização e mapeamento</td>
  </tr>
  <tr>
    <td class="tg-dbpp"><img src="{{ 'assets/img/aperea/sensorultr.png' | relative_url }}" width="100" alt="sensorultr"></td>
    <td class="tg-3je9">Sensor Ultrassônico HC-SR04</td>
    <td class="tg-3je9">HC-SR04</td>
    <td class="tg-3je9">Detectar obstáculos</td>
  </tr>
  <tr>
    <td class="tg-dbpp"><img src="{{ 'assets/img/aperea/lidar.png' | relative_url }}" width="100" alt="lidar"></td>
    <td class="tg-3je9"><span style="font-weight:400;font-style:normal">Lidar LDS-01</span></td>
    <td class="tg-3je9">Robotis</td>
    <td class="tg-3je9">Mapeamento e localização</td>
  </tr>
  <tr>
    <td class="tg-dbpp"><img src="{{ 'assets/img/aperea/motordc.png' | relative_url }}" width="100" alt="motor"></td>
    <td class="tg-3je9">Motor DC 3-6v</td>
    <td class="tg-3je9">Rob</td>
    <td class="tg-3je9">Deslocamento</td>
  </tr>
</tbody>
</table>



<br/>

<center>
<h3 class="post-title">Equipe de desenvolvimento</h3><br/>
</center>
<div class="row">

<div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
<table class="table-borderless highlight">
<thead>
<tr>
<th><center><img src="{{ 'assets/img/people/juliana-1.png' | relative_url }}" width="100" alt="juliana" class="img-fluid rounded-circle" /></center></th>
<th></th>
<th><center><img src="{{ 'assets/img/people/matheusanselmo-1.png'| relative_url }}" width="100" alt="matheusanselmo" class="img-fluid rounded-circle"/></center></th>
<th></th>
<th><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="marco" class="img-fluid rounded-circle"/></center></th>
</tr>
</thead>
<tbody>
<tr class="font-weight-bolder" style="text-align: center margin-top: 0">
  <td width="33.33%">Juliana Santana</td>
  <td></td>
  <td width="33.33%">Matheus Anselmo</td>
  <td></td>
  <td width="33.33%">Marco Reis</td>
  </tr>
<tr style="text-align: center" >
<td style="vertical-align: top"><small>Pesquisadora Jr. do projeto <br>Engenheira Eletricista.</small></td>
<td></td>
<td style="vertical-align: top"><small>Pesquisador Jr. do projeto <br>Engenheiro de Controle e Automação.</small></td>
<td></td>
<td style="vertical-align: top"><small>Orientador do projeto <br>Mestre em Engenharia de Produção e Eng. Eletricista.</small></td>
</tr>
</tbody>
</table>
</div>
</div>

<br>

### Resumo do Projeto
1. Categoria: 
2. Prazo: 03 meses
3. Data de início: <font color="#fbb117">07/maio/2021</font>
4. Data de término: <font color="#fbb117">30/julho/2021</font>
5. Repositório URL: 
6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>
7. Recursos materiais: US$
8. Apresentação URL:
9. Report URL: 
10. Artigos relacionados: 

<br>

##### Referência
1. <a href="https://jetbot.org/master"><font color="#fbb117">JETBOT</font></a>. Acesso em: 4 de Junho de 2021.
