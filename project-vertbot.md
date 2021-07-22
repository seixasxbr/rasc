---
layout: page
title: Vertbot
subtitle: Projeto open-source para o desenvolvimento de um robô diferencial
---

<p align = "center">
    <img src = "{{ 'assets/img/vertbot/vertbot_model.png' | relative_url }}">
</p>

<!-- ## Introdução -->
<!-- Neste tópico devemos ter no mínimo três parágrafos:
- parágrafo introdutório
- descrição sucinta do projeto apresentando o objetivo principal do projeto, data de início e prazo para a realização.
- justificativa -->

<p style="text-align: justify;">Vertbot é um robô diferencial open-source, que está sendo elaborado a partir do kit de desenvolvimento Jetson Nano, fabricado pela NVIDIA, além de múltiplos sensores e uma estrutura produzida por impressão 3D. Seu nome foi pensado pelo fato da fabricante do kit Jetson Nano utilizar tons de verde em sua marca e por decisão da equipe o termo Vert (verde em Francês) foi adotado como nome do modelo.

O projeto tem como objetivo encontrar uma esfera em um ambiente *indoor* de forma autônoma, utilizando sensores ópticos, sensores laser e sensores ultrassônicos, e deve ao mesmo tempo executar manobras de desvio de obstáculo. A execução dessa atividade teve início dia 10 de maio e está planejada para ser encerrada dia 20 de agosto.</p>

<p style="text-align: justify;"></p>

<p align = "center">
    <img src = "{{ 'assets/img/vertbot/vert_mission.png' | relative_url }}">
</p>

<p style="text-align: justify;">As atividades citadas tem como razão exercer na prática as funções de navegação autônoma para a execução de tarefas pré-determinadas atreladas a tags pré-estabelecidas, que serão reconhecidas e lidas por componentes de visão computacional. Também serão executadas tarefas relacionadas a gestão de projeto a fim de estimular e desenvolver aprendizado da parte de documentação e organização por parte do planejamento.</p>

## Detalhamento
<!-- Neste tópico devemos descrever o projeto mostrando os componentes principais e suas funcionalidades. -->

<p style="text-align: justify;">Para possibilitar uma navegação autônoma é necessário que o robô seja capaz de reconhecer o ambiente onde ele irá atuar. Portanto, um conjunto de sensores foram selecionados para captar informações dos arredores para que o robô tome suas decisões para suas ações. Os sensores escolhidos foram os listados a seguir.</p>

<style>
.vertical-center {
  margin: 0;
  position: absolute;
  top: 50%;
  -ms-transform: translateY(-50%);
  transform: translateY(-50%);
}
</style>

<div style="height: 240px; position: relative; border: 3px solid transparent;">
  <div class="vertical-center">
    <img src="{{ 'assets/img/vertbot/sonar.png' | relative_url }}" alt="Not found" width="200">
  </div> 
  <div style="padding-left: 210px;">
    <p style="text-align: justify;">O modelo de sensor escolhido para identificar obstáculos na trajetória do robô e calcular a distância desse obstáculo até o mesmo é o <b>Sonar HC-SR04</b>, que é um sensor ultrassônico com uma faixa de funcionamento entre 2 cm e 4 metros.Seu princípio de funcionamento é baseado na emissão e recepção de ondas sonoras.</p>
</div>
</div>

---

<div style="height: 200px; position: relative; border: 3px solid transparent;">
  <div class="vertical-center">
    <img src="{{ 'assets/img/vertbot/lidar.png' | relative_url }}" alt="Not found" width="200">
  </div> 
  <div style="padding-left: 210px;">
    <p style="text-align: justify;">O dispositivo escolhido para permitir a localização e mapeamento simultâneo (SLAM) do robô é o 360 <b>Laser Distance Sensor LDS-01</b>, que é um LiDAR capaz de medir a distância do robô para objetos em uma cobertura de 360 graus.</p>
</div>
</div>

---

<hr style="height:10px; visibility:hidden;" />

<div style="height: 170px; position: relative; border: 3px solid transparent;">
  <div class="vertical-center">
    <img src="{{ 'assets/img/vertbot/camera_v2.png' | relative_url }}" alt="Not found" width="200">
  </div> 
  <div style="padding-left: 210px;">
    <p style="text-align: justify;">Para realizar a identificação de marcos fiduciais, também conhecidos como TAG's, e também para detectar a esfera, que é missão do robô, será utilizada uma câmera de alta resolução, a <b>Raspberry Pi Camera Module V2</b>. </p>
