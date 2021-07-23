---
layout: post
title: Primeiros passos
subtitle: Testes de sensores e iniciando o Gazebo by Breno Portela
cover-img: /assets/img/vertbot/jukan-tateisi-bJhT_8nbUA0-unsplash.jpg
thumbnail-img: /assets/img/vertbot/vertbot_model.png
share-img: /assets/img/rosa-logo-redondo.png
tags: [vertbot]
---

### Testando os sensores do Vertbot

Nesta etapa de desenvolvimento foi feita a pesquisa dos pacotes e das bibliotecas necessárias para o funcionamento dos diversos sensores presentes no projeto, seguido do teste e integração dos sensores com o ROS operando na Jetson Nano. Nos testes feitos com os sensores de corrente e de tensão, mostrados respectivamente nas Imagens 1 e 2 , foi verificada uma inconsistência do valor apresentado como resultado para o valor real que estava sendo medido, devido a uma não linearidade nas respostas dos sensores. 

Devido a isso, foi levantada a curva das suas respostas analógicas de saída em função das suas entradas, mostradas nas Figuras 1 e 2 e feita uma linearização na faixa de operação que a alimentação do robô estará operando. No teste de tensão foi medida a tensão sobre uma fonte de tensão chaveada e no teste de tensão de corrente foi medida a corrente passando por um resistor de 1R2. Os sensores de corrente, de tensão e o sensor ultrassônico são sensores com resposta analógica de até 5 V, tensão não suportada pelas portas analógicas da Jetson Nano. Portanto tais sensores serão ligados a um microprocessador Arduino Nano, sendo necessário o pacote rosserial para a integração das respostas do Arduino com o ROS operando na Jetson Nano. No teste do sensor ultrassônico, mostrado na Imagem 3,  foram medidas diversas distâncias com o sensor e comparadas com os valores obtidos com uma fita métrica para avaliar os resultados.



<div style="display:inline-block; vertical-align:top;">
    <img align="left" src = "{{ 'assets/img/vertbot/test_current_sensor.jpg' | relative_url }}" height="300" class="float-left">
    Devido a isso, foi levantada a curva das suas respostas analógicas de saída em função das suas entradas, mostradas nas Figuras 1 e 2 e feita uma linearização na faixa de operação que a alimentação do robô estará operando. No teste de tensão foi medida a tensão sobre uma fonte de tensão chaveada e no teste de tensão de corrente foi medida a corrente passando por um resistor de 1R2. Os sensores de corrente, de tensão e o sensor ultrassônico são sensores com resposta analógica de até 5 V, tensão não suportada pelas portas analógicas da Jetson Nano. Portanto tais sensores serão ligados a um microprocessador Arduino Nano, sendo necessário o pacote rosserial para a integração das respostas do Arduino com o ROS operando na Jetson Nano. No teste do sensor ultrassônico, mostrado na Imagem 3,  foram medidas diversas distâncias com o sensor e comparadas com os valores obtidos com uma fita métrica para avaliar os resultados.
</div>
<div style="display:inline-block;">
    <div>
    Devido a isso, foi levantada a curva das suas respostas analógicas de saída em função das suas entradas, mostradas nas Figuras 1 e 2 e feita uma linearização na faixa de operação que a alimentação do robô estará operando. No teste de tensão foi medida a tensão sobre uma fonte de tensão chaveada e no teste de tensão de corrente foi medida a corrente passando por um resistor de 1R2. Os sensores de corrente, de tensão e o sensor ultrassônico são sensores com resposta analógica de até 5 V, tensão não suportada pelas portas analógicas da Jetson Nano.
    </div>
</div>


![](/assets/img/vertbot/test_current_sensor.jpg){: width="40%"}  ![](/assets/img/vertbot/test_voltage_sensor.jpg){: width="31%"} 


![](/assets/img/vertbot/graph_current_sensor.png){: width="40%"}  ![](/assets/img/vertbot/graph_voltage_sensor.png){: width="40%"} 



<p align = "center">
Imagem 1 - Teste do sensor de corrente
</p>

<p align = "center">
    <img src = "{{ 'assets/img/vertbot/test_voltage_sensor.jpg' | relative_url }}" height="400">
</p>
<p align = "center">
Imagem 2 - Teste do sensor de tensão
</p>

<p align = "center">
    <img src = "{{ 'assets/img/vertbot/graph_current_sensor.png' | relative_url }}">
</p>
<p align = "center">
Figura 1 - Curva de resposta analógica (corrente)
</p>

<p align = "center">
    <img src = "{{ 'assets/img/vertbot/graph_voltage_sensor.png' | relative_url }}">
</p>
<p align = "center">
Figura 2 - Curva de resposta analógica (tensão)
</p>

<p align = "center">
    <img src = "{{ 'assets/img/vertbot/test_sonar.jpg' | relative_url }}" height="750">
</p>
<p align = "center">
Imagem 3 - Teste do sonar
</p>

O pacote disponível para a câmera estéreo Mynt Eye foi desenvolvido para o Ubuntu 18.04, porém a versão usada na Jetson Nano é a 20.04, sendo necessário o uso do container Docker com a versão 18.04 do Ubuntu para utilizar o pacote. Na Imagem 4, podemos ver a imagem de ambas câmeras da Mynt Eye sendo exibidas no Rviz do ROS. Os demais sensores, a Câmera Raspberry Pi V2 e o lidar LDS-01, apresentaram respostas coerentes com as bibliotecas encontradas no estudo da arte desenvolvido. Podemos ver o teste da Câmera V2 na Imagem 5 e do teste do lidar na Imagem 6.

<p align = "center">
    <img src = "{{ 'assets/img/vertbot/test_mynt-eye.jpg' | relative_url }}">
</p>
<p align = "center">
Imagem 4 - Teste da camera Mynt Eye
</p>

<p align = "center">
    <img src = "{{ 'assets/img/vertbot/test_camera_v2.jpg' | relative_url }}" height="750">
</p>
<p align = "center">
Imagem 5 - Teste da camera Rasp V2
</p>

<p align = "center">
    <img src = "{{ 'assets/img/vertbot/test_lidar.jpg' | relative_url }}" height="750">
</p>
<p align = "center">
Imagem 6 - Teste do LiDAR
</p>

### Desenvolvimento do URDF

Após a atualização da estrutura do modelo do robô, foi dado o início da montagem do _workspace_ e da construção do arquivo URDF (Unified Robot Description Format) para inicializar a simulação. Alguns ajustes serão feitos futuramente no chassis para adicionar os encaixes do sensor de corrente, sensor de tensão e shield do motor, além do desenvolvimento de uma peça de encaixe da _caster ball_ e possíveis redimensionamentos para o encaixe de peças que estão em processo de compra. Com o workspace da simulação já iniciado, é possível começar os testes de sensores via simulação para a criação da rede de sensores e os testes de interação entre eles, além do desenvolvimento dos algoritmos e das funcionalidades abordadas no projeto. Abaixo podemos ver o modelo do robô em uma simulação do Gazebo.

<p align = "center">
    <img src = "{{ 'assets/img/vertbot/vertbot_gazebo.png' | relative_url }}">
</p>
<p align = "center">
Figura 3 - Modelo Vertbot no Gazebo
</p>


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
          <th><img src="{{ 'assets/img/people/breno-1.png' | relative_url }}" width="100" alt="breno" class="img-fluid rounded-circle" /></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td>Breno Portela</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Engenheiro Mecânico - Senai Cimatec. Líder da équipe Vertbot.</small></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>