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

<p>
<strong>Ergo Jr</strong> é um braço de baixo custo projetado para a fins didáticos <a href="#ERGO">[ERGO]</a>, fácil de construir e modificar. Graças à programação visual, pode ser usado em escolas para realizar desde projetos pequenos a mais complexos.
</p>{: style="text-align: justify;"}

<p>
Originalmente o braço robótico foi projetado pela equipe do  <a target="_blank" href="https://flowers.inria.fr/"><font color="#fbb117">laboratório Flowers</font></a>, o Ergo Jr foi então adaptado pela equipe do <a target="_blank" href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>, para atender às necessidades de pesquisas científicas.
</p>{: style="text-align: justify;"}

<br>

### DESIGN E CARACTERÍSTICAS

<p>
O <strong>Ergo</strong> é um braço robótico, composto por 6 motores e uma estrutura confeccionada por impressão 3D, que possibilita uma movimentação livre em 6 graus de liberdade. O Ergo Jr desenvolvido tem duas ferramentas para diferentes interações com seu ambiente: um abajur e um gripper (garra mecânica).
</p>{: style="text-align: justify;"}

<p>
O robô é controlado por uma placa Raspberry Pi 4 e possui uma câmera que ajuda a interagir com o mundo.
</p>{: style="text-align: justify;"}

### SEMELHANÇAS

<p>
O robô tem uma grande semelhança com o mascote da <strong><i>Pixar</i></strong>, trazendo um aspecto lúdico para interação com o público. 
</p>{: style="text-align: justify;"}

<p>
Ter um robô com tais aspectos proporciona difundir a tecnologia em lugares como escolas, a fim de incentivar o estudo e interesse à área de robótica desde o ensino primário. É possível notar também que nem sempre um projeto de engenharia e robótica, tem uma aparência de apenas fio e metal, e pode sim ter um aspecto mais próximo do público em geral.
</p>{: style="text-align: justify;"}

<p align="center">
    <img src="{{ 'assets/img/ergo/ergo.png' | relative_url }}" alt="Not found" width="250"/>
    <img src="{{ 'assets/img/ergo/pixar.png' | relative_url }}" alt="Not found" width="270"/>
</p>

### TECNOLOGIA ENVOLVIDA

O **Ergo** conta com tecnologias que o ajudam a interagir com o mundo. 

<p>
O robô conta com dois controladores, o principal é um Raspberry Pi 4 e suporta o ROS Noetic, já o secundário é um OpenCR que cuida das entradas e saídas dos atuadores.
</p>{: style="text-align: justify;"}

<p>
Já na parte de atuação, temos 6 <i>Dynamixels</i> MX-106 espalhados nas diversas articulações do robô.
</p>{: style="text-align: justify;"}

<p align="center">
    <img src="{{ 'assets/img/ergo/controladores.png' | relative_url }}" alt="Not found" width="500"/>
    <img src="{{ 'assets/img/ergo/atuadores.png' | relative_url }}" alt="Not found" width="200"/>
</p>

<p>
O <strong>Ergo</strong> conta ainda com um sensor que é responsável por aquisições de dados em tempo real.
</p>{: style="text-align: justify;"}

<p>
A câmera RGB é capaz de detectar e codificar cores no espaço. 
</p>{: style="text-align: justify;"}

<p align="center">
    <img src="{{ 'assets/img/ergo/camera.png' | relative_url }}" alt="Not found" width="350"/>
</p>

### RESULTADOS

<p>
Foi construído o <strong>projeto Ergo</strong> com os equipamentos citados e foram feitos alguns testes de movimentação tanto na estrutura real como na simulação. Os vídeos dos testes podem ser vistos a seguir. 
</p>{: style="text-align: justify;"}

<p>
A <strong>simulação</strong> a princípio mostrou sinais de instabilidade, mas depois de algumas correções no modelo disponibilizado conseguimos orientar o robô. O resultado pode ser observado no vídeo abaixo. 
</p>{: style="text-align: justify;"}

<div align="center">
<iframe width="620" height="315" src="https://www.youtube.com/embed/KsNMs92i8cs" frameborder="0" allowfullscreen></iframe>
</div>

<p>
O vídeo que se segue, demonstra os testes feitos no <strong>modelo real</strong>. E é possível ver que a estrutura foi corretamente impressa em 3d e modificada com os servos descritos (<i>Dynamixel</i> MX-106).
</p>{: style="text-align: justify;"}

<div align="center">
<iframe width="620" height="315" src="https://www.youtube.com/embed/AmQxrFoqw_w" frameborder="0" allowfullscreen></iframe>
</div>

<p>
Como o projeto do <a target="_blank" href="https://flowers.inria.fr/"><font color="#fbb117">laboratório Flowers</font></a>, não dispõe de um pacote que integrasse corretamente o framework de robótica ROS, então a nossa equipe desenvolveu algumas correções para que o robô ficasse estável no cenário simulado e real, como pode ser visto nos vídeos.
</p>{: style="text-align: justify;"}

<br>
<br>
<hr>

<!-- Equipe -->
<center><h3 class="post-title">Equipe de desenvolvimento</h3><br/></center>
<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><center><a href="https://www.linkedin.com/in/matheus-fran%C3%A7a-b62044150/" target="_blank">
                <p align="center">
                    <img src="{{ 'assets/img/people/matheusfrança-1.png' | relative_url }}" alt="Not found" width="100" class="img-fluid rounded-circle" />
                </p>
            </a></center></th>
          <th></th>
          <th><center><a href="https://www.linkedin.com/in/breno-portela-051270166/" target="_blank">
                <p align="center">
                    <img src="{{ 'assets/img/people/breno-1.png' | relative_url }}" alt="breno" width="100" class="img-fluid rounded-circle" />
                </p>
            </a></center></th>
          <th></th>
          <th><center><a href="https://mhar-vell.github.io/portfolio/" target="_blank">
                <p align="center">
                    <img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" alt="marco" width="100" class="img-fluid rounded-circle" />
                </p>
            </a></center></th>
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

##### Referências
1. <a id="ERGO" target="_blank" href="https://www.poppy-project.org/en/robots/poppy-ergo-jr/">**Poppy Ergo**</a>; **Manipulador**. Acesso em: 20 de Julho de 2021.


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
