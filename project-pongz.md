---
layout: page
title: PongZ
subtitle: Uma releitura do pong para os tempos atuais.
#cover-img: https://i.imgur.com/9AJowrB.png[/img]
---

<th><center><iframe src="https://giphy.com/embed/l8DL07tSFOLLd7LQL5" width="500" height="250" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p></p></center></th>

# Um pouco de história
<div style="text-align: justify"> 
O Pong é considerado o primeiro jogo a se tornar lucrativo na história em formato de vídeo. Criado por  Nolan Bushnell e Ted Dabney, foi baseado no clássico jogo de tênis de dois jogadores, em que as hastes/barras simulam as raquetes que rebatem a bola com objetivo de ultrapassar as linhas laterais que os jogadores devem proteger, caso isso não aconteça um ponto será concedido a favor daquele que rebateu a bola. A versão clássica do PONG consiste em um console ligado a um monitor, sendo as hastes movidas por moedas.
</div><br>

# O PongZ
<div style="text-align: justify"> 
Nesta versão que adotamos o nome de PongZ, sendo "Pong" o nome do jogo original e "Z" o termo que remete a geração de nascimento dos desenvolvedores. Neste projeto resolvemos remodelar o design, mas sem alterar a essência do jogo, trazendo uma clássica trilha sonora dos anos 70. Além disso, no lugar das moedas que moviam as hastes usamos potenciômetros, e um arduino que faz a interpretação desses dados e envia para o computador através da porta USB, contendo também informações dos push buttons que permitem o jogador controlar, pausar e reiniciar o jogo.
</div><br>

### O desafio
<div style="text-align: justify"> 
O PongZ é o resultado do que começou como um trabalho passado pelo professor Marco Reis na disciplina de Sistemas Embarcados no curso de Engenharia Elétrica do SENAI CIMATEC. A ideia era desenvolver um jogo inspirado no clássico Pong com o objetivo de que assim nós pudéssemos usar todos os conhecimentos aprendidos durante o semestre de uma única vez e num mesmo projeto. 
</div><br>

### Um pouco sobre o desenvolvimento
<div style="text-align: justify"> 
Para construção da parte física do projeto, o hardware, nós dois botões: um para pausar e o outro para reiniciar a partida, dois potenciômetros, que funcionaram como os joysticks e um arduino. Para mostrar como esses componentes foram conectados ao arduino nós fizemos um esquema de ligação usando o Tinkercad. Veja ele na imagem abaixo.

<br><th><center><img src="{{ 'assets/img/pongz/pong_circuito.png' | relative_url }}" width="500" alt="Esquema de Ligacao" class="img" /></center></th>
<br>

Já para a parte da programação, o software, nós programamos o arduino para verificar se algum botão havia sido apertado ou se algum potenciômetro tinha sido girado e então enviar essa informações para o computador. No computador, por sua vez, nós usamos um programado chamado Processing 3 para criar a interface gráfica do jogo.

Quando conseguimos recriar as mecânicas básicas do jogo percebemos que poderíamos adicionar algumas novidades a ele para dar uma aparência única e mais moderna ao jogo, já que muitas características do Pong clássico como conhecemos foram desenvolvidas dessa forma por limitações da tecnologia da época. Assim, nós demos ao campo uma nova cor, tornamos as barras de rebatimento um pouco mais arredondas, adicionamos uma música de fundo e demos um efeito à bola para que ela começasse totalmente branca e fosse se tornando cada vez mais avermelhada a cada rebatida para mostrar ao jogadores que ela estava ficando cada vez mais rápida.
</div><br>

## Live Game
O vídeo abaixo mostra versão final do jogo, tanto o que é mostrado na tela do computador, quanto o uso dos botões e do potenciômetro.

<div class="embed-responsive embed-responsive-16by9">

<iframe width="415" height="315" src="https://www.youtube.com/embed/Yl8Gpslcpxw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
          width="100" alt="alexandreadonai"
          class="img-fluid rounded-circle" /></center></a></th>
          <th></th>
          <th><a href="http://lattes.cnpq.br/3714599132684846"><center><img src="{{ 'assets/img/people/gabrielcalmon-1.png' | relative_url}}" 
          width="100" alt="gabrielcalmon"
          class="img-fluid rounded-circle" /></center></a></th>
          <th></th>
          <th><a href="https://www.linkedin.com/in/jo%C3%A3o-v%C3%ADtor-s-mendes-aa2ab71b5/"><center><img src="{{ 'assets/img/people/vitormendes-1.png' | relative_url}}" 
          width="100" alt="vitormendes"
          class="img-fluid rounded-circle" /></center></a></th>
          <th></th>
          <th><a href="https://www.mhar-vell.github.io/portifolio/"><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url}}" 
          width="100" alt="marcoreis"
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
4. [Arduino](ttps://www.arduino.cc/reference/pt/). Documentação de Referência da Linguagem Arduino. Acesso em: 19 de Julho de 2021.
5. [Processing](https://processing.org/reference/). Reference: processing was designed to be aflexible software sketchbook. Acesso em: 19 de Julho de 2021.
6. [Techtudo](https://www.techtudo.com.br/noticias/noticia/2016/03/conheca-pong-o-primeiro-videogame-lucrativo-da-historia.html). Conheça Pong, o primeiro videogame lucrativo da história. Acesso em: 19 de Julho de 2021.
