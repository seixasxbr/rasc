---
layout: page
title: Walker
subtitle: Um robô bípede
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

<center><img src="{{ 'assets/img/walker/walker_title_yellow.png' | relative_url }}" alt="Walker_missao" width="380"/></center>

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

Um robô terrestre que se locomove sobre dois pés é classificado como bípede. Para isto, os movimentos realizados por este robô são similares a um andar antropomórfico. Movimentos antropomórficos são amplamente estudados e utilizados tanto na área medicinal como na industrial. 

<!--objetivo, data-->
O Walker faz parte da primeira fase do programa de estágio do laboratório de Robótica e Sistemas Autonômos. A iniciativa visa a construção de um robô autônomo bípede para exploração em um ambiente indoor controlado. Este projeto foi iniciado em 12 de maio de 2021 e será finalizado em 30 de julho de 2021. 

<!--justificativa-->
Um robô deste porte e com movimentação autônoma é comumente utilizado para realizar tarefas *indoor* simples e para interagir com os humanos. A elaboração e construção deste robô proporciona o aprendizado de conceitos básicos da robótica móvel e de visão computacional, como também, proporciona o embasamento para a formulação de um projeto. 

Para concepção do robô Walker, buscamos por projetos similares existentes, com o intuito de nortear nosso desenvolvimento.
A imagem a seguir ilustra as principais referências utilizadas para o projeto. 

<center>

<img src="{{ 'assets/img/walker/walker_semelhantes.png' | relative_url }}" alt="Semelhantes" /><br>

Da esquerda para direita: ROFI [1], Darwin-OP [2] e NAO [3].
</center>

<br>

### Missão

Como missão do robô Walker, ele deverá explorar uma área delimitada em busca de uma TAG.
Ao encontrá-la, ela indicará a posição de uma esfera no ambiente.
O Walker deverá, então, deslocar-se até essa posição e encontrar a esfera.
A TAG e a esfera podem ser vistas na primeira imagem. 

<br>

### Como ele fará isso?
<img src="{{ 'assets/img/walker/walker_componentes.png' | relative_url }}" alt="Walker_componentes" />
<!--<img src="/assets/img/walker/walker_componentes.png" width="250">-->

Para desempenhar suas funções, o Walker contará com alguns componentes. 
Dentre eles, os principais são:
- **Raspberry Pi 4:** Será a central de processamento do robô, controlando todo seu funcionamento
- **Dynamixels XM430:** Atuadores que irão possibilitar o deslocamento do robô sobre dois pés
- **Sensores Ultrassônicos HC-SR04:** Permitirão a detecção de obstáculos, possibilitando sua navegação autônoma
- **Raspicam:** A câmera será utilizada para a detecção e reconhecimento de TAGs, possibilitando sua localização

<br>
<!--equipe-->


<center><h3 class="post-title">Equipe de desenvolvimento</h3><br/></center>
<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><center><img src="{{ 'assets/img/people/brendaalencar-1.png' | relative_url }}" width="100" alt="brenda" class="img-fluid rounded-circle" /></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/felipemohr-1.jpg' | relative_url }}" width="100" alt="felipemohr" class="img-fluid rounded-circle"/></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="marco" class="img-fluid rounded-circle"/></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="33.33%"><center>Brenda Alencar</center></td>
          <td></td>
          <td width="33.33%"><center>Felipe Mohr</center></td>
          <td></td>
          <td width="33.33%"><center>Marco Reis</center></td>
        </tr>
        <tr style="text-align:center" >
          <td width="33.33%" style="vertical-align: top"><small>BrendaEstagiária no CC RoSA, graduanda em Eng. Elétrica. Participou de projetos de Robótica Subaquática e Manipuladores Subaquáticos</small></td>
          <td></td>
          <td width="33.33%" style="vertical-align: top"><small>Estagiário no CC RoSA, graduando em Eng. Elétrica. Participou de projetos de Robótica Subaquática e Robótica Móvel</small></td>
          <td></td>
          <td width="33.33%" style="vertical-align: top"><small>Pesquisador Sênior do projeto <br>Mestre em Engenharia de Produção e Eng. Eletricista.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>

