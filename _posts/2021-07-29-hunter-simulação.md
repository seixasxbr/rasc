---
layout: post
title: Simulação
subtitle: Simulação do hunter by Anderson Lima
cover-img: /assets/img/hunter/hunter-simulação.png
thumbnail-img: https://p1.pxfuel.com/preview/622/928/1003/wall-e-robot-toy-cute.jpg 
share-img: /assets/img/bir-team.png
tags: [hunter]
---

## Modelagem de caça

A simulação em robótica é importante para a criação de um modelo que procura se assemelhar a realidade, sendo possível a implementação de testes sem a necessidade do protótipo estar pronto fisicamente.

O processo de modelagem do Hunter é feito em formato _**URDF (Universal Robotic Description Format)**_ que é um estrutura que se baseia em arquivo XML e define a montagem do robô em função de elementos básicos que se conectam hierarquicamente.

- **LINK**: Corpo rígido com propriedades físicas e visuais
- **JOINTS**: Ponto de conexão entre corpos rígidos

![projeto-hunter](../assets/img/hunter/hunter-link-joint.png)<br>

As características visuais e geométricas dos links do Hunter foram retiradas de modelagem feita na ferramenta **CAD Onshape**, bem como os arquivos exportados que compõem colisão física.