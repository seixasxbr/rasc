---
layout: page
title: UGV-Moco
subtitle: Plataforma terrestre autônoma para inspeção de ambientes "hostis"
---
{% assign date_format = site.date_format | default: "%B %-d, %Y" %}
{%- capture site_tags -%}
    {%- for tag in site.tags -%}
      {% if tag contains 'warthog' %}
        {{- tag | first -}}{%- unless forloop.last -%},{%- endunless -%}
      {% endif %} 
    {%- endfor -%}
{%- endcapture -%}
{%- assign tags_list = site_tags | split:',' | sort -%}

<center><img style="border:5px solid black;" src="{{ 'assets/img/moco/capivara.png' | relative_url }}" text-align=center width="500" alt="Mohan" /><br></center>

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

O UGV-Mocó é uma plataforma robótica modular de pequeno porte planejado para movimentação em terrenos "hostis". A modularidade do projeto tem como objetivo a integração de vários sensores como GPS, IMU, câmeras e lidares assim como controle independente de cada uma das rodas totalmente integrados com ROS para capacidade autônoma.

<!--objetivo, data-->
O objetivo geral do projeto é o desenvolvimento de um robô móvel terrestres autônomo, também conhecido por Unmanned ground vehicle, em português Veículo terrestre não tripulado (UGV), de baixo porte para desinfecção e higienização de ambientes, sejam eles hospitalares, comerciais e empresariais.

<!--justificativa-->
Em virtude à pandemia do novo coronavírus (COVID-19) é preciso desinfectar os ambientes fechados, que mantém um fluxo de pessoas trabalhando ou transitando, para diminuir os riscos de contrair a doença e conter o avanço da disseminação. A partir disso, é possível desenvolver um robô móvel terrestres que possa realizar a desinfecção e higienização de forma eficiente do ambiente, utilizando equipamentos oriundos ou fornecidos por empreendedores brasileiros. 

A aplicação da robótica e da automação de forma mais ampla é uma resposta a ambientes ditos perigosos, como os hospitais. Neste contexto, um robô pode esterilizar superfícies e ambientes reduzindo a potencial exposição sofrida por profissionais de saúde e de higienização hospitalar. Essa atividade pode ser configurada de modo que o robô possa executar sua atividade diariamente sem intervenção humana. Portanto, essa atividade sendo feito a todo momento sem isolamento total do local torna o ambiente sempre limpo e desinfectado.

Dessa forma, de modo a diminuir ou até mesmo inibir os riscos que dos profissionais de saúde, trabalhadores de apoio (Agente de desinfecção, recepcionista, segurança, etc) e pacientes de contrair o vírus (SARS-CoV-2), além de outros patógenos que possam ser transmitidos por ar ou superfície contaminada, seria conveniente ter um dispositivo autônomo que possa transitar pelos corredores e salas a todo momento realizando o procedimento seguro de desinfecção.

<br> 

## Simulação

Simulação do moco baseado em modelo URDF (Unified robot description format) no Gazebo.

<center>

<img style="border:5px solid black;" src="{{ 'assets/img/moco/capivara_tf.png' | relative_url }}" alt="Simulação" width="550"/><br>

Simulação do projeto no *Gazebo*.
</center>


<br>


<!--equipe-->

<center><h3 class="post-title">Equipe de desenvolvimento</h3><br/></center>
<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><center><img src="{{ 'assets/img/people/matheuscerqueira-1.png' | relative_url }}" width="100" alt="israel" class="img-fluid rounded-circle" /></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/felipemohr-1.jpg' | relative_url }}" width="100" alt="lucas" class="img-fluid rounded-circle"/></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="marco" class="img-fluid rounded-circle"/></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="33.33%">Mateus Cerqueira</td>
          <td></td>
          <td width="33.33%">Felipe Mohr</td>
          <td></td>
          <td width="33.33%">Marco Reis</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Pesquisador bolsista no CC RoSA, Engenheiro Mecânico, Especialista em Robótica e Sistemas Autonônomos.</small></td>
          <td></td>
          <td style="vertical-align: top"><small>Estagiário no CC RoSA, graduando em Eng. Elétrica. Participou no desenvolvimento da simulação.</small></td>
          <td></td>
          <td style="vertical-align: top"><small>Pesquisador Sênior do projeto <br>Mestre em Engenharia de Produção e Eng. Eletricista.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>

<!-- ### Resumo do Projeto
1. Categoria: <font color="#fbb117">Robótica móvel</font>
2. Prazo: <font color="#fbb117">5 meses e 15 dias</font>
3. Data de início: <font color="#fbb117">15/01/2021</font>
4. Data de término: <font color="#fbb117">30/06/2021</font>
5. Repositório URL: [Warthog](https://github.com/Brazilian-Institute-of-Robotics/bir_warthog)
6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>
7. Recursos materiais: --
8. Apresentação URL: [Warthog-presentation](https://github.com/Brazilian-Institute-of-Robotics/bir_warthog/blob/feature/move_base_flex/warthog_docs/presentation.pdf)
9. Report URL: [Warthog-report](https://github.com/Brazilian-Institute-of-Robotics/bir_warthog/blob/feature/move_base_flex/warthog_docs/report.pdf)
10. Artigos produzidos:

<br> -->

<!-- ##### Referências
1. PÜTZ, S.; SIMÓN, J. S.; HERTZBERG, J. Move base flex a highly flexible navigation
framework for mobile robots. In: IEEE. 2018 IEEE/RSJ International Conference on
Intelligent Robots and Systems (IROS). [S.l.], 2018. p. 3416–3421.
2. COLLEDANCHISE, M.; ÖGREN, P. Behavior trees in robotics and AI: An introduction.
[S.l.]: CRC Press, 2018.


<br> -->
<!-- <hr class="mark">
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
</div> -->