</div>
</div>

<hr style="height:10px; visibility:hidden;" />

---

<div style="height: 180px; position: relative; border: 3px solid transparent;">
  <div class="vertical-center">
    <img src="{{ 'assets/img/vertbot/mynt-eye.png' | relative_url }}" alt="Not found" width="200">
  </div> 
  <div style="padding-left: 210px;">
    <p style="text-align: justify;">Para auxiliar no processo de localização por odometria e detecção de obstáculos é utilizada a câmera estéreo <b>Mynt Eye S1030</b>. Além do seu campo de visão, o componente dispõe de uma IMU, possibilitando a realização da odometria.</p>
</div>
</div>

---

Além dos sensores, foram selecionados também componentes para a realização da parte de processamento, apresentados a seguir.

<div style="height: 250px; position: relative; border: 3px solid transparent;">
  <div class="vertical-center">
    <img src="{{ 'assets/img/vertbot/jetson_nano.png' | relative_url }}" alt="Not found" width="200">
  </div> 
  <div style="padding-left: 210px;">
    <p style="text-align: justify;">Como unidade central de processamento, por onde passará todo fluxo de informação, será utilizado o computador de pequeno porte <b>Jetson Nano Developer Kit</b>. O sistema operacional  que será utilizado na Jetson Nano é o Ubuntu 20.04 e o software que auxilia no processamento e gerenciamento de informação é o Robot Operating System, versão Noetic.</p>
</div>
</div>

---

<div style="height: 220px; position: relative; border: 3px solid transparent;">
  <div class="vertical-center">
    <img src="{{ 'assets/img/vertbot/arduino_nano.png' | relative_url }}" alt="Not found" width="200">
  </div> 
  <div style="padding-left: 210px;">
    <p style="text-align: justify;">Os sensores HC-SR04, o Current Sensor 1122 e o Voltage Sensor 1135 são sensores com saída analógica de 0 V a 5V, sendo que a o sinal de entrada máximo suportado pela portas analógicas da Jetson Nano são de 3,3 V. Diante disso, foi escolhida como unidade de processamento auxiliar o  <b>Arduino Nano</b></p>
</div>
</div>

---

Alguns componentes foram escolhidos para compor a parte elétrica/eletrônica para atuar na parte tanto de alimentação como de gerênciamento de enérgia.

<div style="height: 190px; position: relative; border: 3px solid transparent;">
  <div class="vertical-center">
    <img src="{{ 'assets/img/vertbot/voltage_sensor.png' | relative_url }}" alt="Not found" width="200">
  </div> 
  <div style="padding-left: 210px;">
    <p style="text-align: justify;">Para realizar a gestão e monitoramento da carga das baterias que irão alimentar o sistema robótico é utilizado o <b>sensor de tensão 1135 da marca Phidgets</b> que é capaz de medir tensões DC na faixa de -30 V até 30 V.</p>
</div>
</div>

---

<div style="height: 190px; position: relative; border: 3px solid transparent;">
  <div class="vertical-center">
    <img src="{{ 'assets/img/vertbot/current_sensor.png' | relative_url }}" alt="Not found" width="200">
  </div> 
  <div style="padding-left: 210px;">
    <p style="text-align: justify;">O sensor de corrente, também utilizado para gerir e monitorar a carga da bateria, é o <b>Current Sensor 1122</b>, da marca <b>Phidgets</b>, capaz de medir correntes de 75 mA até 30 A em módulo.</p>
</div>
</div>

---

<div style="height: 150px; position: relative; border: 3px solid transparent;">
  <div class="vertical-center">
    <img src="{{ 'assets/img/vertbot/battery.png' | relative_url }}" alt="Not found" width="200">
  </div> 
  <div style="padding-left: 210px;">
    <p style="text-align: justify;">Para comportar as duas <b>baterias recarregáveis de íon de lítio do modelo 18650 de 4,2 V</b>, que irão alimentar o sistema, é utilizado o <b>Battery Shield 18650 V3</b>. </p>
</div>
</div>

---

Por fim, para a movimentação do robô foram selecionados um par de motores seguido de um shield para gerencia-los.

