---
layout: page
title: Doogie Mouse
subtitle: Projeto open source para ensino de robótica móvel e inteligência artificial
---
{% assign date_format = site.date_format | default: "%B %-d, %Y" %}
{%- capture site_tags -%}
    {%- for tag in site.tags -%}
      {% if tag contains 'doogie' %}
        {{- tag | first -}}{%- unless forloop.last -%},{%- endunless -%}
      {% endif %} 
    {%- endfor -%}
{%- endcapture -%}
{%- assign tags_list = site_tags | split:',' | sort -%}

<center>
<img src="{{ 'assets/img/doogie/doogies-robots.png' | relative_url }}" alt="Dois protótipos construídos" width="957"/>
</center>

<div class="before-content">
  <center>
    {%- for tag in tags_list -%}
      <br>
      <a href="#{{- tag -}}" class="btn btn-primary tag-btn"><i class="fas fa-tag" aria-hidden="true"></i>&nbsp;{{- tag -}}-posts&nbsp;({{site.tags[tag].size}})</a>
    {%- endfor -%}
  </center>    
  <!--hr class="mark"-->
</div>

O projeto Doogie Mouse foi iniciado no ano de 2019, como projeto final de graduação em engenharia de alunos do SENAI CIMATEC. Seguindo a metodologia alemã TheoPrax, o centro universitário propõe que seus alunos realizem o TCC, junto com o desenvolvimento de algum produto ou metodologia aplicado a um problema da indústria.  Dessa forma, estudantes das Engenharias Mecânica e Controle e Automação decidiram realizar o seu projeto em parceria com o Instituto Brasileiro de Robótica (BIR), conhecido por sua atuação em P&D na área de petróleo e gás e robótica underwater.

Atendendo uma necessidade do instituto, foi proposto o desenvolvimento de uma plataforma robótica que pudesse ser utilizada em seus processos internos de capacitação e qualificação de novos recursos humanos, unindo conceitos de robótica móvel e algoritmos de busca (tópicos iniciais de inteligência artificial). A partir disso que então surgiu a ideia da construção de um robô micromouse, bastante conhecido por suas competições estudantis realizadas pelo IEEE. 

Após um ano de intenso desenvolvimento e contínua interação com o instituto, o projeto culminou na elaboração de dois protótipos de robôs micromouse (ilustrado no topo da página) e um ambiente de simulação no Gazebo, conforme figura abaixo. 

<center>
<img src="{{ 'assets/img/doogie/doogie-gazebo.png' | relative_url }}" alt="Dois protótipos construídos" width="900"/>
</center>

<br>

### Missão
O robô Doogie Mouse foi criado baseado na competição Micromouse. Essa disputa é um concurso anual na qual estudantes do mundo todo desenvolvem pequenos robôs autônomos, chamados micromouse, postos a correr dentro de um labirinto. Dessa forma, o micromouse que mais rápido chegar ao seu centro é o vencedor da competição.

<br>

### Como ele fará isso?
O robô Doogie é composto de um sistema microprocessado compatı́vel com distribuições Linux; sensores de percepção que permitem a detecção de paredes ao redor do robô; sensores de posição para o controle dos movimentos e localização dentro do labirinto ; e atuadores para permitir a locomoção dentro do labirinto. Além disso, ele é equipado com bateria recarregável, conversor analógico/digital, multiplexador analógico, botões, LEDs e Buzzer. Nas imagens a seguir é mostrado cada elemento nos chassis superior e inferior do robô.

<center>
<img src="{{ 'assets/img/doogie/top-board-elementos.png' | relative_url }}" alt="Dois protótipos construídos" width="900"/>
Elementos da placa (chassi) superior
</center>

<br>

<center>
<img src="{{ 'assets/img/doogie/bottom-board-elementos.png' | relative_url }}" alt="Dois protótipos construídos" width="1000"/>
Elementos da placa (chassi) inferior
</center>

<br>
<!--equipe-->

<center><h3 class="post-title">Equipe de desenvolvimento</h3><br/></center>
<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><center><img src="{{ 'assets/img/people/caioamaral-1.png' | relative_url }}" width="100" alt="caio" class="img-fluid rounded-circle" /></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/elissonoliveira-1.png' | relative_url }}" width="100" alt="mateus" class="img-fluid rounded-circle"/></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/iurepinheiro-1.png' | relative_url }}" width="100" alt="marco" class="img-fluid rounded-circle"/></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="33.33%">Caio Amaral</td>
          <td></td>
          <td width="33.33%">Élisson Oliveira</td>
          <td></td>
          <td width="33.33%">Iure Pinheiro</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Desenvolvedor do projeto<br>Eng. Mecânico</small></td>
          <td></td>
          <td style="vertical-align: top"><small>Desenvolvedor do projeto<br>Eng. de Controle e Automação</small></td>
          <td></td>
          <td style="vertical-align: top"><small>Desenvolvedor do projeto <br>Eng. de Controle e Automação</small></td>
        </tr>
      </tbody>
    </table>
    <br>
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/mateusmenezes-2.png' | relative_url }}" width="100" alt="mateus" class="img-fluid rounded-circle"/></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="marco" class="img-fluid rounded-circle"/></center></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td></td>
          <td width="33.33%">Mateus Menezes</td>
          <td></td>
          <td width="33.33%">Marco Reis</td>
          <td></td>
        </tr>
        <tr style="text-align: center" >
          <td></td>
          <td style="vertical-align: top"><small>Gestor e Desenvolvedor do projeto<br>Mestrando em Eng. Elétrica e Eng. de Controle e Automação</small></td>
          <td></td>
          <td style="vertical-align: top"><small>Orientador do projeto <br>Mestre em Engenharia de Produção e Eng. Eletricista.</small></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>

### Resumo do Projeto
1. Categoria: <font color="#fbb117">Robótica móvel</font>
2. Prazo: <font color="#fbb117">9 meses </font>
3. Data de início: <font color="#fbb117">18/03/2019</font>
4. Data de término: <font color="#fbb117">19/12/2019</font>
5. Repositório URL: [doogie-wiki]
6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>
7. Recursos materiais: R$ 2,421,83
8. Apresentação URL: [doogie-documentation] 
9. Monografia: [doogie-documentation]
10. Artigos produzidos: [doogie-documentation]

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

[doogie-wiki]: https://github.com/Brazilian-Institute-of-Robotics/doogie/wiki
[doogie-documentation]: https://github.com/Brazilian-Institute-of-Robotics/doogie_documentation
