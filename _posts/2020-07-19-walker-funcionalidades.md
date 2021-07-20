---
layout: post
title: Walker - Funcionalidades
subtitle: O que o robô será capaz de fazer?
cover-img: /assets/img/path.jpg
thumbnail-img: assets/img/walker/walker_funcionalidades.png
share-img: assets/img/walker/walker_funcionalidades.png
tags: [walker, funcionalidades]
---

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
