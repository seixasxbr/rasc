---
layout: post
title: Testes da eletrônica
subtitle: Validando os componentes do Bbot by Matheus França
cover-img: assets/img/bbot/bbot_wide.png
thumbnail-img: assets/img/bbot/bbot.png
share-img: assets/img/rosa-logo-redondo.png
comments: true
tags: [bbot]
---

Com a escolha das peças para compor o robô, foi preciso fazer testes físicos para entender e validar as peças em questão. 

Este post trata dos testes eletrônicos, demonstrando a configuração, data e os resultados encontrados.

## Testes da eletrônica

Os testes da eletrônica estão divididos com as respectivas peças. iniciamos os testes no dia 10 de junho de 2021 com o motor de passo.

### Teste 1 - Stepper

**Data:** 10/06/2021

Os testes foram realizados com a seguinte configuração:

- Motor de passo NEMA 17
- Driver Sparkfun (Big Easy Driver)
- OpenCM9.04

O motor de passo NEMA 17 foi testado com o microcontrolador OpenCM904 (STM32) fazendo interface com o driver Big Easy Driver da Sparkfun. O driver do motor foi alimentado com 11.1 V  via fonte de bancada e a OpenCM904 pelo próprio USB do computador. O algoritmo usado foi um exemplo de teste do próprio site da Sparkfun.

Todos os componentes apresentaram funcionamento dentro do esperado. Apenas o motor de passo apresentou resultados preocupantes, não tendo torque suficiente para o peso do robô. Foi decidido então modificar o atuador por um __*Dynamixel XM430-W210-R*__ (testes apresentados mais pra frente no post).

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/LyrG0p-TM_Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

### Teste 2 - Gyro GS-12

**Data**: 14/06/2021

Os testes foram realizados com a seguinte configuração:

- Gyro sensor GS-12 da ROBOTIS
- OpenCM9.04

O teste foi realizado com um algoritmo de leitura dos valores de saída do sensor. A placa __*OpenCM*__ foi alimentada pelo USB e tivemos de usar um cabo diferente do padrão para o sensor, pois sua alimentação era de 5V porém a OpenCM apenas entregava 3V3. 

O sensor se mostrou preciso para as medições de velocidade angular, com saída entre 0 ~ 1000 para w = [-300º/s : 300º/s], sendo a saída estável aproximadamente 450. Contudo, foi visto que também será necessário os dados da posição angular. Portanto, iremos mudar para um IMU com chip __*MPU6050*__ (mostramos os testes mais pra frente no post).

### Teste 3 - Sensor de tensão Phidgets 1135

**Data**: 14/06/2021

Os testes foram realizados com a seguinte configuração:

- Sensor de tensão Precision Voltage 1135
- Fonte de bancada
- LiPO 3S
- OpenCM904

Os testes foram realizados de duas formas, com uma fonte de bancada e com uma bateria LiPO de 11.1 V. A saída foi lida pela entrada analógica da OpenCM904. 

O sensor apresentou leituras estáveis para tensões menores que 10V. Acima desse valor, a leitura ficou bastante ruidosa. Acreditamos ser pelo fato de a referência analógica da openCM904 ser 3V3, mas a saída do sensor ser 5V. As tensões de 11.1V com a fonte de bancada resultaram em uma saída de aproximadamente 3.27 V, porém esse valor já foi o suficiente para acrescentar ruído na leitura da _OpenCM904_. Para continuar utilizando este sensor, uma alternativa é indicar tensão abaixo da mínima (ex.: 10V), caso o leitor apresente um número elevado de leitura consecutivas dentro de um _range_ pequeno, o que comprova estabilidade e, portanto, que a tensão está abaixo dos 10V.

### Teste 4 - Dynamixel MX-106

**Data:** 15/06/2021

Os testes foram realizados com a seguinte configuração:

- Dynamixel MX-106 
- OpenCM904
- OpenCM485 Expansion board

O Teste foi realizado alimentando a _OpenCM485_ via fonte de bancada a 11.1V e com a _OpenCM904_ conectada a ela. Após a configuração de todos os IDs (141,151, 112, 122) e Baudrate (1Mbps), foram testados alguns códigos de exemplo do Dynamixel para controle de posição e velocidade.

O Dynamixel apresentou resultados satisfatórios para os controles de velocidade e posição. A posição varia de 0 - 306º (0 ~ 4095) e a velocidade de 0 a 41 rpm (-1023 ~ 1023), para a tensão de 11.1 V. 

<center>
<iframe width="360" height="315" src="https://www.youtube.com/embed/s95iISFyurc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="360" height="315" src="https://www.youtube.com/embed/-lRE_ntTgp0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

### Teste 5 - MPU6050

**Data:** 15/06/2021

Os testes foram realizados com a seguinte configuração:

- IMU MPU6050
- RaspberryPi

O teste foi realizado com o IMU MPU6050 conectado à RaspberryPi com Ubuntu 20.04 + ROS Noetic. O IMU comunicava com a raspberry via protocolo i2C e um pacote do ROS [mpu6050_driver](https://github.com/Brazilian-Institute-of-Robotics/mpu6050_driver) fazia o processamento dos dados e publicava a orientação, velocidade angular e aceleração angular em tópicos dos ROS.

Foi possível ler os dados via terminal, eles estavam consistentes com as movimentações aplicadas no sensor. 

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/d2jDFID_kvw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

### Teste 6 - Dynamixel XM430-W210-R

**Data:** 16/07/2021

Os testes foram realizados com a seguinte configuração:

- Dynamixel XM430-W210-R
- OpenCM904
- OpenCM485 Expansion board

O Teste foi realizado alimentando a OpenCM485 via fonte de bancada entre 11.1V ~ 14.8V e com a OpenCM904 conectada a ela. Foram testados apenas códigos padrão do Dynamixel para controle de velocidade, já que esse atuador vai substituir o Nema 17 na movimentação da roda.

O Dynamixel apresentou resultados satisfatórios para o controle de velocidade. Para a tensão de 14.8 V ele chega a uma velocidade de aproximadamente 95 rpm. 

<center>
<iframe width="360" height="315" src="https://www.youtube.com/embed/ku5Ztdp1ibE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="360" height="315" src="https://www.youtube.com/embed/E79M9DK45sI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

## Resultados

Nesta etapa do projeto, nós apresentamos os testes de eletrônica do **Bbot**. <img src="{{ 'assets/img/bbot/bbot.png' | relative_url }}" alt="Bbot" width="17"/> ⚡⚡ <img src="{{ 'assets/img/bbot/bbot_stand.png' | relative_url }}" alt="Bbot" width="15"/>
<br>

Os resultados para os testes eletrônicos foram apresentados nas suas respectivas descrições. Para as próximas etapas, serão apresentados os testes com o robô real, demonstrando o controle PID e seus ajustes.

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
          <td style="vertical-align: top;text-align: justify;"><small>Pesquisador Júnior (estagiário) no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia de Controle e Automação.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>
