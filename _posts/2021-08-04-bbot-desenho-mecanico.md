---
layout: post
title: Desenho mecânico do Bbot
subtitle: A criação do projeto mecânico do bbot
cover-img: assets/img/bbot/bbot_wide.png
thumbnail-img: assets/img/bbot/bbot.png
share-img: assets/img/rosa-logo-redondo.png
author: Matheus França
comments: true
tags: [bbot]
---
# Anteriormente
É importante que você tenha visto o post anterior [Funcionalidades do Bbot](https://mhar-vell.github.io/rasc/2021-07-29-funcionalidades-do-bbot/), para um completo entendimento do desenvolvimento do projeto.

## Introdução

Na etapa três do processo de construção do <a href="https://mhar-vell.github.io/rasc/project-bbot/"><font color="#fbb117">Bbot</font></a>, podemos analisar o desenvolvimento do desenho mecânico e as ferramentas escolhidas.

<hr>

<!-- **************************************** -->
## Desenho mecânico

Com o estudo realizado nas etapas anteriores, podemos partir para o dimensionamento da estrutura iniciando a parte do desenho técnico do projeto. O desenho foi todo feito no software **_Fusion 360_**, o modelo serviu para a produção na impressora 3d, testes de liberdade de movimentação e a simulação (Gazebo - ROS), corrigindo eventuais erros.

### Pernas

Iniciamos o desenho do robô pela parte das pernas. Foi escolhido fazer um robô com articulações nas pernas para ajudar a equilibrar o robô, variando o comprimento da perna para suavizar a passagem por obstáculos. 

Com o intuito de melhorar a aderência do robô com o solo, foi projetado um pneu de borracha de silicone.

As pernas são subdivididas em 3 graus de liberdade cada, da seguinte forma:
- **Rodas:** locomoção do robô.
- **Parte inferior das pernas:** angulação medial do robô.
- **Parte superior das pernas:** promovem a angulação da base do robô.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/pernas_explode.png' | relative_url }}" alt="Diagrama de funcionalidades" width="750"/>
</p>

### Base

Já a base do **Bbot**, é projetada para acomodar os sensores e toda sua eletrônica. A vista explodida da base pode ser vista em seguida, e demonstra todas as peças.

Foram projetados amortecedores (frontal e traseiro) para casos de falha e impacto do robô, protegendo as partes sensíveis dos sensores.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/base_explode.png' | relative_url }}" alt="Diagrama de funcionalidades" width="750"/>
</p>

### Processamento para impressão 3d

Depois do desenho ser feito ele é processado pelo programa da impressora 3D, que neste caso será utilizado o **_Ultimaker Cura_**, para gerar o código de máquina (código g) e assim produzir a peça propriamente dita.

Todas as peças foram processadas no software da impressora 3d (**_Ultimaker 2_**) para produção. A base frontal pode ser vista na figura seguinte, demonstrando o software da impressora 3D.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/3d-printing.png' | relative_url }}" alt="Diagrama de funcionalidades" width="750"/>
</p>

### Conclusão

Na **terceira etapa** do projeto, nós apresentamos o detalhamento do desenho mecânico do robô. Apresentamos também a etapa de processamento das peças para impressão 3D. <img src="{{ 'assets/img/bbot/bbot.png' | relative_url }}" alt="Bbot" width="17"/> &#128295; <img src="{{ 'assets/img/bbot/bbot_stand.png' | relative_url }}" alt="Bbot" width="15"/>
<br>

Para as próximas etapas, serão apresentados a impressão e montagem do robô, assim como sua simulação e controle.

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
