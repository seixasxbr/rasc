---
layout: post
title: Trajetória dinâmica
subtitle: Um estudo sobre manipuladores by Marco Reis
cover-img: /assets/img/aum/matt-hardy-6ArTTluciuA-unsplash.jpg
thumbnail-img: /assets/img/aum/network(2).png
share-img: /assets/img/rosa-logo-redondo.png
tags: [aum]
---
# A conversa começa na pesquisa
<p style="text-align: justify;">
Diante de vários estudos realizados com o foco em robótica subaquática e manipulação; percebemos uma situação interessante na qual a grande maioria dos artigos faziam referências ao sistema completo, ou seja era compreendido pelo veículo e o manipulador. Nossa intenção é realizar uma pesquisa com os sistemas isolados, ou seja tratar especificamente somente o subsistema manipulador. 

Dessa forma, é preciso estabelecer a conexão dos assuntos e técnicas dos artigos selecionados que estão relacionados à manipuladores autônomos de base não fixa e que podem sofrer pertubações externas. 
</p>

## A trajetória dinâmica
<p style="text-align: justify;">
Buscando a compreensão dos conhecimentos sobre os sistemas de manipuladores subaquáticos com pertubação na base foi levantada uma lista de artigos e técnicas utilizados por alguns autores. 

Os métodos listados consistem no planejamento dinâmico de trajetória para manipuladores descrito pelos autores <a href="#WEI">WEI</a> e <a href="#VANNOY">VANNOY</a>. Esses métodos têm como fundamento o planejamento dinâmico de trajetória para desvio de obstáculos que podem serem utilizados nos manipuladores subaquáticos por conseguirem alterar o movimento rápidamente com a finalidade de atingir seu objetivo final. 

Outro método fundamental para o conceito de manipuladores subaquáticos com pertubação na base é o da odometria visual, utilizando algumas técnicas de **Odometria Visual**. Esses métodos permitem que o manipulador perceba a alteração da posição de sua base e, consequentemente, o objetivo final muda com relação a base, com isso ele deve realizar um novo planejamento para conseguir alcançar seu objetivo.
</p>

## Seguindo os artigos
<p style="text-align: justify;">
Nossa pesquisa foi realizada na base de artigos do <a href="https://www.elsevier.com/en-in/solutions/scopus"><font color="#fbb117">SCOPUS</font></a>, tomando como janela de tempo os últimos 6 anos. Diante dos dados, pode-se perceber um crescimento anual de 18% na produção científica baseada na *string* de busca.

Nesta revisão realizada, observa-se que a rede de colaboração tem uma sinergia entre alguns pesquisadores, e que os indexadores bibliográficos são considerados relevantes para a pesquisa.
</p>

![Rede de Colaboração](/assets/img/aum/network-3.png)

<p style="text-align: justify;">
Quando tomamos a rede de co-citação, percebe-se uma sinergia em volta de três autores:
  * [Santhakumar Mohan] propõe uma nova proposta de controle de posição do UVMS e um controle PID robusto para rastreamento de posição de um manipulador subaquático.
  * [Pandurang S. Londhe] fala sobre o controle do espaço de operação de um UVMS por esquema de controle Fuzzy e um controle de rastreamento de posição utilizando um método de modo deslizante.
  * [Mingxue Cai] fala sobre o controle de profundidade baseado em ROS para UVMS e Yu Wang, que discorre dos conceitos de propulsão bioinspirada subaquática da inspeção à manipulação.

Essa relevância é importante, para compreender o caminhar da pesquisa diante do assunto pesquisado.
</p>

![Rede de Co-citação](/assets/img/aum/network-2.png)

## So far
<p style="text-align: justify;">
Toda pesquisa precisa de uma direção inicial. Esta pequena introdução está nos direcionando para buscar a relavância dos métodos encontrados e desenvolver um planejamento de experimentos que seja conclusivo diante das questões que foram levantadas.
</p>

<br>

##### Referências
1. <a id="WEI">**Wei, Kun, and Bingyin Ren.**</a> "A method on dynamic path planning for robotic manipulator autonomous obstacle avoidance based on an improved RRT algorithm." Sensors 18.2 (2018): 571.  
2. <a id="VANNOY">**Vannoy, John, and Jing Xiao.**</a> "Real-time adaptive motion planning (RAMP) of mobile manipulators in dynamic environments with unforeseen changes." IEEE Transactions on Robotics 24.5 (2008): 1199-1212. 


<br>

---------------------
<br>

<!-- autor -->
<center><h3 class="post-title">Autor</h3><br/></center>
<div class="row">
  <div class="col-xl-auto offset-xl-0 col-lg-4 offset-lg-0 center">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="amarco" class="img-fluid rounded-circle" /></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td>Marco Reis</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Pesquisador Sênior do projeto<br>Mestre em Engenharia de Produção e Eng. Eletricista.</small></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>
