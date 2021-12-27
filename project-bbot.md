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
<p>
<strong>Bbot</strong> ou <i>Balancing Robot</i>, é um projeto de robô autônomo auto-balanceado <a href="#GURTNER">[GURTNER]</a>. Nosso objetivo é construir um robô móvel operado via <strong>ROS Noetic</strong> capaz de <strong>se equilibrar e se deslocar sobre duas rodas</strong>. Ademais, ele deve ser capaz de realizar a leitura de uma TAG (marco fiducial, <a href="#SANTOS">[SANTOS]</a>). A TAG enviará ao robô uma posição de destino à qual ele deve <strong>navegar de forma autônoma</strong>. Para realizar a navegação, esse robô deverá ser capaz de <strong>criar um mapa do local onde está e se localizar nele</strong>, permitindo-o atualizar sua posição ao longo da missão e <strong>desviar de obstáculos</strong> enquanto navega até seu objetivo. 
</p>{: style="text-align: justify;"}

<br>

### DESIGN E CARACTERÍSTICAS

<p>
O <strong>Bbot</strong> conta com um <i>design</i> adequado ao seu modo de atuação. Sua baixa estatura, aproximadamente 36 cm, permite uma fácil manipulação e operação em ambientes <i>indoor</i>. Sua forte estrutura, com peças para amortecer impacto, o protegem de eventuais quedas. Além disso, boa parte da sua massa foi alocada na parte superior, o que é uma grande vantagem para robôs auto-balanceados, pois a elevação do ponto de gravidade auxilia no equilíbrio.
</p>{: style="text-align: justify;"}

Outra grande vantagem do **Bbot** são suas pernas articuladas com 2 graus de liberdade.

<br>

### TECNOLOGIA ENVOLVIDA

<p>
O <strong>Bbot</strong> é equipado para a ação. Com seus diversos componentes ele pode realizar tarefas em ambientes indoor.
</p>{: style="text-align: justify;"}

<p style="text-align: justify;">
O robô conta com dois controladores, o principal é um Raspberry Pi 4 e suporta o ROS Noetic, já o secundário é um OpenCM9.04 com uma placa de expansão (OpenCM 485) e cuida das entradas e saídas dos atuadores.
</p>

<p>
Já na parte de atuação, temos para cada perna, 2 <i>dynamixels MX106</i> e 1 <i>dynamyxel XM430-W210</i> para locomoção da roda. As rodas são envolvidas em borracha de silicone, tornando o pneu mais aderente ao solo.
</p>{: style="text-align: justify;"}

<p align="center">
    <img src="{{ 'assets/img/bbot/controladores_atuadores.png' | relative_url }}" alt="Not found" width="750"/>
</p>

<p>
O <strong>bbot</strong> conta ainda com sensores que são responsáveis por aquisições de dados em tempo real e um sistema de <strong>controle de potência!!</strong>
</p>{: style="clear: right; padding-top: 25px; text-align: justify;"}

<p>
O LiDAR (Light Detection And Ranging), é um sensor que pode revelar a geometria do ambiente ao seu redor. A câmera RGB é capaz de detectar e codificar cores no espaço.
</p>{: style="text-align: justify;"}

<p>
O IMU detecta variações na inclinação do robô e o sensor de tensão é usado para o controle de falhas.
</p>{: style="text-align: justify;"}

<p>
O sistema é alimentado por uma LiPO 3s e conta com uma placa para distribuir a energia aos componentes. Também comporta um regulador de tensão para energizar a Raspberry Pi 4.
</p>{: style="text-align: justify;"}

<p align="center">
    <img src="{{ 'assets/img/bbot/sensores_pot.png' | relative_url }}" alt="Not found" width="750"/>
</p>

<br>

### IMPLEMENTAÇÃO DO ROBÔ SIMULADO

Com a utilização do _Gazebo - ROS_ como ferramenta de simulação do ambiente e do robô, nós conseguimos chegar na estabilidade e teleoperação do **Bbot**. Para isso, utilizamos o controlador LQR.