<hr style="height:10px; visibility:hidden;" />

<div style="height: 100px; position: relative; border: 3px solid transparent;">
  <div class="vertical-center">
    <img src="{{ 'assets/img/vertbot/motor.png' | relative_url }}" alt="Not found" width="200">
  </div> 
  <div style="padding-left: 210px;">
    <p style="text-align: justify;">Os motores que darão movimento as rodas do robô são os <b>DC Gearbox Motor TT</b>, Motor de 200 RPM. </p>
</div>
</div>

<hr style="height:10px; visibility:hidden;" />

---

<hr style="height:10px; visibility:hidden;" />

<div style="height: 100px; position: relative; border: 3px solid transparent;">
  <div class="vertical-center">
    <img src="{{ 'assets/img/vertbot/motor_shield.png' | relative_url }}" alt="Not found" width="200">
  </div> 
  <div style="padding-left: 210px;">
    <p style="text-align: justify;">Para fazer o controle do giro dos motores é utilizado o <b>Servo Driver 16 canais PCA9685</b>. </p>
</div>
</div>

<hr style="height:10px; visibility:hidden;" />

<br>

## Simulação
<!-- Neste tópico inserir as simulações do projeto. -->

<hr style="height:10px; visibility:hidden;" />

<div style="height: 250px; position: relative; border: 3px solid transparent;">
  <div class="vertical-center">
    <img src="{{ 'assets/img/vertbot/noetic.png' | relative_url }}" alt="Not found" width="200">
  </div> 
  <div style="padding-left: 210px;">
    <p style="text-align: justify;">Para a realização do processo de simulação, será utilizado o sistema ROS (Robot Operating System) na versão Noetic para Ubuntu 20.04. O ROS é uma plataforma open-source que conta com uma vasta biblioteca de software framework para desenvolvimento de projetos na área da robótica, além de ser capaz de funcionar em computadores de diversas configurações.</p>
</div>
</div>

<br>

<img src="{{ 'assets/img/vertbot/gazebo-logo.png' | relative_url }}" alt="Not found" width="200">{: style="float: right; padding-left: 50px;"}

<br>

Os trabalhos já iniciados na parte de simulação já conta com um workspace e um modelo desenvolvido para rodar no ambiente do <b>Gazebo</b>, que é o programa de simulação que trabalha em conjunto com o ROS.

<br><br>

<p align = "center">
    <img src = "{{ 'assets/img/vertbot/vertbot_gazebo.png' | relative_url }}">
</p>

<!-- ## Live Action
Neste tópico o principal é mostrar a realização do projeto. -->

<br>
<!-- ## Equipe -->
<center><h3 class="post-title">Equipe de desenvolvimento</h3><br/></center>
<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><center><img src="{{ 'assets/img/people/breno-1.png' | relative_url }}" width="100" alt="breno" class="img-fluid rounded-circle" /></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/mateusseixas-1.png' | relative_url }}" width="100" alt="mateusseixas" class="img-fluid rounded-circle"/></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="marco" class="img-fluid rounded-circle"/></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="33.33%"><center>Breno Portela</center></td>
          <td></td>
          <td width="33.33%"><center>Mateus Seixas</center></td>
          <td></td>
          <td width="33.33%"><center>Marco Reis</center></td>
        </tr>
        <tr style="text-align:center" >
          <td width="33.33%" style="vertical-align: top"><small>Engenheiro Mecânico - Senai Cimatec.<br> Líder da équipe Vertbot.</small></td>
          <td></td>
          <td width="33.33%" style="vertical-align: top"><small>Engenheiro Eletricista - UFBA.<br> Responsável pela parte elétrica e comunicação dos sensores.</small></td>
          <td></td>
          <td width="33.33%" style="vertical-align: top"><small>Mestre em Engenharia de Produção e Eng. Eletricista. <br> Orientador do Projeto.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>

### Resumo do Projeto
1. Categoria: <font color="#fbb117">Robótica móvel</font>
2. Prazo: <font color="#fbb117">4 meses</font>
3. Data de início: <font color="#fbb117">10/05/2021</font>
4. Data de término: <font color="#fbb117">20/08/2021</font>
5. Repositório URL:
6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>
7. Recursos materiais: --
8. Apresentação URL:
9. Report URL:
10. Artigos relacionados: 