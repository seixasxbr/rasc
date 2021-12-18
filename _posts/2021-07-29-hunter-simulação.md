---
layout: post
title: Simulação de caça
subtitle: Simulação do hunter
cover-img: /assets/img/hunter/post-simulacao/hunter-simulação.png
thumbnail-img: https://p1.pxfuel.com/preview/622/928/1003/wall-e-robot-toy-cute.jpg 
share-img: /assets/img/bir-team.png
author: Anderson Lima
comments: true
tags: [hunter]
---

## Modelagem de caça

A simulação em robótica é importante para a criação de um modelo que procura se assemelhar a realidade, sendo possível a implementação de testes sem a necessidade do protótipo estar pronto fisicamente.

O processo de modelagem do Hunter é feito em formato _**URDF (Universal Robotic Description Format)**_ que é um estrutura que se baseia em arquivo XML e define a montagem do robô em função de elementos básicos que se conectam hierarquicamente.

- **LINK**: Corpo rígido com propriedades físicas e visuais
- **JOINTS**: Ponto de conexão entre corpos rígidos

Por ser um robo de acionamento diferencial, o Hunter se movimenta a partir do controle de velocidade das rodas esquerda e direita, sendo representado pelo esquema a seguir:

<center>
  <img src="{{ 'assets/img/hunter/post-simulacao/hunter-link-joint.png' | relative_url }}" text-align=center alt="linkjoint" />
</center>

As características visuais e geométricas dos links do Hunter foram retiradas de modelagem feita na ferramenta **CAD Onshape**, bem como os arquivos exportados que compõem suas características de colisão física. A partir da criacão do aquivo **urdf** é possível visualizá-lo no ambiente de simulação **gazebo**:

<center>
  <img src="{{ 'assets/img/hunter/post-simulacao/hunter_gazebo.png' | relative_url }}" text-align=center alt="gazebo" />
</center>

A adicao de plugins ao modelo **urdf** traz funcionalidades ao modelo, o plugin diferencial, por exemplo, permite a comunicação com ambiente de simulação gazebo, sendo possivel enviar informacoes de velocidade para os motores.

<center>
  <img src="{{ 'assets/img/hunter/post-simulacao/hunter-plugin.png' | relative_url }}" text-align=center alt="plugin" />
</center>

O atuacão do plugin diferencial permite o controle de movimentacão na simulação. Nas proximas etapas do projeto será implementado a navegacão do Hunter!

<center>
  <img src="{{ 'assets/img/hunter/post-simulacao/hunter-simulation-cmdvel.gif' | relative_url }}" text-align=center alt="plugin" />
</center>