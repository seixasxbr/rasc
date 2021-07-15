---
layout: page
title: Hephaestus
subtitle: Humanoid Robot
---
{% assign date_format = site.date_format | default: "%B %-d, %Y" %}
{%- capture site_tags -%}
    {%- for tag in site.tags -%}
      {% if tag contains 'bbot' %}
        {{- tag | first -}}{%- unless forloop.last -%},{%- endunless -%}
      {% endif %} 
    {%- endfor -%}
{%- endcapture -%}
{%- assign tags_list = site_tags | split:',' | sort -%}

<p align="center">
    <img src="{{ 'assets/img/hefesto/Hephaestus_front_back.png' | relative_url }}" alt="Not found" width="700"/>
</p>

<div class="before-content">
  <center>
    {%- for tag in tags_list -%}
      <a href="#{{- tag -}}" class="btn btn-primary tag-btn"><i class="fas fa-tag" aria-hidden="true"></i>&nbsp;{{- tag -}}-posts&nbsp;({{site.tags[tag].size}})</a>
    {%- endfor -%}
  </center>    
  <!--hr class="mark"-->
</div>

<!-- ## Introdução -->

A robótica tem sido impulsionada pelas possibilidades da utilização de robôs para auxiliar o ser humano. O projeto de um sistema robótico humanoide visa obter uma máquina adaptada ao ambiente humano e que possa realizar tarefas para auxiliar as pessoas com maior adaptabilidade e facilidade de execução. O **Hephaestus** é um projeto de robô autônomo com arquitetura aberta que visa o avanço nas tecnologias de robôs antropomórficos.

### DESIGN E CARACTERÍSTICAS

**Hephaestus** conta com um _design_ articulado de 22 graus de liberdade (DOF - _Degrees of freedom_). Sua estrutura é baseada nos modelos da _Robotis_ Op3 **[1]** e Op2 **[2]**. Além disso o **Hephaestus** é desenvolvido sob ROS (Robot Operating System) para utilizar vários pacotes no ecossistema ROS. Toda tecnologia envolvida e suporte ao ROS, permitem que os desenvolvedores se concentrem mais no avanço de pesquisas e técnicas na área da robótica e visão computacional.

### TECNOLOGIA ENVOLVIDA

O **Hephaestus** é equipado com uma gama de tecnologias!! 

<img src="{{ 'assets/img/hefesto/controladores.png' | relative_url }}" alt="Not found" width="300">{: style="float: left; padding-right: 25px;"}
<p>
O robô conta com dois controladores, o principal é um Raspberry Pi 4 e suporta o ROS Noetic, já o secundário é um OpenCR e cuida das entradas e saídas dos atuadores.
</p>


<img src="{{ 'assets/img/hefesto/atuadores.png' | relative_url }}" alt="Not found" width="350">{: style="float: right; padding-left: 50px;"}
<p>
Já na parte de atuação, temos 2 <i>dynamixels MX106</i> na parte da pelvis e 18 <i>dynamixels MX28</i> espalhados nas diversas articulações do robô.
</p>{: style="clear: left; padding-top: 25px;"}

<p>
O <strong>Hephaestus</strong> conta ainda com sensores que são responsáveis por aquisições de dados em tempo real.
</p>{: style="clear: right; padding-top: 25px;"}

<img src="{{ 'assets/img/hefesto/sensores_1.jpeg' | relative_url }}" alt="Not found" width="400">{: style="float: left; clear:right; padding-right: 50px;"}
<p>
A câmera RGB Stereo é capaz de detectar e codificar cores no espaço. 
</p>{: style="clear: right; padding-top: 50px;"}

<img src="{{ 'assets/img/hefesto/mpu6050.jpg' | relative_url }}" alt="Not found" width="200">{: style="float: right; padding-left: 50px; padding-top: 100px;"}
<p>
O IMU detecta variações na inclinação do robô.
</p>{: style="clear: left; padding-top: 80px;"}


<img src="{{ 'assets/img/hefesto/lipo3s.jpeg' | relative_url }}" alt="Not found" width="300">{: style="float: left; clear:right; padding-right: 50px;"}
<p>
O sistema é alimentado por uma LiPO 3s e a OpenCR distribui a energia aos componentes.
</p>{: style="clear: right; padding-top: 70px;"}

<p>
</p>{: style="clear: both; white-space: pre"}
<br>

<!-- Equipe -->
<center><h3 class="post-title">Equipe de desenvolvimento</h3><br/></center>
<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><center><img src="{{ 'assets/img/people/matheusfrança-1.png' | relative_url }}" width="100" alt="matheusfrança" class="img-fluid rounded-circle" /></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/breno-1.png' | relative_url }}" width="100" alt="lucaslins" class="img-fluid rounded-circle"/></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="marco" class="img-fluid rounded-circle"/></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="33.33%">Matheus França</td>
          <td></td>
          <td width="33.33%">Breno Portela</td>
          <td></td>
          <td width="33.33%">Marco Reis</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Estagiário no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia de Controle e Automação na Área 1.</small></td>
          <td></td>
          <td style="vertical-align: top"><small>Bolsista no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduado em Engenharia Mecânica no Senai Cimatec.</small></td>
          <td></td>
          <td style="vertical-align: top"><small>Pesquisador Sênior do projeto <br>Mestre em Engenharia de Produção e Eng. Eletricista.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>

### Resumo do Projeto
1. Categoria: <font color="#fbb117">Robótica Móvel</font>
2. Prazo: <font color="#fbb117">2 meses e 17 dias</font>
3. Data de início: <font color="#fbb117">10/maio/2021</font>
4. Data de término: <font color="#fbb117">27/julho/2021</font>
5. Repositório URL: -
6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>
7. Recursos materiais: <font color="#fbb117">US$ - </font>
8. Apresentação URL: <a href="https://github.com/Brazilian-Institute-of-Robotics/bir_poppy-docs/tree/feature/follow_up"><font>Hephaestus-docs</font></a>
9. Report URL: -
10. Artigos produzidos: -

<br>

## Referências
[1] [Robotis OP2](https://emanual.robotis.com/docs/en/platform/op2/getting_started). **ROBOTIS OP2**. Acesso em: 15 de Julho de 2021.

[2] [Robotis OP3](https://emanual.robotis.com/docs/en/platform/op3/getting_started). **ROBOTIS OP3**. Acesso em: 15 de Julho de 2021.

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
<hr class="mark">