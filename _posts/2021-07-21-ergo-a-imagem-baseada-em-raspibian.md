---
layout: post
title: A imagem baseada em Raspibian
subtitle: Testando a interface do Ergo by Breno Portela
cover-img: /assets/img/ergo/ergo.jpeg
thumbnail-img: /assets/img/ergo/ergo_real.jpg
share-img: /assets/img/rosa-logo-redondo (180).png
tags: [ergo]
---

### Ergo OS image

Diante de várias tentativas de simular a movimentação do Ergo, a equipe deu seguimento nas atividades para efetuar os testes no modelo real seguindo as instruções de [instalação do software](https://docs.poppy-project.org/en/installation/#you-want-to-try-poppy-robots-in-a-simulator-or-in-a-web-viewer), que sugeria inserir uma [imagem](https://github.com/poppy-project/poppy-ergo-jr/releases/) de sistema operacional disponibilizada no repositório do projeto. Os recursos deste sistema operacional eram apresentados em uma [postagem](https://poppy.discourse.group/t/poppy-ergo-jr-new-software-updates-are-available-in-alpha-version/4925) do forum do projeto junto com algumas figuras de captura de tela que apresentavam o funcionamento de algumas etapas da interface disponibilizada no sistema operacional. Após a instalação da imagem no cartão SD e inicializar a raspberry pi 4, percebeu-se que a interface apontada no forum não era apresentada no momento em que o sistema era ligado e sim uma tela de área de trabalho apresentada na imagem a seguir. Houve então uma necessidade de se pesquisar um pouco mais para que fosse ao menos possível efetuar os testes na interface citada.

<p align="center">
    <img src="{{ 'assets/img/ergo/ergo-rasp.jpg' | relative_url }}" alt="Not found"/>
</p>

### Explorando o sistema operacional

Após uma breve pesquisa, foi encontrado o repositório da web interface de nome [puppet-master](https://github.com/poppy-project/puppet-master), que descrevia os passos para o acesso a interface, algo que não foi apresentado nas instruções de instalação. Com o acesso a interface foi dado início às etapas para acionar o robô, começando pela conexão a interface e montagem do robô apresentados como concluído na figura a seguir.

<p align="center">
    <img src="{{ 'assets/img/ergo/ergo_connection.png' | relative_url }}" alt="Not found"/>
</p>

Com a interface confirmando a conexão e o robô montado, prosseguiu-se para a etapa de acionar o robô, que infelizmente apontou problema quanto a encontrar os motores. Foi perceptível de que o aviso apontava que o script estava tentando encontrar os motores em uma porta que não condizia com a que estava sendo utilizada, porém após alterar para a porta _/dev/ttyACM0_ o erro persistiu como mostra na figura a seguir.

<p align="center">
    <img src="{{ 'assets/img/ergo/ergo_wake_up.png' | relative_url }}" alt="Not found"/>
</p>

Apesar do erro, a equipe jé tinha garantia de que todos os motores estavam sendo encontrados e que a comunicação estava tudo nos conformes como observado na figura abaixo.

<p align="center">
    <img src="{{ 'assets/img/ergo/ergo_dynamixels.png' | relative_url }}" alt="Not found"/>
</p>

Na tentativa de que a interface detectasse os motores para que o robô fosse testado, foi utilizado a ferramenta da interface para que a própria interface configurasse os motores, porém o procedimento não funcionou e apresentou erro de comunicação como visto na figura a seguir.

<p align="center">
    <img src="{{ 'assets/img/ergo/ergo_motor_configure.png' | relative_url }}" alt="Not found"/>
</p>

Mesmo com todos os erros, ao menos foi testado se a interface de interação dos motores visto na figura abaixo, que apesar de não ser em ROS era ao menos um pouco semelhante ao acionamento via Rviz. Apesar da possibilidade da ferramenta de acionar os motores, em momento algum o robô se mexeu.

<p align="center">
    <img src="{{ 'assets/img/ergo/ergo_no_move.png' | relative_url }}" alt="Not found"/>
</p>

<br>

----

<br>

<!-- Autor -->
<center><h3 class="post-title">Autor</h3><br/></center>
<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><center><img src="{{ 'assets/img/people/breno-1.png' | relative_url }}" width="100" alt="breno" class="img-fluid rounded-circle"/></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="33.33%">Breno Portela</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Bolsista no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduado em Engenharia Mecânica no Senai Cimatec.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>