### Resumo do Projeto
1. Categoria: <font color="#fbb117">Robótica móvel</font>
2. Prazo: <font color="#fbb117">2 meses e 18 dias</font>
3. Data de início: <font color="#fbb117">12/05/2021</font>
4. Data de término: <font color="#fbb117">30/07/2021</font>
5. Repositório URL: [Walker](https://github.com/Brazilian-Institute-of-Robotics/bir_walker)
6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>
7. Recursos materiais: --
8. Apresentação URL: [Walker-docs](https://github.com/Brazilian-Institute-of-Robotics/bir_walker-docs/tree/main)
9. Report URL: [Walker-report](https://github.com/Brazilian-Institute-of-Robotics/bir_walker-docs/tree/report-design)
10. Artigos produzidos:

<br>

## Referências
1. [ROFI](http://www.projectbiped.com/prototypes/rofi). **RObot FIve**. Acesso em: 7 de Junho de 2021 .
1. [Darwin-OP](https://emanual.robotis.com/docs/en/platform/op/getting_started). **ROBOTIS OP**. Acesso em: 7 de Junho de 2021.
1. [Nao](https://www.softbankrobotics.com/emea/en/nao). **NAO ROBOTIS SoftBank Robotics**. Acesso em: 7 de Junho de 2021.


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


Durante a etapa de detalhamento e *Design* do robô Walker, foram especificadas as Funcionalidades a serem desenvolvidas no projeto, assim como as relações entre elas. 
Isso é importante para entender o funcionamento do robô, o que ele é capaz de fazer, e como cada subsistema depende dos outros.

A imagem a seguir traz o **Diagrama de Funcionalidades** construído para o robô. Primeiramente, o robô possui o Subsistema de Energia, responsável pela alimentação de todo o sistema. O subsistema de Gestão de Dados está ali para administrar o recebimento e envio de informações entre todos os subsistemas/funcionalidades. E, claro, a Segurança é importante para garantir o seu bom funcionamento. 

<center><img src="{{ 'assets/img/walker/walker_funcionalidades.png' | relative_url }}" alt="Walker_funcionalidades" width="800"/></center>
<p/>

As funcionalidades são as seguintes:

- **Percepção:** É a funcionalidade responsável por receber os dados vindos dos sensores Ultrassônicos, IMU e Câmeras, tornando o robô capaz de perceber o ambiente a sua volta e enviando informações importantes para o funcionamento de outras funcionalidades;

- **Localização:** Através dos dados recebidos pela Percepção, o robô será capaz de se localizar no ambiente, através de sua posição e orientação;

- **Mapeamento:** Utilizando as informações da Localização, é possível criar um Mapa global do ambiente, atualizando assim a Localização do robô;

- **Planejamento:** Dada uma missão para o robô, escolhida através da Interface, o Planejamento é responsável por definir a estratégia e a trajetória que o Walker deverá seguir para cumprir seus objetivos;

- **Interface:** Essa funcionalidade torna possível ao usuário definir a missão do robô, bem como se ele deverá operar de forma autônoma ou teleoperada;

- **Comportamento:** Avalia alguns parâmetros do robô, como a carga na bateria, corrente nos motores e presença de obstáculos, enviando essas informações para a Navegação;

- **Navegação:** Na Navegação, são recebidas informações de diversas Funcionalidades, que juntas irão permitir que o Walker gere seus movimentos, enviando-os à Atuação para permitir o deslocamento seu deslocamento;

- **Atuação:** A Atuação é a funcionalidade responsável por receber os comandos para acionamento dos motores, possibilitando o deslocamento do robô. É nela também que ocorre a odometria dos motores e a leitura de corrente em cada um deles, sendo essas informaões úteis para o Comportamento e a Localização.
