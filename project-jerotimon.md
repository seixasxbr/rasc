---
layout: page
title: JeRoTIMON
subtitle: Manipulator
---
{% assign date_format = site.date_format | default: "%B %-d, %Y" %}
{%- capture site_tags -%}
    {%- for tag in site.tags -%}
      {% if tag contains 'walker' %}
        {{- tag | first -}}{%- unless forloop.last -%},{%- endunless -%}
      {% endif %} 
    {%- endfor -%}
{%- endcapture -%}
{%- assign tags_list = site_tags | split:',' | sort -%}

<center><img src="{{ 'assets/img/jerotimon/jerotimon.jpeg' | relative_url }}" alt="Walker_missao" width="380"/></center>

<div class="before-content">
  <center>
    {%- for tag in tags_list -%}
      <br>
      <a href="#{{- tag -}}" class="btn btn-primary tag-btn"><i class="fas fa-tag" aria-hidden="true"></i>&nbsp;{{- tag -}}-posts&nbsp;({{site.tags[tag].size}})</a>
    {%- endfor -%}
  </center>    
  <!--hr class="mark"-->
</div>

<!-- # turBOT -->
**JeRoTIMON** é um manipulador projetado, simulado e construído com o intuito de atender demandas relacionadas ao reconhecimento de marcadores visuais e acionamento de interruptores, chaves ou botões.
<br>

<!-- ## Requisitos -->
## Nuances do desenvolvimento
Em adição ao seu propósito inicial, posteriormente este manipulador robótico foi integrado ao robô Warthog, desenvolvido pela Clearpath Robotics, com o propósito de realizar a atividade de investigação em ambiente externo, desta vez participando de uma busca e desarme de bombas sem potencial destrutivo.

O pacote de simulação do manipulador **JeRoTIMON** foi construído através do software Gazebo aliado ao MoveIt e a ferramenta de visualização Rviz, possibilitando assim que as atividades realizadas no mundo real tenham sido previamente testadas em ambiente simulado onde é possível analisar os movimentos e limitações do manipulador.
<br>

## Vídeos
### Simulação
<iframe width="560" height="315" src="https://www.youtube.com/embed/C2zw8B4PVy0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Mundo real
<iframe width="560" height="315" src="https://www.youtube.com/embed/1QWw0YnZgzc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<!-- ## Equipe -->

<center><h3 class="post-title">Equipe de desenvolvimento</h3><br/></center>

<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><center><img src="{{ 'assets/img/people/viniciusfelismino-1.png' | relative_url }}" width="100" alt="vinicius" class="img-fluid rounded-circle" /></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/leonardolima-1.png' | relative_url }}" width="100" alt="leonardo" class="img-fluid rounded-circle" /></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/jessicamotta-1.png' | relative_url }}" width="100" alt="jessica" class="img-fluid rounded-circle"/></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/miguelnery-1.png' | relative_url }}" width="100" alt="miguel" class="img-fluid rounded-circle"/></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="25%"><center>Vinícius Felismino</center></td>
          <td></td>
          <td width="25%"><center>Leonardo Lima</center></td>
          <td></td>
          <td width="25%"><center>Jéssica Motta</center></td>
          <td></td>
          <td width="25%"><center>Miguel Nery</center></td>
        </tr>
        <tr style="text-align:center" >
          <td width="25%" style="vertical-align: top"><small>Engenheiro Mecânico e especialista em robótica</small></td>
          <td></td>
          <td width="25%" style="vertical-align: top"><small>Engenheiro de Controle e Automação e especialista em robótica</small></td>
          <td></td>
          <td width="25%" style="vertical-align: top"><small>Eng. de Controle e Automação, mestre em eng. elétrica e especialista em robótica</small></td>
          <td></td>
          <td width="25%" style="vertical-align: top"><small>Engenheiro eletricista, mestrando em eng. elétrica e especialista em robótica</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><center><img src="{{ 'assets/img/people/jeanpaulo-1.png' | relative_url }}" width="100" alt="jean" class="img-fluid rounded-circle" /></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/rodrigoformiga-1.png' | relative_url }}" width="100" alt="rodrigo" class="img-fluid rounded-circle" /></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="marco" class="img-fluid rounded-circle"/></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="marco" class="img-fluid rounded-circle"/></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="25%"><center>Jean Paulo</center></td>
          <td></td>
          <td width="25%"><center>Rodrigo Formiga</center></td>
          <td></td>
          <td width="25%"><center>Tiago Souza</center></td>
          <td></td>
          <td width="25%"><center>Marco Reis</center></td>
        </tr>
        <tr style="text-align:center" >
          <td width="25%" style="vertical-align: top"><small>Engenheiro de Controle e Automação e especialista em robótica</small></td>
          <td></td>
          <td width="25%" style="vertical-align: top"><small>Engenheiro Mecânico e especialista em robótica</small></td>
          <td></td>
          <td width="25%" style="vertical-align: top"><small>Engenheiro eletricista, mestrando em eng. elétrica e orientador do projeto</small></td>
          <td></td>
          <td width="25%" style="vertical-align: top"><small>Pesquisador Sênior do projeto, mestre em Engenharia de Produção e Eng. Eletricista.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>

### Resumo do Projeto
1. Categoria: <font color="#fbb117">Manipuladores</font>
2. Prazo: <font color="#fbb117">10 meses</font>
3. Data de início: <font color="#fbb117">27/02/2020</font>
4. Data de término: <font color="#fbb117">29/11/2020</font>
5. Repositório URL: <!--[Walker](https://github.com/Brazilian-Institute-of-Robotics/bir_walker)-->
6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>
7. Recursos materiais: --
8. Apresentação URL: <!--[Walker-docs](https://github.com/Brazilian-Institute-of-Robotics/bir_walker-docs/tree/main)-->
9. Report URL: <!--[Walker-report](https://github.com/Brazilian-Institute-of-Robotics/bir_walker-docs/tree/report-design)-->
10. Artigos produzidos:

<br>

## Referências
1. 


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


<!-- ## Resultados até o momento -->



<!-- ![sw-2](https://takodana.files.wordpress.com/2016/01/star-wars-empire-strikes-back-poster.jpg?w=1024&h=1448) -->


