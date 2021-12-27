---
layout: post-page
title: O tempo livre de final de ano
subtitle: buscando sentido para um novo ano
cover-img: /assets/img/wesley-pribadi-iS1NV9yN0Lg-unsplash.jpg
thumbnail-img: /assets/img/ubuntu.png
share-img: /assets/img/rosa-logo-redondo.png
author: Marco Reis
comments: true
tags: [blog]
---

<!-- ## Introdução -->

Um tempo livre sempre é esperado, somos imbuídos em esperar pelo final de semana intensamente.
Esperamos em preenchê-lo com afazeres que criamos em nossos deleites substanciais e superficiais.
A efemeridade fala mais alto, e o passageiro é algo momentâneo. E o aproveitar se torna primordial para uma vida existencialista do agora.

Nos últimos 5 dias a gripe me levou a permanecer enfraquecido em cima de uma cama, entre uma febre e outra fui levado a refletir sobre como eu estava preenchendo meus dias de tempo livre. 
Encontrei inquietações que me fizeram a pensar sobre este tempo, que estava fluindo entre os meus dedos sem ao menor erigir uma torre de observação sobre o meu futuro.

Somos insignificantes diante do universo, mas bucólicos para nossa família. Importantes para os que ficam aqui na Terra.
O enredo da vida nos levará, ao final do primeiro ato, a um encontro com Tânato. 

Mas ainda não é o fim.

A transcendência da alma é eterna, e anseia pela busca espiritual do **Caminho**. 

Neste ano, nosso grupo ousou saltar no vazio, em buscar reflexão mais humanizadas. Passamos por discussões e leituras (A Sociedade da Transparência, Identidade e O Jeito Harvard de Ser Feliz) que mexeram com nossos ideais, nossas bases dicotômicas, nossas visões de mundo. Eu espero que o ano de 2022 seja de mais preces abnegadas de prazer, pois a sociedade esta inundada na efemeridade do ter, e somos agentes da mudança.

Mudança de um mundo melhor. Este é o meu desejo. Que isso torne-se um feitiço, que entre em seu corpo e transforme de dentro para fora. Perceba que somos as palavras que os outros plantaram em nós. E isso é bem parecido com a fala do grande poeta português Fernando Pessoa: *Sou o intervalo entre o meu desejo e aquilo que os desejos dos outros fizeram de mim.*

Somos resultado de um enorme feitiço.

E se você me acompanhou até aqui, eu espero que o seu tempo seja ainda mais reflexivo sobre a mudança. A mudança da sociedade. A mudança da família. A minha e a tua mudança, comecemos nós pois muitos já alcançaram o *Nirvana*.

Pensando sobre tudo isso, acabei encontrando um video curto de 15 minutos, que coincidentemente (Jung diria que é sincronicidade) trazia aspectos sobre o que eu estava pensando. Veja e reflita.

Um feliz 2022 de muita prece...



<br>

<!-- detalhamento -->

## 1. Acesso ao *root* da máquina
Inicie a sua máquina e pressione o botão **ESC** até que a tela do GRUB apareça.

Algo similar a isto...

[![](../assets/img/page-senha/GRUB-1.png)](../assets/img/page-senha/GRUB-1.png)

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
  <div class="col-xl-auto offset-xl-0 col-lg-4 offset-lg-0 center">
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
          <td style="color: #808080; vertical-align: top; text-align: justify"><small>Pesquisador em Robótica no Centro de Competências em Robótica e Sistemas Autônomos do Senai Cimatec. Apaixonado por robótica e um idealista puro, vive motivando aqueles que caminham em direção ao sucesso. Atualmente segue o interesse do seu coração realizando pesquisa na área de robótica, coordenando projetos acadêmicos e escrevendo ficção. Marco é formado em engenharia elétrica pela UFPR e mestrado em engenharia de produção pela UFSC. E aguarda anciosamente o Winds of Winter.</small></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>
<br>
