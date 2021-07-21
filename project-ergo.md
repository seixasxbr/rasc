---
layout: page
title: Ergo
subtitle: Robotic manipulator
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
    <img src="{{ 'assets/img/ergo/ergo.png' | relative_url }}" alt="Not found" width="300"/>
    <img src="{{ 'assets/img/ergo/ergo_gripper.png' | relative_url }}" alt="Not found" width="300"/>
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

**Ergo Jr** é um braço de baixo custo projetado para a educação [1], fácil de construir e modificar. Graças à programação visual, pode ser usado em escolas para realizar desde projetos pequenos a mais complexos.

Originalmente o braço robótico foi projetado pela equipe do [laboratório Flowers](https://flowers.inria.fr/), o Ergo Jr foi então adaptado por nós do <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>, para atender às necessidades de pesquisas científicas.

### DESIGN E CARACTERÍSTICAS

O **Ergo** é um braço robótico, composto por 6 motores que permitem movimentos realistas e elementos impressos em 3D. O Ergo Jr desenvolvido tem duas ferramentas para diferentes interações com seu ambiente: um abajur e um gripper.

O robô é controlado por uma placa Raspberry Pi e uma câmera o ajuda a interagir com o mundo.

### TECNOLOGIA ENVOLVIDA

O **Ergo** conta com tecnologias que o ajudam a interagir com o mundo. 

<img src="{{ 'assets/img/ergo/controladores.png' | relative_url }}" alt="Not found" width="350">{: style="float: left; padding-right: 25px;"}
<p>
O robô conta com dois controladores, o principal é um Raspberry Pi 4 e suporta o ROS Noetic, já o secundário é um OpenCR e cuida das entradas e saídas dos atuadores.
</p>


<img src="{{ 'assets/img/ergo/atuadores.png' | relative_url }}" alt="Not found" width="250">{: style="float: right; padding-left: 50px;"}
<p>
Já na parte de atuação, temos 6 <i>dynamixels MX28</i> espalhados nas diversas articulações do robô.
</p>{: style="clear: left; padding-top: 25px;"}

<p>
O <strong>Ergo</strong> conta ainda com sensor que é responsável por aquisições de dados em tempo real.
</p>{: style="clear: right; padding-top: 25px;"}

<img src="{{ 'assets/img/ergo/camera.png' | relative_url }}" alt="Not found" width="350">{: style="float: left; clear:right; padding-right: 50px;"}
<p>
A câmera RGB é capaz de detectar e codificar cores no espaço. 
</p>{: style="clear: right; padding-top: 50px;"}

<p>
</p>{: style="clear: both; white-space: pre"}
<br>

### RESULTADOS

Foi construído o projeto Ergo com os equipamentos citados e foram feitos alguns testes de movimentação tanto na estrutura real como na simulação. 

<!-- 

Os vídeos dos testes podem ser vistos a seguir. 

<video width="320" height="240" controls>
  <source src="{{ 'assets/img/ergo/dynamixel_test.mp4' | relative_url }}" type="video/mp4">
</video> 

-->

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
          <th><center><img src="{{ 'assets/img/people/breno-1.png' | relative_url }}" width="100" alt="breno" class="img-fluid rounded-circle"/></center></th>
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
1. Categoria: <font color="#fbb117">Robótica</font>
2. Prazo: <font color="#fbb117">2 meses e 17 dias</font>
3. Data de início: <font color="#fbb117">10/maio/2021</font>
4. Data de término: <font color="#fbb117">27/julho/2021</font>
5. Repositório URL: <a href="https://github.com/Brazilian-Institute-of-Robotics/bir_ergo"><font color="#fbb117">BIR Ergo</font></a>
6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>
7. Recursos materiais: <font color="#fbb117">US$ 1614,65 </font>
8. Apresentação URL: -
9. Report URL: -
10. Artigos produzidos: -

<br>

## Referências
[1] [Poppy Ergo](https://www.poppy-project.org/en/robots/poppy-ergo-jr/). **Manipulador**. Acesso em: 20 de Julho de 2021.


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