---
layout: page
title: Hunter
subtitle: Jetson Nano Differencial Wheeled Robot
---
{% assign date_format = site.date_format | default: "%B %-d, %Y" %}
{%- capture site_tags -%}
    {%- for tag in site.tags -%}
      {% if tag contains 'hunter' %}
        {{- tag | first -}}{%- unless forloop.last -%},{%- endunless -%}
      {% endif %} 
    {%- endfor -%}
{%- endcapture -%}
{%- assign tags_list = site_tags | split:',' | sort -%}

<center><img src="{{ '/assets/img/hunter/hunter.png' | relative_url }}" text-align=center width="500" alt="hunter" /><br></center>


<div class="before-content">
  <center>
    {%- for tag in tags_list -%}
      <br>
      <a href="#{{- tag -}}" class="btn btn-primary tag-btn"><i class="fas fa-tag" aria-hidden="true"></i>&nbsp;{{- tag -}}-posts&nbsp;({{site.tags[tag].size}})</a>
    {%- endfor -%}
  </center>    
  <!--hr class="mark"-->
</div>

Robôs autônomos são sistemas que podem operar em ambientes imprevisíveis e parcialmente desconhecidos, tendo a capacidade de realizar uma navegação ininterrupta e desviar de obstáculos. Neste contexto, se destaca o robô de tração diferencial, que possui uma simples construção, boa manobrabilidade [[1]](https://ieeexplore.ieee.org/document/9007654).

O Hunter é um projeto de um robô de tração diferencial autônomo, que utiliza a plataforma [NVIDIA Jetson Nano Developer Kit](https://developer.nvidia.com/embedded/jetson-nano-developer-kit) como base de desenvolvimento. O objetivo deste projeto é desenvolver um robô que seja capaz de navegar em um ambiente desconhecido, realizando mapeamento, localização e ***obstacle avoidance***, e encontrar objetos dispostos no ambiente. Esta tarefa de busca estará associada a identificação de um marco fiducial, que apontará uma localização de um novo objeto a ser atingido. Assim, a tarefa é cumprida quando o robô encontra o marco, segue até a localização apontada e encontra o objeto buscado.

A principal vantagem de utilizar o Hunter é a disponibilidade de um sistema embarcado capaz de rodar múltiplas redes neurais em paralelo, que possibilita a aplicação de classificação de imagem, detecção de objetos, etc. Esta capacidade permite que técnicas modernas de odometria, localização e mapeamento possam ser embarcada neste robô diferencial, assim elevando o nível cognição do sistema.

## Detalhamento
![componentes](/assets/img/hunter/components.png)

O hunter utilizará sensores externos que serão utilizados
na sua navegação e na percepção do ambiente, sendo os principais
sensores:
- Stereo camera: Controle de odometria
- Raspicam : Será utilizada para detectar o marco fiducial (tag) no ambiente
- Sensor ultrassônico HC-SR04: Permitirá a indentificação de obstaculos possibilitando a navegação de forma autônoma
- Sensor LiDAR: Auxiliará no mapeamento do ambiente e deslocamento simultâneo

## Simulação
![componentes](/assets/img/hunter/hunter_gazebo.png)

Simulação do hunter baseado em modelo URDF (Unified robot description format) no Gazebo.

<br>

<hr>
<!-- equipe -->
<center><h3 class="post-title">Equipe de desenvolvimento</h3><br/></center>
<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><center><img href="https://www.linkedin.com/in/caio-maia-5b5a383b/" src="{{ 'assets/img/people/caiomaia-1.png' | relative_url }}" width="100" alt="caiomaia-foto" class="img-fluid rounded-circle" /></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/andersonlima-1.png' | relative_url }}" width="100" alt="andersonlima-foto" class="img-fluid rounded-circle"/></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="marco" class="img-fluid rounded-circle"/></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="33.33%" ><a>Caio Maia</a></td>
          <td></td>
          <td width="33.33%">Anderson Lima</td>
          <td></td>
          <td width="33.33%">Marco Reis</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Bolsista no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia Elétrica na UESC.</small></td>
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
1. Categoria: Robótica móvel
2. Prazo: 14 semanas
3. Data de início: 17/05/2021
4. Data de término: 21/08/2021
5. Repositório URL: [Hunter](https://github.com/Brazilian-Institute-of-Robotics/bir_jetbot-3)
6. Sponsor: [SENAI CIMATEC](http://www.senaicimatec.com.br/en/)
7. Recursos materiais: US$
8. Apresentação URL: [Hunter-docs](https://github.com/Brazilian-Institute-of-Robotics/bir_jetbot-3-docs)
9. Report URL:[Hunter-docs](https://github.com/Brazilian-Institute-of-Robotics/bir_jetbot-3-docs)
10. Artigos relacionados: -

<br>

##### Referências

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