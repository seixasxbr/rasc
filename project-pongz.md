---
layout: page
title: PongZ
subtitle: Uma releitura do pong para os tempos atuais.
#cover-img: https://i.imgur.com/9AJowrB.png[/img]
---

<th><center><iframe src="https://giphy.com/embed/l8DL07tSFOLLd7LQL5" width="500" height="250" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p></p></center></th>

# Um pouco de história
<div style="text-align: justify"> 
O Pong é considerado o primeiro jogo da história em formato de vídeo a ser lucrativo. Criado por  Nolan Bushnell e Ted Dabney, o jogo se inspira no clássico jogo de tênis de dois jogadores em que as hastes/barras simulam as raquetes, e a bola da mesma forma que em uma partida de tênis, percorre a quadra até um dos jogadores não conseguir rebater. A versão clássica do PONG consiste em um console ligado a um monitor, sendo as hastes movidas por moedas.
</div>

# O PongZ
<div style="text-align: justify"> 
Nesta versão que adotamos o nome de PongZ, sendo "Pong" o nome do jogo original e "Z" o termo que remete o nascimento da geração dos desenvolvedores. Neste projeto resolvemos remodelar o design, mas sem alterar a essência do jogo, trazendo uma clássica trilha sonora dos anos 70. Além disso, no lugar das moedas que moviam as hastes temos potenciômetros, e um arduino que faz a interpretação desses dados e envia para o computador através da porta USB, contendo também informações dos botões push buttons que permitem o jogador controlar pausar e resetar o jogo.
</div>

### O desafio
<div style="text-align: justify"> 
O PongZ é um projeto criado dentro da disciplina de Sistemas Embarcados no curso de Engenharia Elétrica do SENAI CIMATEC ministrado pelo Prof. Marco Reis, com intuito de explorar as habilidades desenvolvidas durante a disciplina, como fazer a interação entre software e hardware através de comunicação serial e manipulação de dados capturados em um sistema embarcados.
</div>

### Um pouco sobre o desenvolvimento
<div style="text-align: justify"> 
O hardware do projeto conta com dois botões, dois potenciômetros e um arduino. Quanto ao software, o arduino foi programado para monitorar os sensores e enviar estes dados através da comunicação serial, enquanto um algoritmo em Processing 3 foi responsável pela interface do jogo.

Para uma melhor didática de como foram feitas as conexões dos potenciômetros e push buttons ao arduino, foi demonstrado no Tinkercad conforme a imagem abaixo. As ligações dos potenciômetros foram, respectivamente, o terminal 1 ligado ao GND, o terminal 2 aos pinos analógicos A0 e A2 e o terminal 3 ligado ao 5V. Já os push buttons, foram ligados, respectivamente, o terminal 1B aos pinos digitais 9 e 8 e o terminal 2B ao GND.
</div>


<th><center><img src="{{ 'assets/img/pongz/pong_circuito.png' | relative_url }}" width="500" alt="Alexandre" class="img" /></center></th>

<br>

#//TODO realizar o video com informações ao público
## Live Game
O vídeo abaixo tem como objetivo representar a versão final do jogo, demonstrando a jogabilidade e suas funções.

<div class="embed-responsive embed-responsive-16by9">

<iframe width="415" height="315" src="https://www.youtube.com/embed/Yl8Gpslcpxw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

</div>
<br>

## O que foi possível aprender?
<br>
<div style="text-align: justify">
Através do Arduino junto ao Processing, foi possível perceber um pouco de como funciona o desenvolvimento de um game.A equipe teve diversas dificuldades, mas nada que, por meio de pesquisas junto ao conhecimento aprendido em Sistemas Embarcados, não tornasse possível a conclusão do clássico jogo Pong.
</div>
<div style="text-align: justify">
Assim, nesse desafio foi aplicado a utilização de sensores e atuadores, leitura de sinais analógicos e digitais, comunicação entre componentes, criação de representações do mundo físico no mundo digital e muitos outros assuntos.  Concluir o PongZ foi uma tremenda conquista, foi descoberto novas áreas da engenharia o que deixou a equipe inspirada a realizar conquistas ainda maiores.
</div>


