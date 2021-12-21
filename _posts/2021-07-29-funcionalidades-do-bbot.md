---
layout: post
title: Funcionalidades do Bbot
subtitle: A importância das funcionalidades
cover-img: assets/img/bbot/bbot_wide.png
thumbnail-img: assets/img/bbot/bbot.png
share-img: assets/img/rosa-logo-redondo.png
author: Matheus França
comments: true
tags: [bbot]
---
# Anteriormente
É importante que você tenha visto o post anterior, [Definição do modelo Bbot](https://mhar-vell.github.io/rasc/2021-07-21-bbot-definição-do-modelo-bbot/), para um completo entendimento do desenvolvimento do projeto.


Na <strong>etapa dois</strong> do processo de construção do <a href="https://mhar-vell.github.io/rasc/project-bbot/"><font color="#fbb117">Bbot</font></a>, e de qualquer outro projeto de robótica, é <strong>importante</strong> definir as <strong>funcionalidades</strong> do robô. Antes de iniciarmos as próximas etapas, o desenho da arquitetura do robô (mão na massa!! 👷🔧), precisamos listar essas características e analisar como elas estão conectadas entre si, tendo assim um total controle do desenvolvimento do projeto. 


<hr>

<!-- **************************************** -->
## Diagrama das funcionalidades

No diagrama construído para o Bbot, podemos ver uma gama de funcionalidades. Para facilitar o entendimento, vamos particionar o diagrama em seções de funcionalidade.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/diagrama_funcionalidades_v2.png' | relative_url }}" alt="Diagrama de funcionalidades" width="750"/>
</p>

### Localização

A **localização** é responsável por monitorar da posição e orientação do robô dentro do ambiente no qual está contido. Usando os dados de posicionamento e orientação, enviados pelos sensores presentes no sistema de percepção, esta funcionalidade fornece aos sistemas de mapeamento e planejamento de trajetória uma mensagem contendo os dados de posição e orientação do robô no ambiente. A funcionalidade **localização** serve de base para outras funcionalidades que promovem autonomia ao robô.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/df-localizacao.png' | relative_url }}" alt="Not found" width="750"/>
</p>

### Navegação

A navegação para o bbot utiliza o **_planejamento local_** e **_global_** para transitar de forma segura no ambiente. O sistema de **_navegação_** possui como dependência a funcionalidade de **_planejamento de trajeto_**. Como saída da funcionalidade de navegação, será enviado a execução da trajetória e, na falha de uma adequada navegação, envia um comando de **_replanejamento de trajeto_**. 

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/df-navegacao.png' | relative_url }}" alt="Not found" width="750"/>
</p>

### Percepção

O sistema de percepção do **Bbot**, através de sensoriamento, deve fornecer ao robô a capacidade de perceber e traduzir as suas próprias condições e as condições do ambiente no qual está inserido. Essas funções são garantidas pela aquisição e processamento de dados coletados de sensores inerciais e sensores ópticos, os quais estão integrados à estrutura do robô. O sistema de percepção oferece, portanto, modelagem do robô e do ambiente obtida pela representação dos dados de IMU, LiDAR 2D, Câmera e Sensor de tensão e pelos algoritmos de tratamento aplicados a esses dados.

A funcionalidade de **_percepção_** depende dos dados sensoriais que estão incorporados na estrutura do robô.

As saídas desta funcionalidade são o **_mapeamento_**, **_localização_**, **_detecção_** e **_controle_**.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/df-percepcao.png' | relative_url }}" alt="Not found" width="750"/>
</p>

### Mapeamento

Utilizando as informações da **_localização_**, é possível criar um mapa do ambiente.

A funcionalidade de **_mapeamento_** depende dos dados de **_percepção_** (pontos 3d do sensor LiDAR) e **_localização_**.

Através dos mapa, é possível gerar um **_costmap global_** e um **_costmap local_**, que é utilizado pela funcionalidade de **_planejamento de trajetória_** para identificar a posições do mapa onde o robô não pode transitar e pela funcionalidade de **_navegação_** para planejar os controles de velocidade do robô de forma que ele não colida com os obstáculos.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/df-mapeamento.png' | relative_url }}" alt="Not found" width="750"/>
</p>

### Detecção

No **Bbot** essa funcionalidade é responsável pela detecção da TAG (importante para missão do robô). Depende dos dados da funcionalidade de **_percepção_** e tem como saída o **_planejamento de trajetória_** (enviando a pose de destino).

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/df-deteccao.png' | relative_url }}" alt="Not found" width="750"/>
</p>

### Controle

Define a estratégia adotada para que o robô consiga se equilibrar. No nosso caso, foi escolhido o controlador PID. Depende da funcionalidade da **_percepção_** e tem como saída os comandos de velocidade do robô para que ele consiga de equilibrar.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/df-controle.png' | relative_url }}" alt="Not found" width="750"/>
</p>

### Comportamento

O **_comportamento_** tem como função avaliar as situações do ambiente e do estado do robô. Esta funcionalidade é genérica e pode ser descrita como um tomador de decisões que garantem o bom funcionamento do robô. No caso do Bbot, esta funcionaliade irá monitorar a carga atual da bateria e garantir que o robô interrompa sua missão e sinalize o usuário caso esta esteja abaixo de um dado valor. Esta funcionalidade, no entanto, pode ser incrementada futuramente para englobar outras decisões. 

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/df-comportamento.png' | relative_url }}" alt="Not found" width="750"/>
</p>

### Inatividade

É a funcionalidade que dá ao robô uma posição de proteção por motivos de falha. Ela tem como entradas as falhas do robô e como saída a **_posição de inatividade_**. 

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/df-inatividade.png' | relative_url }}" alt="Not found" width="750"/>
</p>

### Planejamento de trajetória

Recebe dados do **_mapeamento_**, **_detecção_**, **_localização_** e **_navegação_** e, seguindo uma trajetória definida na interface, faz um planejamento adequado para o robô. Tem como saída o path global e local para a funcionalidade de **_navegação_**.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/df-planejamento_de_trajetoria.png' | relative_url }}" alt="Not found" width="750"/>
</p>

### Atuação

Essa funcionalidade torna possível o controle dos atuadores das pernas e de locomoção. Tem como entrada os comandos de velocidade dados pelo **_controle_** e como saída os comandos de movimento para cada junta do robô. Esta funcionalidade faz a comunicação direto com o _hardware_.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/df-atuacao.png' | relative_url }}" alt="Not found" width="750"/>
</p>

### Conclusão

<p>
Na <strong>segunda etapa</strong> do projeto, nós apresentamos as funcionalidades e como elas estão relacionadas. Com base nesses parâmetros propostos aqui, podemos partir para a construção do Bbot!! <img src="{{ 'assets/img/bbot/bbot.png' | relative_url }}" alt="Bbot" width="17"/> &#128295; <img src="{{ 'assets/img/bbot/bbot_stand.png' | relative_url }}" alt="Bbot" width="15"/>
</p>{: style="text-align: justify;"}

<br>

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
