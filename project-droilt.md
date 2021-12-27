---
layout: page
title: DRoILT
subtitle: Robô móvel para inspeções em linhas de transmissão
---
{% assign date_format = site.date_format | default: "%B %-d, %Y" %}
{%- capture site_tags -%}
    {%- for tag in site.tags -%}
      {% if tag contains 'droilt' %}
        {{- tag | first -}}{%- unless forloop.last -%},{%- endunless -%}
      {% endif %} 
    {%- endfor -%}
{%- endcapture -%}
{%- assign tags_list = site_tags | split:',' | sort -%}

<p align="center">
    <img src="{{ 'assets/img/droilt/DRoILT3.png' | relative_url }}" alt="Not found" width="700"/>
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
A robótica é um campo relativamente jovem da tecnologia moderna que atravessa os limites da engenharia tradicional <a href="#SPONG">[SPONG]</a>. O estudo da robótica é um ramo da tecnologia que engloba área de mecânica, eletrônica e computação, com graus de teoria de controle, microeletrônica, inteligência artificial, fatores humanos e de produção <a href="#PIMENTA">[PIMENTA]</a>. Segundo <a href="#ERTHAL">[ERTHAL]</a>, o crescimento da robótica na indústria é justificado em face das exigências de maior qualidade, produtividade e flexibilidade nos processos fabris. Na área industrial, a robótica evoluiu devido a necessidade de escalabilidade de projetos e aumento de produção.

O **DRoILT** consiste no desenvolvimento de um robô móvel planar que possa se locomover em linhas de transmissão de alta potência e transpor obstáculos quando necessário. Este projeto foi realizado com o auxílio do Centro de Competência de Robótica e Sistemas Autônomos do <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">SENAI CIMATEC</font></a>.

### OBJETIVO

O objetivo deste projeto é a simulação do robô de inspeção de linhas de transmissão (LT) chamado **DRoILT** utilizando a ferramenta __Gazebo__ para o framework __ROS Noetic__. A meta é que o robô possa habitar as LT, sendo possível se locomover e transpor obstáculos autonomamente, e que possa realizar a inspeção visual destas LT enquanto energizadas.

### DESIGN E CARACTERÍSTICAS

O robô utilizará um sistema de navegação e localização simultâneos com técnicas de __Voxel-grid__ para seu mapeamento em 2D e identificação detalhada dos obstáculos presentes na linha. Também possuirá sensores visuais (mynt eye s1030) para auxiliar a odometria gerada pelas rodas e a identificação dos problemas que a LT possui.

<p align="center">
    <img src="{{ 'assets/img/droilt/mynt.png' | relative_url }}" alt="Not found" width="400"/>
</p>

O robô apresentado, **DRoILT**, tem uma formação mecânica divida em 3 partes: traseira, frontal e central. As partes frontais e traseiras contam com seu sistema de tração exclusivo para auxiliar o robô a manter o seu centro de gravidade estável durante a movimentação ou transposição. 

<p align="center">
    <img src="{{ 'assets/img/droilt/droilt_l_mod.png' | relative_url }}" alt="Not found" width="350"/>
    <img src="{{ 'assets/img/droilt/droilt_r_mod.png' | relative_url }}" alt="Not found" width="350"/>
    <img src="{{ 'assets/img/droilt/droilt_c_mod.png' | relative_url }}" alt="Not found" width="350"/>
</p>

Suas medidas por completo podem ser vistas na figura seguinte. Ele é um robô móvel planar que se movimenta nas linhas de transmissão utilizando 5 roldanas alocadas em seus suportes. A movimentação deste robô utiliza 3 controladores de velocidade, para que as 3 divisões mecânicas atuem independentemente. A base, localizada na parte central, tem as dimensões necessárias para inclusão de uma bateria, uma central de controle e sensores de localização e de ajustes inerciais. Suas dimensões externas totalizam aproximadamente 1680 x 140 x 650 mm. A modularidade do sistema faz com que seja possível a adição de novos sensores como LiDAR e câmeras estéreo.

<p align="center">
    <img src="{{ 'assets/img/droilt/DRoILT2.png' | relative_url }}" alt="Not found" width="750"/>
</p>

Já na parte de atuação, temos dois tipos, os __dynamixels MX106__ e __dynamyxel MX28__ para locomoção das roldanas e do braço robótico. 

<p align="center">
    <img src="{{ 'assets/img/droilt/mx106.png' | relative_url }}" alt="Not found" width="200"/>
    <img src="{{ 'assets/img/droilt/mx28.png' | relative_url }}" alt="Not found" width="300"/>
</p>

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
             <th><center><a href="https://www.linkedin.com/in/jean-paulo-990594127/" target="_blank">
                <p align="center">
                    <img src="{{ 'assets/img/people/jeanpaulo-1.png' | relative_url }}" alt="Not found" width="100" class="img-fluid rounded-circle" />
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
          <td width="33.33%">Jean Paulo</td>
          <td></td>
          <td width="33.33%">Marco Reis</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top;text-align: justify;"><small>Estagiário no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia de Controle e Automação na Área 1.</small></td>
          <td></td>
          <td style="vertical-align: top;text-align: justify;"><small>Mestrando em Engenharia mecatrônica na UFBA</small></td>
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
2. Prazo: <font color="#fbb117">5 meses e 10 dias</font>
3. Data de início: <font color="#fbb117">18/janeiro/2021</font>
4. Data de término: <font color="#fbb117">28/junho/2021</font>
5. Repositório URL: <a href="https://github.com/Brazilian-Institute-of-Robotics/bir_droilt"><font>DRoILT</font></a>
6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>
7. Recursos materiais: <font color="#fbb117">$USD --</font>
8. Apresentação URL: <a href="https://github.com/Brazilian-Institute-of-Robotics/bir_droilt-docs/tree/main/Presentation"><font>Droilt-pres</font></a>
9. Report URL: <a href="https://github.com/Brazilian-Institute-of-Robotics/bir_droilt-docs/tree/main/doc"><font>Droilt-report</font></a>
10. Artigos produzidos: --

<br>

### Referências

1. <a id="SPONG">**Spong, Mark W and Hutchinson, Seth and Vidyasagar, Mathukumalli and others**</a>; Robot modeling and control; wiley New York, v3, 2006.
1. <a id="PIMENTA">**Pimenta, Karla Boaventura and others**</a>; "Controle de juntas roboticas usando controlador preditivo generalizado adaptativo direto", 2003.

1. <a id="ERTHAL">**Erthal, Jorge Luiz and others**</a>; "Estudo de metodos para a solução da cinematica inversa de robôs industriais para implementação computacional", 1992.

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