<br/>
<br/>

<center><h3 class="post-title">Equipe de desenvolvimento</h3><br/></center>
<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><a href="https://www.linkedin.com/in/alexandre-adonai-gama-da-silva-365a35211/"><center><img src="{{ 'assets/img/people/alexandreadonai-1.png' | relative_url}}" 
          width="100" alt="Alexandre"
          class="img-fluid rounded-circle" /></center></a></th>
          <th></th>
          <th><a href="http://lattes.cnpq.br/3714599132684846"><center><img src="{{ 'assets/img/people/gabrielcalmon-1.png' | relative_url}}" 
          width="100" alt="Alexandre"
          class="img-fluid rounded-circle" /></center></a></th>
          <th></th>
          <th><a href="https://www.linkedin.com/in/jo%C3%A3o-v%C3%ADtor-s-mendes-aa2ab71b5/"><center><img src="{{ 'assets/img/people/vitormendes-1.png' | relative_url}}" 
          width="100" alt="Alexandre"
          class="img-fluid rounded-circle" /></center></a></th>
          <th></th>
          <th><a href="https://www.mhar-vell.github.io/portifolio/"><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url}}" 
          width="100" alt="Alexandre"
          class="img-fluid rounded-circle" /></center></a></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
         <td width="25.00%">Alexandre Adonai</td>
          <td></td>
          <td width="25.00%">João Gabriel Calmon</td>
          <td></td>
          <td width="25.00%">João Vítor Mendes</td>
          <td></td>
          <td width="25.00%">Marco Reis</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Graduando em Eng. Elétrica.</small></td>
          <td></td>
          <td style="vertical-align: top"><small>Graduando em Eng. Elétrica.</small></td>
          <td></td>
          <td style="vertical-align: top"><small>Graduando em Eng. Elétrica.</small></td>
          <td></td>
          <td style="vertical-align: top"><small>Pesquisador Sênior do projeto <br>Mestre em Engenharia de Produção e Eng. Eletricista.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

## Resumo do Projeto

1. Categoria: Sistemas Embarcados
2. Prazo: 20 dias
3. Data de início: 25/05/2021
4. Data de término: 14/06/2021
5. Repositório URL: [PongZ](https://github.com/GabrielCalmon/Desafio_Pong_2021-1)
6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>
7. Recursos materiais: US$ 42.00
8. Apresentação URL: [PongZ-ppt](https://drive.google.com/drive/folders/188Juz5FEUqrq5PzuuWtxbnuLv0CRaUem?usp=sharing) 
9. Report URL: [PongZ-report](https://drive.google.com/drive/folders/188Juz5FEUqrq5PzuuWtxbnuLv0CRaUem?usp=sharing) 

<br>

##### Referências
1. [TinkerCAD DashBoard](https://www.tinkercad.com/things/alnQmejrYC8-pong-av3/editel). Tinkercad Dashboard. Acesso em: 19 de Julho de 2021.
2. [MasterWalker](https://blogmasterwalkershop.com.br/arduino/arduino-utilizando-o-potenciometro-linear). Como usar com Arduino-chave táctil/pushbutton. Acesso em: 19 de Julho de 2021.
3. [MasterWalker](https://blogmasterwalkershop.com.br/arduino/arduino-utilizando-o-potenciometro-linear). Como usar com Arduino – potenciômetro linear 10k com eixo estriado. Acesso em: 19 de Julho de 2021.
4. [Arduino](https://www.arduino.cc/reference/pt/). Documentação de Referência da Linguagem Arduino. Acesso em: 19 de Julho de 2021.
5. [Processing](https://processing.org/reference/). Reference: processing was designed to be aflexible software sketchbook. Acesso em: 19 de Julho de 2021.
6. [Techtudo](https://www.techtudo.com.br/noticias/noticia/2016/03/conheca-pong-o-primeiro-videogame-lucrativo-da-historia.html). Conheça Pong, o primeiro videogame lucrativo da história. Acesso em: 19 de Julho de 2021.
