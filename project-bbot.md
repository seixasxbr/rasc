---
layout: page
title: Bbot
subtitle: Balancing Robot
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
    <img src="{{ 'assets/img/bbot/bbot.png' | relative_url }}" alt="Not found" width="200"/>
    <img src="{{ 'assets/img/bbot/bbot_stand.png' | relative_url }}" alt="Not found" width="200"/>
    <!-- <img src="assets/img/bbot/bbot.png" width="200"> -->
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

**Bbot** ou _Balancing Robot_, é um projeto de robô autônomo auto-balanceado [1]. Nosso objetivo é construir um robô móvel operado via **ROS Noetic** capaz de **se equilibrar e se deslocar sobre duas rodas**. Ademais, ele deve ser capaz de realizar a leitura de uma TAG (marco fiducial, [2]). A TAG enviará ao robô uma posição de destino à qual ele deve **navegar de forma autônoma**. Para realizar a navegação, esse robô deverá ser capaz de **criar um mapa do local onde está e se localizar nele**, permitindo-o atualizar sua posição ao longo da missão e **desviar de obstáculos** enquanto navega até seu objetivo. 

<br>

### DESIGN E CARACTERÍSTICAS

**Bbot** conta com um _design_ adequado ao seu modo de atuação. Sua baixa estatura, aproximadamente 36 cm, permite uma fácil manipulação e operação em ambientes _indoor_. Sua forte estrutura, com peças para amortecer impacto, o protegem de eventuais quedas. Além disso, boa parte da sua massa foi alocada na parte superior, o que é uma grande vantagem para robôs auto-balanceados, pois a elevação do ponto de gravidade auxilia no equilíbrio.

Outra grande vantagem do **Bbot** são suas pernas articuladas com 2 graus de liberdade[^1] .

[^1]: DOF - _Degrees of freedom_

<br>

### TECNOLOGIA ENVOLVIDA

O **Bbot** é equipado para a ação. Com seus diversos componentes ele pode realizar tarefas em ambientes indoor.

<img src="{{ 'assets/img/bbot/controladores.png' | relative_url }}" alt="Not found" width="200">{: style="float: left; padding-right: 50px;"}
<p>
O robô conta com dois controladores, o principal é um Raspberry Pi 4 e suporta o ROS Noetic, já o secundário é um OpenCM9.04 com uma placa de expansão (OpenCM 485) e cuida das entradas e saídas dos atuadores.
</p>

<img src="{{ 'assets/img/bbot/atuadores.png' | relative_url }}" alt="Not found" width="200">{: style="float: right; padding-left: 50px;"} <!--  clear:left -->
<p>
Já na parte de atuação, temos 2 <i>dynamixels MX106</i> na parte da perna e 1 <i>Nema 17</i> para locomoção da roda. As rodas são envolvidas em borracha de silicone, tornando o pneu mais aderente ao solo.
</p>{: style="clear: left; padding-top: 25px;"}

<p>
O <strong>bbot</strong> conta ainda com sensores que são responsáveis por aquisições de dados em tempo real e um sistema de <strong>controle de potência!!</strong>
</p>{: style="clear: right; padding-top: 25px;"}

<img src="{{ 'assets/img/bbot/sensores_1.png' | relative_url }}" alt="Not found" width="200">{: style="float: left; clear:right; padding-right: 50px;"}
<p>
O LiDAR (Light Detection And Ranging), é um sensor que pode revelar a geometria do ambiente ao seu redor. A câmera RGB é capaz de detectar e codificar cores no espaço.
</p>{: style="clear: right"}

<img src="{{ 'assets/img/bbot/sensores_2.png' | relative_url }}" alt="Not found" width="200">{: style="float: right; padding-left: 50px;"} <!--  clear:left -->
<p>
O IMU detecta variações na inclinação do robô e o sensor de tensão é usado para o controle de falhas.
</p>{: style="clear: left; padding-top: 25px;"}

<img src="{{ 'assets/img/bbot/pot.png' | relative_url }}" alt="Not found" width="200">{: style="float: left; clear:right; padding-right: 50px;"}
<p>
O sistema é alimentado por uma LiPO 3s e conta com uma placa para distribuir a energia aos componentes. Também comporta um regulador de tensão para energizar a Raspberry Pi 4.
</p>{: style="clear: right; padding-top: 25px;"}

<p>

</p>{: style="clear: both; white-space: pre"}

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
          <th><center><img src="{{ 'assets/img/people/lucaslins-1.png' | relative_url }}" width="100" alt="lucaslins" class="img-fluid rounded-circle"/></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="marco" class="img-fluid rounded-circle"/></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="33.33%">Matheus França</td>
          <td></td>
          <td width="33.33%">Lucas Souza</td>
          <td></td>
          <td width="33.33%">Marco Reis</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Estagiário no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia de Controle e Automação na Área 1.</small></td>
          <td></td>
          <td style="vertical-align: top"><small>Estagiário no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia Elétrica no Senai Cimatec.</small></td>
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
2. Prazo: <font color="#fbb117">2 meses e 18 dias</font>
3. Data de início: <font color="#fbb117">11/maio/2021</font>
4. Data de término: <font color="#fbb117">29/julho/2021</font>
5. Repositório URL: <a href="https://github.com/Brazilian-Institute-of-Robotics/bir_bbot"><font>Bbot</font></a>
6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>
7. Recursos materiais: <font color="#fbb117">$USD 3162,64</font>
8. Apresentação URL: <a href="https://github.com/Brazilian-Institute-of-Robotics/bir_bbot-docs"><font>Bbot-docs</font></a>
9. Report URL: <a href="https://github.com/Brazilian-Institute-of-Robotics/bir_bbot-docs/tree/doc/report"><font>Bbot-report</font></a>
10. Artigos produzidos: 

<br>

## Referências

[1] **Adam Kollarčík and Martin Gurtner**; Modeling and Control of Two-Legged Wheeled Robot; Master’s thesis, CZECH TECHNICAL UNIVERSITY IN PRAGUE. 2021.

[2] **Santos, Gabriel da Silva; Cardoso, Etevaldo; Reis, Marco Antonio dos**; "Localização de Robôs Móveis em Ambiente Internos usando Marcos Fiduciais", p. 226-233 . In: **Anais do V Simpósio Internacional de Inovação e Tecnologia**. São Paulo: Blucher, 2019.


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