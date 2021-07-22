---
layout: post
title: Definição do modelo Bbot 
subtitle: Um robô que se equilibra com pernas articuladas
cover-img: assets/img/bbot/bbot_wide.png
thumbnail-img: assets/img/bbot/bbot.png
share-img: assets/img/rosa-logo-redondo (180).png
tags: [bbot]
---

<!-- **************************************** -->
<!-- ### Introdução -->
<p>
Motivados pelo desejo de contribuir para a inovação no campo dos robôs auto-balanceados e suas tecnologias, e com o avanço da investigação da robótica internacional, decidimos avançar com a criação de uma nova plataforma com características especiais face a soluções previamente definidas.
</p>{: style="text-align: justify;"}

<p>
Para iniciarmos a <strong>etapa 1</strong> da construção do robô, definimos como prioridade utilizar componentes já disponíveis no laboratório da instituição (<a target="_blank" href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>). Além disso, o <a href="https://mhar-vell.github.io/rasc/project-bbot/"><font color="#fbb117">projeto Bbot</font></a> deverá atender requisitos baseados nas necessidades e expectativas de pesquisa. A adição de servos para manipular membros sobre rodas traz um desafio com uma série de benefícios. Ou seja, ser capaz de ajustar a altura de cada perna para permanecer estável mesmo ao tombar de um lado para o outro e com maior capacidade off-road, bem como até mesmo pular. 
</p>{: style="text-align: justify;"}

<hr>

<!-- **************************************** -->
### Requisitos 

Para nortear nosso projeto, seguimos alguns requisitos. São estes:

- O robô deve se equilibrar sobre duas rodas;
- O robô deve ser capaz de receber uma posição de destino;
- O robô deve ser capaz de navegar até o destino de forma autônoma;
- O robô deve ser capaz de desviar de obstáculos enquanto navega de forma autônoma até o objetivo.

<p>
São necessários, então, condições e critérios para a satisfação dos objetivos estabelecidos. São estas:
</p>{: style="text-align: justify;"}

- Utilizar um Framework de robótica;
- Deve ser capaz de ler uma TAG;
- Deve mapear o ambiente ao seu redor e se localizar nele;
- Detectar variações de inclinação;
- Pernas articuladas com 2 DOF em sentido pitch (Y);
- Deve ser capaz de controlar a velocidade das rodas.

<!-- **************************************** -->
### Selecionando os componentes 

<p>
Aqui está uma lista completa de peças até o momento (sujeito a alterações):
</p>{: style="text-align: justify;"}

