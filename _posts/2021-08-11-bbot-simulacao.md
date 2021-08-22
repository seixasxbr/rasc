---
layout: post
title: Simulação do Bbot
subtitle: Simulação do sistema de controle e teleoperação do Bbot
cover-img: assets/img/bbot/bbot_wide.png
thumbnail-img: assets/img/bbot/bbot.png
share-img: assets/img/rosa-logo-redondo.png
comments: true
tags: [bbot]
---
# Anteriormente
É importante que você tenha visto o post anterior [Desenho mecânico do Bbot](https://mhar-vell.github.io/rasc/2021-08-04-bbot-desenho-mecanico/), para um completo entendimento do desenvolvimento do projeto.

## Introdução

Na etapa quatro do processo de construção do <a href="https://mhar-vell.github.io/rasc/project-bbot/"><font color="#fbb117">Bbot</font></a>, podemos analisar o desenvolvimento de sua simulação feita no Gazebo, utilizando o ROS Noetic.

Caso você não saiba, o _Robot Operating System_ (ROS) é um _framework_ de robótica _OpenSource_ com diversas ferramentas implementadas para facilitar o desenvolvimento de aplicações em robótica. Você pode consultar este [link](http://wiki.ros.org/ROS/Introduction) para mais informações sobre o ROS. Para o desenvolvimento do **Bbot**, estamos usando a versão do ROS Noetic.

<hr>

<!-- **************************************** -->
## Representação e controle do sistema

O **Bbot**, assim como vários outros robôs de alto-balanceamento, pode ser tratado como um pêndulo invertido. Diferente de um pêndulo convencional, esse sistema visa equilibrar a sua haste na posição vertical para cima, como mostrado na figura abaixo.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/pend_inv.png' | relative_url }}" alt="Pêndulo invertido" width="150" height="250"/>
</p>

Ao deixá-lo oscilar livremente, o pêndulo irá cair até tocar o chão. Contudo, caso uma força seja exercida na base do robô, de forma a deslocá-lo para frente ou para trás, uma pseudo-força (que é a inércia) agirá sobre a haste no sentido contrário ao torque aplicado pelo seu próprio peso. Com a força adequada, podemos fazer o pêndulo voltar à posição vertical. Como esta posição é instável, a haste voltará a cair e, portando, outra força deve ser aplicada. 

Caso possamos monitorar a inclinação instantânea do pêndulo e, a partir dela, calcular e exercer a força adequada para que ele volte à posição vertical, conseguiremos mantê-lo em equilíbrio. A seguir está o diagrama de blocos do sistema. 

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/basic_block_diag.png' | relative_url }}" alt="Diagrama de blocos" width="420"/>
</p>

Este é um sistema realimentado, onde estaremos a todo tempo enviando a inclinação de equilíbrio do robô como entrada (~ 0°) e mandando para o controlador a diferença entre esta e a inclinação atual do robô. Este sinal, chamado de "erro", é a entrada do controlador, o qual este usará para calcular a força necessária para manter o **Bbot** em equilíbrio.

O controlador será do tipo PID (_**P**roportional-**I**ntegral-**D**erivative_). Este tipo de controlador é um dos mais utilizados em sistemas de controle. Ele pode ser descrito pela seguinte equação:

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/pid_eqt.png' | relative_url }}" alt="Equação do PID" width="340" height="70"/>
</p>

Como podemos ver, ele possui 3 parâmetros de configuração: **Kp**, **Ki** e **Kd**. Cada um desses influencia na velocidade de recuperação da posição de equilíbrio, no tempo necessário para que ele se estabilize nessa posição e no tipo de resposta transitória que o sistema terá para alcançar o equilíbrio. Caso você queira saber mais sobre o controlador PID, pode acessar este [link](https://en.wikipedia.org/wiki/PID_controller).

### Configurando a simulação no ROS

Para poder simular o **Bbot** no ROS, criamos um arquivo URDF (_Unified Robot Description Format_), que contêm todas as informações necessárias para simular o robô no Gazebo. Neste arquivo estão definidas todas as partes móveis do robô, assim como tipo de juntas, parâmetros inerciais e de colisão, além dos aspectos visuais, baseados no desenho mecânico que fizemos e mostramos no post anterior ([clique aqui](https://mhar-vell.github.io/rasc/2021-08-04-bbot-desenho-mecanico/) para saber mais). 

Para poder enviar comandos de velocidade para o robô e conseguir movê-lo para frente e para trás, assim como girar em torno do próprio eixo, utilizamos um controlador de direção diferencial implementado no pacote [ros_control](http://wiki.ros.org/ros_control).

Como o **Bbot** possui pernas articuladas, também configuramos controladores de posição para cada uma das suas juntas. Contudo, para esta simulação, não utilizaremos o controle das pernas.

Até então, seria possível mover o robô, mas para que ele seja autônomo, são necessários alguns sensores para que este consiga sentir o ambiente ao seu redor, ter noção de sua posição e orientação no espaço, além de ver o que está a sua frente. Portando, também no URDF, configuramos os _plugins_ do Gazebo que simulam um sensor IMU (_Inertial Mesurement Unit_), para monitorar a inclinação do robô assim como sua velocidade e aceleração angular em 3 dimensões; um Lidar (_Light Detection and Ranging_), para identificar possíveis obstáculos e uma câmera, que nos permite usar a visão computacional para dar mais inteligência ao robô.

Criamos, então, três pacotes para guardar todas essas informações:
- **bbot_description**: contém o arquivo URDF e os arquivos de renderização do **Bbot**.
- **bbot_gazebo:** contém a arquivo do mundo virtual e arquivos .launch para iniciar a simulação.
- **bbot_control:** contém os arquivos de configuração dos controladores das juntas além do algoritmo de controle que mantêm o robô equilibrado.

Com tudo isso configurado, já podemos visualizar o robô no Gazebo e também no Rviz.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/bbot_in_gazebo.png' | relative_url }}" alt="Visualização do Bbot no Gazebo" width="750"/>
</p>

### Algoritmo de Controle

Para criar o algoritmo de controle do robô, utilizamos um pacote do ROS [pid](http://wiki.ros.org/pid), que implementa um controlador do tipo PID que já utiliza toda a interface do ROS como tópicos e parâmetros. Este pacote contém um nó que, após receber uma mensagem pelo tópico `/setpoint`, é habilitado e, sempre que recebe uma mensagem pelo tópico `/state`, calcula o erro entre ambas, aplica a fórmula do PID e publica outra mensagem no tópico `/control_effort`. O processo acontece de forma assíncrona, portando, cabe ao usuário manter as publicações em `/state` o mais constante possível na frequência que desejar. Manter o _loop_ de controle em uma frequência única eleva a precisão do controlador e melhora os resultados. No caso do **Bbot**, o _loop_ de controle roda a 100 Hz, que é a frequência de aquisição das informações de inclinação, fornecida pelo IMU.

Como o algorítmo do controlador já está pronto, criamos um nó que apenas redireciona as informações necessárias compartilhadas pela interface do ROS para os tópicos certos com o formato de mensagem adequado. Caso você esteja ouvindo esses termos referentes ao ROS pela primeira vez, vale a pena dar uma olhada nesse tutorial: [link](http://wiki.ros.org/ROS/Tutorials/UnderstandingTopics).

Uma representação gráfica dos processos que ocorrem no ROS pode ser visto na figura abaixo.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/rosnode_diagram.png' | relative_url }}" alt="Diagrama de processos no ROS" width="750"/>
</p>

Nesta imagem, há dois controladores PID. O controlador `/balancing_pid` calcula o esforço de controle para manter o robô equilibrado em uma angulação específica, enquanto o controlador `/velocity_pid` qual é este ângulo, com base nos comandos de velocidade que o robô recebe do usuário ou, eventualmente, de um planejador de trajetórias.

O nó `/freq_pub` tem a função de diminuir a frequência de publicações no tópico `/setpoint` do `/balancing_pid`, para diminuir ruído no controle. Como estas mensagens alteram o ângulo de equilíbrio e o robô precisa de tempo para se estabilizar, notamos pela simulação que gerar mudanças nesse a cada 0,01 segundos gerava muito ruído no controlador.

Uma representação do mesmo sistema em formato de diagrama de blocos pode ser visto abaixo.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/control_diagram.png' | relative_url }}" alt="Diagrama de blocos do sistema" width="750"/>
</p>

Pode-se notar que os dados que são realimentados no controlador `/velocity_pid` não é o comando de velocidade mais atual do robô, mas a média dos últimos N comandos. Utilizamos N = 100. Essa medida também é uma forma de diminuir ruídos no controlador, pois os comandos de velocidade podem variar rapidamente, porém sua média é uma informação mais estável e fácil de controlar.

### Resultados da simulação

Após alguns dias ajustando os parâmetros dos controladores e aperfeiçoando o sistema, conseguimos fazer o **Bbot** se equilibrar e teleoperá-lo.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/Bbot_teleop.gif' | relative_url }}" alt="Teleoperação do Bbot" width="750"/>
</p>

Testamos também a reação dele a esforços externos:

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/resistence_test.gif' | relative_url }}" alt="Teste de resistência do Bbot" width="750"/>
</p>

Na **quarta etapa** do projeto, nós apresentamos o desenvolvimento do sistema de controle e teleoperação do **Bbot**. <img src="{{ 'assets/img/bbot/bbot.png' | relative_url }}" alt="Bbot" width="17"/> &#128295; <img src="{{ 'assets/img/bbot/bbot_stand.png' | relative_url }}" alt="Bbot" width="15"/>
<br>

Para as próximas etapas, serão apresentados a impressão e montagem do robô, assim como os testes do sistema com o robô real.

----------------

<br>

<!-- **************************************** Autor **************************************** -->
<center><h3 class="post-title">Autor</h3><br/></center>

<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
            <th><center><a href="https://www.linkedin.com/in/lucas-lins-souza-51b1909a/" target="_blank">
                <p align="center">
                    <img src="{{ 'assets/img/people/lucaslins-1.png' | relative_url }}" alt="Not found" width="100" class="img-fluid rounded-circle" />
                </p>
            </a></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center; margin-top: 0">
          <td width="33.33%">Lucas Lins</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top;text-align: justify;"><small>Estagiário no laboratório de Robótica e Sistemas Autônomos (RoSA), SENAI CIMATEC, graduando em Engenharia Elétrica no SENAI CIMATEC.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>