<center>
<iframe width="360" height="315" src="https://www.youtube.com/embed/ycF7wwak_io" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="360" height="315" src="https://www.youtube.com/embed/yk-3Swis2Z4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

Não menos importante, conseguimos tornar o robô autônomo, com a utilização de algoritmos para navegação e localização. 

<p align="center">
    <img src="{{ 'assets/img/bbot/navigation.gif' | relative_url }}" alt="Not found" width="750"/>
</p>

<br>

### IMPLEMENTAÇÃO DO ROBÔ REAL

Após a implementação e estudo para validação do modelo com a simulação, fizemos a implementação do robô real!!

<center>
<iframe width="360" height="315" src="https://www.youtube.com/embed/p4HWfqaTFYM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="360" height="315" src="https://www.youtube.com/embed/ZBc304Rp0nM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

Os testes apresentados mostram que o robô conseguese se estabilizar e aguenta pequenas perturbações.

O projeto continua em andamento e vamos seguir para a **Fase II**. Iremos fazer algumas melhorias que observamos ao decorrer desta primeira etapa de projeto (Você pode ver algumas melhorias listadas neste [LINK](https://mhar-vell.github.io/rasc/2021-11-26-bbot-first-time-standing/)). Continue atento para mais novidades!! <img src="{{ 'assets/img/bbot/bbot.png' | relative_url }}" alt="Bbot" width="17"/><img src="{{ 'assets/img/bbot/bbot.png' | relative_url }}" alt="Bbot" width="17"/>

<br>

<hr>

<br>

<!-- equipe -->
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
             <th><center><a href="https://www.linkedin.com/in/lucas-lins-souza-51b1909a/" target="_blank">
                <p align="center">
                    <img src="{{ 'assets/img/people/lucaslins-1.png' | relative_url }}" alt="Not found" width="100" class="img-fluid rounded-circle" />
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
          <td width="33.33%">Lucas Souza</td>
          <td></td>
          <td width="33.33%">Marco Reis</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top;text-align: justify;"><small>Estagiário no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia de Controle e Automação na Área 1.</small></td>
          <td></td>
          <td style="vertical-align: top;text-align: justify;"><small>Estagiário no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia Elétrica no Senai Cimatec.</small></td>
          <td></td>
          <td style="vertical-align: top;text-align: justify;"><small>Pesquisador Sênior do projeto <br>Mestre em Engenharia de Produção e Eng. Eletricista.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>

### Resumo do Projeto
1. Categoria: <font color="#fbb117">Robótica Móvel</font>
2. Prazo: <font color="#fbb117">7 meses</font>
3. Data de início: <font color="#fbb117">11/maio/2021</font>
4. Data de término: <font color="#fbb117">11/dezembro/2021</font>
5. Repositório robô real: <a href="https://github.com/Brazilian-Institute-of-Robotics/bir_bbot"><font>Bir_Bbot</font></a>
5. Repositório robô simulado: <a href="https://github.com/Brazilian-Institute-of-Robotics/bir_bbot-simulation"><font>Bir_Bbot-simulation</font></a>
6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>
7. Recursos materiais: <font color="#fbb117">$USD 3162,64</font>
8. Apresentação URL: <a href="https://github.com/Brazilian-Institute-of-Robotics/bir_bbot-docs"><font>Bbot-docs</font></a>
9. Report URL: <a href="https://github.com/Brazilian-Institute-of-Robotics/bir_bbot-docs/tree/doc/report"><font>Bbot-report</font></a>
10. Artigos produzidos: 

<br>

### Referências

1. <a id="GURTNER">**Adam Kollarčík and Martin Gurtner**</a>; Modeling and Control of Two-Legged Wheeled Robot; Master’s thesis, CZECH TECHNICAL UNIVERSITY IN PRAGUE. 2021.
1. <a id="SANTOS">**Santos, Gabriel da Silva; Cardoso, Etevaldo; Reis, Marco Antonio dos**</a>; "Localização de Robôs Móveis em Ambiente Internos usando Marcos Fiduciais", p. 226-233 . In: **Anais do V Simpósio Internacional de Inovação e Tecnologia**. São Paulo: Blucher, 2019.

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
