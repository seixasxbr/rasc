---
layout: post
title: Planejamento de trajetória 
subtitle:  Modelagem com Pêndulo invertido by Brenda Alencar
thumbnail-img: assets/img/walker/naos.jpg
cover-img: assets/img/walker/humanoides.jpg
share-img: /assets/img/rosa-logo-redondo.png
tags: [walker]
---

Nesta fase do projeto foi desenvolvido um modelo que representasse o robô no espaço, utilizando o conceito de pêndulo, a fim de obter XXXX. Um pêndulo é um sistema composto por um fio inextensível, preso a um suporte, cuja extremidade contém um corpo de formato redondo que concentra a massa de um corpo . Nessa aplicação, iremos considerar que o pêndulo está invertido e que toda a massa do robô está localizada na esfera, a qual será equilibrada durante o planejamento dos passos. Dessa forma, estamos analisando o movimento do centro de massa do robô e a posição dos pés durante uma marcha simétrica para frente, em que os passos possuem a mesma distância e alterna-se os pés de apoio.

Primeiramente, foram encontradas as condições iniciais de posição e velocidade,  para uma dada posição em x, um dado comprimento de passo e considerando que o pêndulo irá oscilar na altura do centro de massa do robô. EXPLICR MAIS COMO ENCONTRA. Nesta simulação as velocidades iniciais foram de xxxxx

O primeiro movimento será o de aplicar ao corpo do robô as condições iniciais, isto é, abaixar o corpo até a altura determinada, o que seria similar a dobrar os joelhos do robô,  e mover o pé esquerdo com a metade de um passo. Esta movimentação serve para inicializar corretamente o robô, retirando-o da posição de duplo suporte....

<center><img src="{{ 'assets/img/walker/halfstep.gif' | relative_url }}" alt="Movimento dos pés." width="500"/>
</center>

Em seguida o pêndulo irá saltar seguindo as pegadas planejadas, de forma que a base da haste represente o pé de apoio do robô.  Enquanto isso, o pé de alavanca movimenta-se para frente movendo o centro de massa para que o pêndulo permaneça estável, seguindo a condição de Zero momento de inércia. 

<center><img src="{{ 'assets/img/walker/lipmtraj.gif' | relative_url }}" alt="Planejamento do movimento dos pés." width="500"/>
</center>


Além do planejamento de passos, estamos também em busca da trajetória dos pés durante os passos do robô, ou seja, a posição dos pés no espaço ao realizar o movimento. Para isso, usaremos outra representação, um modelo com dois pêndulos não invertidos, com um mesmo ponto de apoio fixo, de modo que agora as esferas sem massas representem os pés. Nesta fase, estamos planejando também trajetórias polinomiais, pois estas curvas representam a flexão e extensão das juntas do robô ao caminhar.

<center><img src="{{ 'assets/img/walker/feettraj.gif' | relative_url }}" alt="Planejamento do movimento dos pés." width="500"/>
</center>


<br>

---------------------
<br>

<!-- autor -->
<center><h3 class="post-title">Autora</h3><br/></center>
<div class="row">
  <div class="col-xl-auto offset-xl-0 col-lg-4 offset-lg-0 center">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><img src="{{ 'assets/img/people/brendaalencar-1.png' | relative_url }}" width="100" alt="felipemohr" class="img-fluid rounded-circle" /></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td>Brenda Alencar</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Estagiária no CC RoSA, graduanda em Eng. Elétrica. Participou de projetos de Robótica Subaquática e Manipuladores Subaquáticos</small></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>