<style type="text/css">.tg-sort-header::-moz-selection{background:0 0}.tg-sort-header::selection{background:0 0}.tg-sort-header{cursor:pointer}.tg-sort-header:after{content:'';float:right;margin-top:7px;border-width:0 5px 5px;border-style:solid;border-color:#404040 transparent;visibility:hidden}.tg-sort-header:hover:after{visibility:visible}.tg-sort-asc:after,.tg-sort-asc:hover:after,.tg-sort-desc:after{visibility:visible;opacity:.4}.tg-sort-desc:after{border-bottom:none;border-width:5px 5px 0}@media screen and (max-width: 767px) {.tg {width: auto !important;}.tg col {width: auto !important;}.tg-wrap {overflow-x: auto;-webkit-overflow-scrolling: touch;margin: auto 0px;}}</style><div class="tg-wrap"><table id="tg-NPaUZ" style="border-collapse:collapse;border-color:#9ABAD9;border-spacing:0;margin:0px auto" class="tg"><thead><tr><th style="background-color:#409cff;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#fff;font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">COMPONENTES</th><th style="background-color:#409cff;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#fff;font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">QTD</th><th style="background-color:#409cff;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#fff;font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">LINK</th><th style="background-color:#409cff;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#fff;font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">VALOR TOTAL ($USD)</th></tr></thead><tbody><tr><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">DYNAMIXEL MX-106</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">4</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://www.robotis.us/dynamixel-mx-106t/" target="_blank" rel="noopener noreferrer">Dynamixel Robotis</a></td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">2159,6</td></tr><tr><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">DYNAMIXEL XM430-W210</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">2</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://www.robotis.us/dynamixel-xm430-w210-r/" target="_blank" rel="noopener noreferrer">Dynamixel Robotis</a></td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><span style="font-weight:400;font-style:normal">519,8</span></td></tr><tr><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">LiDAR</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://www.robotis.us/360-laser-distance-sensor-lds-01-lidar/" target="_blank" rel="noopener noreferrer">LiDAR Robotis</a></td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">196,1</td></tr><tr><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">OpenCM 9.04</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://emanual.robotis.com/docs/en/parts/controller/opencm904/" target="_blank" rel="noopener noreferrer">Open CM9.04 Robotis</a></td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">21,7</td></tr><tr><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">OpenCM 485 Exp.</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://emanual.robotis.com/docs/en/parts/controller/opencm485exp/" target="_blank" rel="noopener noreferrer">OpenCM 485 exp. Robotis</a></td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">32,6</td></tr><tr><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">MPU6050</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://produto.mercadolivre.com.br/MLB-1820250930-acelermetro-e-giroscopio-3-eixos-gy521-mpu6050-gy521-c-nfe-_JM?matt_tool=87716990&amp;amp;matt_word=&amp;amp;matt_source=google&amp;amp;matt_campaign_id=12413740998&amp;amp;matt_ad_group_id=119070072438&amp;amp;matt_match_type=&amp;amp;matt_network=g&amp;amp;matt_device=c&amp;amp;matt_creative=500702333978&amp;amp;matt_keyword=&amp;amp;matt_ad_position=&amp;amp;matt_ad_type=pla&amp;amp;matt_merchant_id=164968240&amp;amp;matt_product_id=MLB1820250930&amp;amp;matt_product_partition_id=337120033364&amp;amp;matt_target_id=pla-337120033364&amp;amp;gclid=CjwKCAjwiLGGBhAqEiwAgq3q_ly8hxZFz8qCPXFHc8ORE4E79RhaUB8MnjT3uuzdJ6T3VrzeIPiazBoCMR0QAvD_BwE" target="_blank" rel="noopener noreferrer">IMU MercadoLivre</a></td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">3,48</td></tr><tr><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">Camera RaspberryPI V2</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://www.filipeflop.com/produto/camera-raspberry-pi-v2-8mp/" target="_blank" rel="noopener noreferrer">Camera Filipeflop</a></td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">50,11</td></tr><tr><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">RaspberryPI 4</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://www.raspberrypi.org/" target="_blank" rel="noopener noreferrer">RPI 4 raspberrypi</a></td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">93,25</td></tr><tr><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">Borracha de silicone vermelha</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://www.redelease.com.br/catalog/product/view/id/1631/s/borracha-de-silicone-vermelha-rigida-para-fundicao-com-catalisador-1-050-kg/" target="_blank" rel="noopener noreferrer">Silicone Redelease</a></td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">11,59</td></tr><tr><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">Lipo 4s</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://produto.mercadolivre.com.br/MLB-1873655714-bateria-lipo-4s-3300mah-100c-_JM#position=4&search_layout=stack&type=item&tracking_id=43bd6937-975f-4cbd-a206-b2ad73fb843a" target="_blank" rel="noopener noreferrer">Bateria MercadoLivre</a></td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">54,72</td></tr><tr><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">Regulador tensão</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://produto.mercadolivre.com.br/MLB-1242529223-lm2596-conversor-regulador-tenso-step-down-_JM?matt_tool=87716990&amp;matt_word=&amp;matt_source=google&amp;matt_campaign_id=12413740998&amp;matt_ad_group_id=119070072438&amp;matt_match_type=&amp;matt_network=g&amp;matt_device=c&amp;matt_creative=500702333978&amp;matt_keyword=&amp;matt_ad_position=&amp;matt_ad_type=pla&amp;matt_merchant_id=147035375&amp;matt_product_id=MLB1242529223&amp;matt_product_partition_id=337120033364&amp;matt_target_id=pla-337120033364" target="_blank" rel="noopener noreferrer">Regulador MercadoLivre</a></td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">2,69</td></tr><tr><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">Precision Voltage Sensor</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://www.phidgets.com/?tier=3&amp;catid=16&amp;pcid=14&amp;prodid=1067" target="_blank" rel="noopener noreferrer">Phidgets</a></td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">17</td></tr></tbody></table></div><script charset="utf-8">var TGSort=window.TGSort||function(n){"use strict";function r(n){return n?n.length:0}function t(n,t,e,o=0){for(e=r(n);o<e;++o)t(n[o],o)}function e(n){return n.split("").reverse().join("")}function o(n){var e=n[0];return t(n,function(n){for(;!n.startsWith(e);)e=e.substring(0,r(e)-1)}),r(e)}function u(n,r,e=[]){return t(n,function(n){r(n)&&e.push(n)}),e}var a=parseFloat;function i(n,r){return function(t){var e="";return t.replace(n,function(n,t,o){return e=t.replace(r,"")+"."+(o||"").substring(1)}),a(e)}}var s=i(/^(?:\s*)([+-]?(?:\d+)(?:,\d{3})*)(\.\d*)?$/g,/,/g),c=i(/^(?:\s*)([+-]?(?:\d+)(?:\.\d{3})*)(,\d*)?$/g,/\./g);function f(n){var t=a(n);return!isNaN(t)&&r(""+t)+1>=r(n)?t:NaN}function d(n){var e=[],o=n;return t([f,s,c],function(u){var a=[],i=[];t(n,function(n,r){r=u(n),a.push(r),r||i.push(n)}),r(i)<r(o)&&(o=i,e=a)}),r(u(o,function(n){return n==o[0]}))==r(o)?e:[]}function v(n){if("TABLE"==n.nodeName){for(var a=function(r){var e,o,u=[],a=[];return function n(r,e){e(r),t(r.childNodes,function(r){n(r,e)})}(n,function(n){"TR"==(o=n.nodeName)?(e=[],u.push(e),a.push(n)):"TD"!=o&&"TH"!=o||e.push(n)}),[u,a]}(),i=a[0],s=a[1],c=r(i),f=c>1&&r(i[0])<r(i[1])?1:0,v=f+1,p=i[f],h=r(p),l=[],g=[],N=[],m=v;m<c;++m){for(var T=0;T<h;++T){r(g)<h&&g.push([]);var C=i[m][T],L=C.textContent||C.innerText||"";g[T].push(L.trim())}N.push(m-v)}t(p,function(n,t){l[t]=0;var a=n.classList;a.add("tg-sort-header"),n.addEventListener("click",function(){var n=l[t];!function(){for(var n=0;n<h;++n){var r=p[n].classList;r.remove("tg-sort-asc"),r.remove("tg-sort-desc"),l[n]=0}}(),(n=1==n?-1:+!n)&&a.add(n>0?"tg-sort-asc":"tg-sort-desc"),l[t]=n;var i,f=g[t],m=function(r,t){return n*f[r].localeCompare(f[t])||n*(r-t)},T=function(n){var t=d(n);if(!r(t)){var u=o(n),a=o(n.map(e));t=d(n.map(function(n){return n.substring(u,r(n)-a)}))}return t}(f);(r(T)||r(T=r(u(i=f.map(Date.parse),isNaN))?[]:i))&&(m=function(r,t){var e=T[r],o=T[t],u=isNaN(e),a=isNaN(o);return u&&a?0:u?-n:a?n:e>o?n:e<o?-n:n*(r-t)});var C,L=N.slice();L.sort(m);for(var E=v;E<c;++E)(C=s[E].parentNode).removeChild(s[E]);for(E=v;E<c;++E)C.appendChild(s[v+L[E-v]])})})}}n.addEventListener("DOMContentLoaded",function(){for(var t=n.getElementsByClassName("tg"),e=0;e<r(t);++e)try{v(t[e])}catch(n){}})}(document)</script>

Todas essas peças tem o valor aproximado de $USD 3162,64. 

<!-- **************************************** -->
### Definindo o modelo

<p>
Feito a seleção dos componentes e definindo as peças que vamos utilizar, podemos definir a arquitetura geral do Bbot. 
</p>{: style="text-align: justify;"}

<p>
É possível analisar que a arquitetura está dividida em três grandes blocos, que compõem a <strong>interface do usuário</strong>, a <strong>central de gerenciamento do sistema</strong> (Ubuntu 20.04 + ROS Noetic) e a <strong>interface com o hardware</strong>. 
</p>{: style="text-align: justify;"}

<p>
Podemos notar que existem pontos de conexão entre os blocos, são eles: 
</p>{: style="text-align: justify;"}

- **OpenCM 9.04:** responsável pela aquisição de dados dos sensores e da comunicação com os atuadores
- **Wi-fi:** Disponibiliza o acesso remoto com a Raspberry Pi

<p align="center">
    <img src="{{ 'assets/img/bbot/arquitetura_geral.png' | relative_url }}" alt="Arquitetura geral" width="750"/>
</p>

<!-- **************************************** -->
### Diagrama de componentes

<p>
Já com o diagrama de componentes, podemos definir as conexões entre os componentes e obter uma visão geral do projeto.
</p>{: style="text-align: justify;"}

<p>
O diagrama se divide em <strong>base</strong> e <strong>pernas</strong>. Na base do robô, nós temos os controladores, a bateria e os sensores. As pernas ficam com os atuadores. 
</p>{: style="text-align: justify;"}

<p>
É possível notar que as conexões entre os  componentes se dividem em <strong>potência</strong> (vermelho) e <strong>data</strong> (preto). Os atuadores são apresentados apenas com uma “linha” de potência, pois são conectados em cadeia, então optamos por essa descrição no diagrama.
</p>{: style="text-align: justify;"}

<p align="center">
    <img src="{{ 'assets/img/bbot/components_diagram.png' | relative_url }}" alt="Diagrama de componentes" width="750"/>
</p>

<!-- **************************************** -->
### Conclusão

<p>
Nessa primeira etapa do projeto Bbot, foi apresentado a metodologia do projeto e a definição do modelo. Com base nos parâmetros propostos aqui, podemos partir para descrição das funcionalidades do Bbot!! <img src="{{ 'assets/img/bbot/bbot.png' | relative_url }}" alt="Bbot" width="17"/> <img src="{{ 'assets/img/bbot/bbot_stand.png' | relative_url }}" alt="Bbot" width="15"/>
</p>{: style="text-align: justify;"}

<!-- **************************************** -->
### Veja a seguir

<p>
Aqui você encontra os posts relacionados às etapas de projeto do Bbot. <strong>Fique atento!!</strong>
</p>{: style="text-align: justify;"}

<a href="https://mhar-vell.github.io/rasc/2021-07-22-bbot-funcionalidades-do-bbot/"><font color="#fbb117">[Etapa 2] Funcionalidades do Bbot</font></a>

<!-- <a href="https://mhar-vell.github.io/rasc/2021-07-28-bbot-modelo-3d-do-bbot-etapa-2/"><font color="#fbb117">[Etapa 2] Construindo o Bbot (Modelo 3d)</font></a> -->
 
<!-- <a href="https://mhar-vell.github.io/rasc/2021-08-04-bbot-esquematico-ee-etapa-3/"><font color="#fbb117">[Etapa 3] Esquemático EE</font></a> - disponivel em 04/08/2021 -->

<!-- <a href="https://mhar-vell.github.io/rasc/2021-08-11-bbot-simulacao-etapa-4/"><font color="#fbb117">[Etapa 4] Simulação</font></a> - disponivel em 11/08/2021 -->

<!-- <a href="https://mhar-vell.github.io/rasc/2021-08-18-bbot-montagem-e-teste-etapa-5/"><font color="#fbb117">[Etapa 5] Montagem final e teste</font></a> - disponivel em 18/08/2021 -->

<br>
<hr>

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
<hr>


<!-- **************************************** BT TOP **************************************** -->
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 20px;
}

#myBtn {
  display: none;
  position: fixed;
  bottom: 20px;
  right: 30px;
  z-index: 99;
  font-size: 18px;
  border: none;
  outline: none;
  background-color: red;
  color: white;
  cursor: pointer;
  padding: 15px;
  border-radius: 4px;
}

#myBtn:hover {
  background-color: #555;
}
</style>
</head>
<body>

<button onclick="topFunction()" id="myBtn" title="Go to top">Top</button>

<script>
//Get the button
var mybutton = document.getElementById("myBtn");

// When the user scrolls down 20px from the top of the document, show the button
window.onscroll = function() {scrollFunction()};

function scrollFunction() {
  if (document.body.scrollTop > 20 || document.documentElement.scrollTop > 20) {
    mybutton.style.display = "block";
  } else {
    mybutton.style.display = "none";
  }
}

// When the user clicks on the button, scroll to the top of the document
function topFunction() {
  document.body.scrollTop = 0;
  document.documentElement.scrollTop = 0;
}
</script>

</body>
</html>