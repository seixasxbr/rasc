---
layout: post
title: Processo de montagem do Bbot
subtitle: Construindo o projeto bbot by Matheus França
cover-img: assets/img/bbot/bbot_wide.png
thumbnail-img: assets/img/bbot/bbot.png
share-img: assets/img/rosa-logo-redondo.png
comments: true
tags: [bbot]
---
## Anteriormente
É importante que você tenha visto o post anterior [Simulação do Bbot](https://mhar-vell.github.io/rasc/2021-08-11-bbot-simulacao/), para um completo entendimento do desenvolvimento do projeto.

## Montagem

Na etapa cinco do processo de construção do <a href="https://mhar-vell.github.io/rasc/project-bbot/"><font color="#fbb117">Bbot</font></a>, podemos analisar o desenvolvimento de sua construção.

Podemos ver o desenvolvimento e o processamento da impressora 3d no post anterior, [desenho mecânico](https://mhar-vell.github.io/rasc/2021-08-04-bbot-desenho-mecanico/). 

### Roda

Para uma maior aderência do robô ao solo, decidimos construir rodas de borracha de silicone. Com o molde e a jante já impressos em 3d, acoplamos os dois e o envolvemos no silicone. 

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/molde_roda.jpg' | relative_url }}" alt="Molde roda" width="200" style="display:inline;margin:0px 50px 0px 0px;"/>
    <img id="myImg" src="{{ 'assets/img/bbot/roda.jpeg' | relative_url }}" alt="Roda" width="200"/>
</p>

Após 2 dias para a cura da borracha, podemos abrir o molde e fazer a limpeza da peça, obtendo a roda completa.

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/SNo7njk5Hwg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

### Pernas

Simultaneamente à construção da roda, fizemos a montagem das pernas do robô. Foi feita a impressão 3D das peças e a limpeza dos materiais.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/perna_1.jpeg' | relative_url }}" alt="Molde roda" width="400" style="display:inline;margin:0px 50px 0px 0px;"/>
    <img id="myImg" src="{{ 'assets/img/bbot/perna_2.jpeg' | relative_url }}" alt="Roda" width="227"/>
</p>

As pernas comportam 2 GDLs (Graus De Liberdade) cada, possibilitando ao Bbot uma mobilidade maior para ultrapassar obstáculos.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/perna_3.jpeg' | relative_url }}" alt="Molde roda" width="230" style="display:inline;margin:0px 50px 0px 0px;"/>
    <img id="myImg" src="{{ 'assets/img/bbot/perna_4.jpeg' | relative_url }}" alt="Roda" width="230"/>
</p>

O motor de locomoção contém uma peça de acoplamento para a roda, isso faz com que a manutenção das peças seja mais fácil. Possibilita também a mudança da roda ou do atuador da roda, sem grande impacto no projeto.

### Base

A base do robô vai comportar toda a parte de potência e os sensores do Bbot. 

Parte essencial do self balancing, o IMU, foi posicionado no centro da base, produzindo um feedback importante para o equilíbrio. Já os amortecedores foram acoplados à base com a intenção de proteger o LiDAR, que fica em uma área desprotegida (no topo do robô).

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/base_1.jpeg' | relative_url }}" alt="Molde roda" width="230" style="display:inline;margin:0px 50px 0px 0px;"/>
    <img id="myImg" src="{{ 'assets/img/bbot/base_2.jpg' | relative_url }}" alt="Roda" width="380"/>
</p>

Para uma completa lista de equipamentos das peças internas do Bbot, siga para o post do [desenho mecânico](https://mhar-vell.github.io/rasc/2021-08-04-bbot-desenho-mecanico/). 


## Resultados

Na **quinta etapa** do projeto, nós apresentamos a construção do **Bbot**. <img src="{{ 'assets/img/bbot/bbot.png' | relative_url }}" alt="Bbot" width="17"/> &#128295; <img src="{{ 'assets/img/bbot/bbot_stand.png' | relative_url }}" alt="Bbot" width="15"/>
<br>

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/f9vfHLqY0YA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

Para as próximas etapas, serão apresentados os testes com o robô real.

<!-- SPOILER -->
<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/6xNG0_EvZec" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

----------------

<br>

<!-- **************************************** Autor **************************************** -->
<center><h3 class="post-title">Autor</h3><br/></center>

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
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center; margin-top: 0">
          <td width="33.33%">Matheus França</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top;text-align: justify;"><small>Estagiário no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia de Controle e Automação na Área 1.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>
