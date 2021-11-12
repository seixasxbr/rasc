---
layout: post-page
title: Desafio de Visão Computacional 
subtitle: Como recuperar informação de imagens incompletas 
cover-img: /assets/img/wesley-pribadi-iS1NV9yN0Lg-unsplash.jpg
thumbnail-img: /assets/img/ubuntu.png
share-img: /assets/img/rosa-logo-redondo.png
comments: true
---

<!-- ## Introdução -->

Quem se interessa por tecnologia e acompanha os noticiários deve se espantar com a velocidade com que ocorrem os avanços atualmente. A cada dia  são noticiados um novo computador quântico, uma nova forma de obtenção de energia ou ainda novas aplicações de inteligência artificial . Uma área que tem recebido bastante atenção é a **visão computacional**, sendo esta uma área de estudos que trata o problema de fazer com que máquinas possam enxergar. Isto é alcançado por meio do desenvolvimento de teorias e tecnologias que permitam a construção de sistemas artificiais que obtenham informações de imagem e vídeo. Este intenso interesse e esforço depositado está relacionado às possibilidades de aplicação desta visão. Outros fatores motivantes são o barateamento de câmeras, aperfeiçoamento de hardware dedicado e desenvolvimento de novos algoritmos.
Umas das principais aplicações da visão computacional é a detecção e identificaçao de objetos e obstaculos em ambientes de trânsitos. Estas aplicações são importante tanto para [ADAS](https://en.wikipedia.org/wiki/Advanced_driver-assistance_systems) ( Advenced Driver-assistance System) quanto para Carros Autônomos e 

Contudo, todo este desenvolvimento se ampara em uma série de etapas que passam pela filtragem e melhoramentos da informações bem como extração de características destas.
Dentre das habilidades básicas para se trabalhar em visão computacional está a capacidade de manipular adequadamente as informações contidas em imagens. Neste sentido, este post apresenta a solução de um desafio que consiste na recuperação de informação em uma imagem de cartas submetidas a oclusão e distorção de perspectiva.



## O Desafio

O desafio consiste em realizar transformações de modo a corrigir determinada imagem. Esta imagem consiste em um conjunto de cartas em perspectiva e sob oclusão. Deste modo, para resolver o desafio, as castas devem ser apresentadas na forma retangular e sem oclusão.




<br>

<!-- detalhamento -->

## 1. Acesso ao *root* da máquina
Inicie a sua máquina e pressione o botão **ESC** até que a tela do GRUB apareça.

Algo similar a isto...

![](../assets/img/page-senha/GRUB-1.png)

Clique em *Advanced options for Ubuntu*, logo depois você deverá escolher o modo *Recovery Mode* do Ubuntu.

![](../assets/img/page-senha/GRUB-2.png)

Ao selecionar o modo *RECOVERY*, você será direcionado para o *Recovery Menu*.

![](../assets/img/page-senha/GRUB-3-ROOT.png)

Escolha a opção *root - drop to root shell prompt*.

<br>

## 2. Acessando o *root* da máquina
Você deverá agora montar o sistema de arquivos de **somente leitura** para **permissão de escrita**:

`mount -o rw,remount /`

Agora você estará no ponto para alterar a sua senha.

<br>

## 3. Alterando a senha
Para alterar a senha, você deverá executar o seguinte comando (lembrando que o **nomedousuário** é justamente o nome do usuário que esqueceu a senha para entrar no Ubuntu):

`sudo passwd nomedousuário`

Defina a nova senha e confirme.

Com a nova senha definida, você deverá agora sair do *root* executando o seguinte comando:

`exit`

<br>

## 4. Saindo do modo de recuperação
Ao executar o comando `exit`, você retornará para o **Recovery Menu**.

![](../assets/img/page-senha/GRUB-RESUME.png)

Desta forma, escolha a opção **Resume** e dê um **OK**.

*WELL DONE*

Agora, você já poderá entrar no Ubuntu com a nova senha.

<br>

<!--
## Simulação
Como o projeto está em desenvolvimento, simulações parciais estão sendo testadas (referência).

<br>

## Live Action
Testes preliminares também estão sendo realizados em laboratório, onde alguns resultados foram alcançados.

<br>
-->

<hr>

<!-- autor -->
<center><h3 class="post-title">Autor</h3><br/></center>
<div class="row">
  <div class="col-xl-8 offset-xl-0 col-lg-4 offset-lg-0 center">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="amarco" class="img-fluid rounded-circle" /></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td>Marco Reis</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top; text-align: justify"><small>Pesquisador Sênior no Centro de Competêhncias em Robótica e Sistemas Autônomos do Senai Cimatec. Apaixonado por robótica e um idealista puro, vive motivando aqueles que caminham em direção ao sucesso. Atualmente segue o interesse do seu coração realizando pesquisa na área de robótica, coordena projetos no Senai Cimatec e lidera o grupo do Centro de Competências em Robótica e Sistemas Autônomos. Marco é formado em engenharia elétrica pela UFPR e mestrado em engenharia de produção pela UFSC. Aguarda anciosamente o novo SuperMetroid e Winds of Winter.</small></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>
