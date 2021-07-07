---
layout: page
title: Hefesto
subtitle: Humanoid Robot
---
{% assign date_format = site.date_format | default: "%B %-d, %Y" %}
{%- capture site_tags -%}
    {%- for tag in site.tags -%}
      {% if tag contains 'hefesto' %}
        {{- tag | first -}}{%- unless forloop.last -%},{%- endunless -%}
      {% endif %} 
    {%- endfor -%}
{%- endcapture -%}
{%- assign tags_list = site_tags | split:',' | sort -%}

<center><img src="{{ 'assets/img/hefesto/op3.png' | relative_url }}" text-align=center width="200" alt="op3" /><br></center>

<div class="before-content">
  <center>
    {%- for tag in tags_list -%}
      <br>
      <a href="#{{- tag -}}" class="btn btn-primary tag-btn"><i class="fas fa-tag" aria-hidden="true"></i>&nbsp;{{- tag -}}-posts&nbsp;({{site.tags[tag].size}})</a>
    {%- endfor -%}
  </center>    
  <!--hr class="mark"-->
</div>

<!-- ## Introdução -->
A robótica tem sido impulsionada pelas possibilidades da utilização de robôs para auxiliar o ser humano. O projeto de um sistema robótico humanoide visa obter uma máquina adaptada ao ambiente humano e que possa realizar tarefas para auxiliar as pessoas com maior adaptabilidade e facilidade de execução. O **Hefesto** é um projeto de robô autônomo com arquitetura aberta que visa o avanço nas tecnologias de robôs antropomórficos.

<br>

### DESIGN E CARACTERÍSTICAS

**Hefesto** conta com um _design_ articulado de 20 graus de liberdade (DOF - _Degrees of freedom_). Sua estrutura é baseada nos modelos da _Robotis_ Op3 e Op2. Além disso o **Hefesto** é desenvolvido sob ROS (Robot Operating System) para utilizar vários pacotes no ecossistema ROS. Toda tecnologia envolvida e suporte ao ROS, permitem que os desenvolvedores se concentrem mais no avanço de pesquisas e técnicas na área da robótica e visão computacional.

<br>

### TECNOLOGIA ENVOLVIDA

O **Hefesto** é equipado com uma gama de tecnologias!! 

O robô conta com dois controladores, o principal é um Raspberry Pi 4 e suporta o ROS Noetic, já o secundário é um OpenCR e cuida das entradas e saídas dos atuadores. 
<img src="{{ 'assets/img/hefesto/controladores.png' | relative_url }}" text-align=center width="800" alt="controladores" />


Já na parte de atuação, temos 2 _dynamixels MX106_ na parte da pelvis e 18 _dynamixels MX28_ espalhados nas diversas articulações do robô.
<img src="{{ 'assets/img/hefesto/atuadores.png' | relative_url }}" text-align=center width="550" alt="atuadores" />

O **hefesto** conta ainda com sensores que são responsáveis por aquisições de dados em tempo real.

A câmera RGB Stereo é capaz de detectar e codificar cores no espaço.
<img src="{{ 'assets/img/hefesto/atuadores.png' | relative_url }}" text-align=center width="400" alt="atuadores" />


O IMU detecta variações na inclinação do robô.
<img src="{{ 'assets/img/hefesto/mpu6050.jpg' | relative_url }}" text-align=center width="150" alt="mpu" />

O sistema é alimentado por uma LiPO 3s e a OpenCR distribui a energia aos componentes.
<img src="{{ 'assets/img/hefesto/lipo3s.jpeg' | relative_url }}" text-align=center width="400" alt="lipos" />

<br>
 

<!-- equipe -->
<center><h3 class="post-title">Equipe de desenvolvimento</h3><br/></center>
<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><center><img src="{{ 'assets/img/people/matheusfrança-1.png' | relative_url }}" width="100" alt="matheusfrança" class="img-fluid rounded-circle" /></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/breno-1.png' | relative_url }}" width="100" alt="breno" class="img-fluid rounded-circle"/></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="marco" class="img-fluid rounded-circle"/></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="33.33%">Anderson Queiroz</td>
          <td></td>
          <td width="33.33%">Brenda Alencar</td>
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
2. Prazo: <font color="#fbb117">02 anos</font>
3. Data de início: <font color="#fbb117">23/novembro/2020</font>
4. Data de término: <font color="#fbb117">28/outubro/2022</font>
5. Repositório URL: 
6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>
7. Recursos materiais: <font color="#fbb117">US$</font>
8. Apresentação URL:
9. Report URL: 
10. Artigos produzidos: 

<br>

## Referências

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