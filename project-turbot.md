---
layout: page
title: turBOT
subtitle: Mini Autonomous Underwater Vehicle
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

<center><img src="{{ 'assets/img/turbot/turbot-design.png' | relative_url }}" alt="Walker_missao" width="380"/></center>

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
O **turBOT** é um veículo subaquático autônomo de pequenas dimensões feito para realizar pesquisas costeiras em águas rasas. 
<!-- O projeto é concebido pela parceria  entre o SENAI CIMATEC e a Universidade de San Diego, nos Estados Unidos. -->

<!-- ## Objetivos 
    Os principais objetivos são realizar o Estudo do Estado da Arte sobre temas relacionados, confeccionar o design da estrutura externa do veículo e realizar a sua simulação CFD, implementar funcionalidades de autonomia usando a prática de simulação em tempo real e a escrita de artigos relacionados às atividades desenvolvidas ao longo do projeto. -->
    
<br>

<!-- ## Requisitos -->
## Nuances do desenvolvimento
O **turBOT** será capaz de navegar em ambientes subaquáticos de até 50 m de profundidade, o mesmo ainda terá como funcionalidade a capacidade de identificar e desviar de obstáculos.

Além disso o **turBOT** está sendo concebido para que tenha uma eficiência energética suficiente para executar por completo suas tarefas.

<br>


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
          <th><center><img src="{{ 'assets/img/people/felipemohr-1.jpg' | relative_url }}" width="100" alt="felipemohr" class="img-fluid rounded-circle"/></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="marco" class="img-fluid rounded-circle"/></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="25%"><center>Vinícius Felismino</center></td>
          <td></td>
          <td width="25%"><center>Leonardo Lima</center></td>
          <td></td>
          <td width="25%"><center>Felipe Mohr</center></td>
          <td></td>
          <td width="25%"><center>Marco Reis</center></td>
        </tr>
        <tr style="text-align:center" >
          <td width="25%" style="vertical-align: top"><small>Engenheiro Mecânico e especialista em robótica. Responsável por desenhos e simulações CFD.</small></td>
          <td></td>
          <td width="25%" style="vertical-align: top"><small>Engenheiro de Controle e Automação e especialista em robótica. Responsável pela simulação real-time.</small></td>
          <td></td>
          <td width="25%" style="vertical-align: top"><small>Estagiário no CC RoSA, graduando em Eng. Elétrica. Participou de projetos de Robótica Subaquática e Robótica Móvel</small></td>
          <td></td>
          <td width="25%" style="vertical-align: top"><small>Pesquisador Sênior do projeto <br>Mestre em Engenharia de Produção e Eng. Eletricista.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>

### Resumo do Projeto
1. Categoria: <font color="#fbb117">Robótica móvel</font>
2. Prazo: <font color="#fbb117">6 meses</font>
3. Data de início: <font color="#fbb117">05/01/2021</font>
4. Data de término: <font color="#fbb117">30/07/2021</font>
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


