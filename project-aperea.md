---
layout: page
title: APEREA
subtitle: Robô autônomo diferencial
---
{% assign date_format = site.date_format | default: "%B %-d, %Y" %}
{%- capture site_tags -%}
    {%- for tag in site.tags -%}
      {% if tag contains 'aperea' %}
        {{- tag | first -}}{%- unless forloop.last -%},{%- endunless -%}
      {% endif %} 
    {%- endfor -%}
{%- endcapture -%}
{%- assign tags_list = site_tags | split:',' | sort -%}

<center><img src="{{ 'assets/img/aperea/aperea.png' | relative_url }}" text-align=center width="500" alt="aperea" /><br></center>

<div class="before-content">
  <center>
    {%- for tag in tags_list -%}
      <br>
      <a href="#{{- tag -}}" class="btn btn-primary tag-btn"><i class="fas fa-tag" aria-hidden="true"></i>&nbsp;{{- tag -}}-posts&nbsp;({{site.tags[tag].size}})</a>
    {%- endfor -%}
  </center>    
  <!--hr class="mark"-->
</div>


<p style="text-align: justify;">
A junção da mobilidade com ferramentas de visão computacional e inteligência artificial proporcionam aos robôs móveis uma grande variedade de aplicações e autonomia. Dentre estas aplicações temos, por exemplo, a navegação, a localização e a identificação de objetos.
</p>
<p style="text-align: justify;">
O Projeto Aperea almeja utilizar alguns dos benefícios gerados do elo entre robótica móvel, visão computacional e I.A. Para isso será utilizada a placa Nvidia Jetson Nano em conjunto com elementos sensoriais para coletar dados do meio externo e assim, construir um robô autônomo diferencial.
</p>

## Escopo do projeto
<p style="text-align: justify;">
O projeto teve início em 10/05/2021 e tem sua conclusão prevista para 20/08/2021. A execução deste projeto irá propor, aos seus respectivos desenvolvedores, conhecimentos direcionados a robótica móvel, além de experiências voltadas ao gerenciamento de projetos. Ambos ganhos são importantes na formação de pesquisadores e desenvolvedores com alvo em sistemas robóticos.
</p>

<center>
<img src="{{ 'assets/img/aperea/jetbot_mission.png' | relative_url }}" text-align=center alt="missao" />
</center>

<p style="text-align: justify;">
A missão do robô será a localização de uma bola. Para isso, o robô deverá ser capaz de buscar e reconhecer uma tag no ambiente. A tag indicará a localização de uma bola na cor laranja. E, a partir desta informação, o robô deverá encontrar esta bola.
</p>

## Principais componentes do sistema
<p style="text-align: justify;">
A estrutura do Aperea será de um robô diferencial com um conjunto de sensores na parte frontal, um par de motores e rodas para locomoção e uma bola boba para dar estabilidade. Para fazer o gerenciamento, armazenamento e integração dos dados obtidos pelos sensores será necessário uma unidade de processamento, a qual será a placa NVIDIA Jetson Nano.
</p>

<center>
<img src="{{ 'assets/img/aperea/esquema.png' | relative_url }}" width="400" text-align=center alt="ga" />
</center>

<p style="text-align: justify;">
Durante a navegação, o robô deve encontrar obstáculos que podem dificultar a execução da missão. Para tratar os eventuais obstáculos serão implementados sensores que ajudarão na tarefa de evita-lós.
</p>
<p style="text-align: justify;">
O sensor ultrassônico, implementado na parte frontal do robô, proverá informações da existência de obstáculos que podem estar a frente do robô.
Enquanto um Lidar, juntamente com uma câmera de profundidade Mynteye serão utilizados para tornar este sistema robótico capaz de realizar a técnica SLAM, que irá permitir a construção do mapa e localização de forma simultânea.
</p>

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

<p style="text-align: justify;">
A fim de identificar a TAG e a esfera colorida, a câmera V2 Raspberry Pi será utilizada para captar os dados visuais do ambiente. Os dados visuais serão processados com uso da biblioteca de visão computacional OpenCV.
</p>
<p style="text-align: justify;">
Como mencionado anteriormente, o processamento dos dados que serão coletados pelos sensores será realizado pela placa Nvidia Jetson Nano. A placa conterá o sistema operacional Ubuntu 20.04, que permitirá a instalação da plataforma ROS, Robot Operation System, versão Noetic. 
</p>
<p style="text-align: justify;">
Também será desenvolvido um sistema de gerenciamento de energia para monitorar a carga do sistema. A tabela acima apresenta mais informações com relação aos principais componentes que compõem o sistema do Aperea.
</p>
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
2. Prazo: 04 meses
3. Data de início: <font color="#fbb117">10/maio/2021</font>
4. Data de término: <font color="#fbb117">20/agosto/2021</font>
5. Repositório URL: 
6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>
7. Recursos materiais: US$
8. Apresentação URL:
9. Report URL: 
10. Artigos relacionados: 

<br>

##### Referência
1. <a href="https://jetbot.org/master"><font color="#fbb117">JETBOT</font></a>. Acesso em: 4 de Junho de 2021.



<br>
<hr class="mark">
<div id="full-tags-list">
<h3 class="post-title"><font color="#fbb117">Posts</font></h3>
  {%- for tag in tags_list -%}
      <h4 id="{{- tag -}}" class="linked-section">
          <i class="fas fa-tag" aria-hidden="true"></i>
          &nbsp;{{- tag -}}&nbsp;({{site.tags[tag].size}})
      </h4>
      <div class="post-list">
          {%- for post in site.tags[tag] -%}
              <div class="tag-entry">
                  <a href="{{ post.url | relative_url }}">{{- post.title -}}</a>
                  <div class="entry-date">
                      <time datetime="{{- post.date | date_to_xmlschema -}}">{{- post.date | date: date_format -}}</time>
                  </div>
              </div>
          {%- endfor -%}
      </div>
  {%- endfor -%}
</div>