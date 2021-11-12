---
layout: post
title: Planejamento de trajetória 
subtitle:  Modelagem com Pêndulo invertido by Brenda Alencar
thumbnail-img: assets/img/walker/naos.jpg
cover-img: assets/img/walker/Phases-of-biped-locomotion.png
share-img: /assets/img/rosa-logo-redondo.png
tags: [walker]
---

Nesta fase do projeto foi desenvolvido um modelo que representasse o robô no espaço, utilizando o conceito de pêndulo. Um pêndulo é um sistema composto por um fio inextensível, preso a um suporte, cuja extremidade contém um corpo de formato redondo que concentra a massa de um corpo . Nessa aplicação, consideramos que o pêndulo está invertido e que toda a massa do robô está localizada na esfera, que é equilibrada durante o planejamento dos passos. Dessa forma, estamos analisando o movimento do centro de massa do robô e a posição dos pés durante uma marcha simétrica para frente, em que os passos possuem a mesma distância e alterna-se os pés de apoio.

O primeiro movimento consiste em aplicar ao corpo do robô as condições iniciais, isto é, abaixar o corpo até a altura determinada na qual ele deve oscilar, o que seria similar a dobrar os joelhos do robô,  e mover o pé esquerdo com a metade de um passo. Esta movimentação serve para inicializar corretamente o robô, retirando-o da posição de duplo suporte e aplicando as condições iniciais de posição e velocidade, as quais são determinadas utilizando equações da energia orbital de um corpo.

<center><img src="{{ 'assets/img/walker/halfstep.gif' | relative_url }}" alt="Movimento dos pés." width="500"/>
</center>

Em seguida o pêndulo salta seguindo as pegadas planejadas, de forma que a base da haste represente o pé de apoio do robô.  Enquanto isso, o pé de alavanca movimenta-se para frente e, para que o robô permaneça estável, move-se também o centro de massa, que obedece a trajetória 3D de um pêndulo linear, sem torques iniciais, escrita por Kajita et Al em [The 3D Linear Inverted Pendulum Mode A simple modeling for a biped walking pattern generation](https://www.cs.cmu.edu/~hgeyer/Teaching/R16-899B/Papers/KajiitaEA01IEEE_ICIRS.pdf).

<center><img src="{{ 'assets/img/walker/lipmtraj.gif' | relative_url }}" alt="Planejamento do movimento dos pés." width="500"/>
</center>

Além do planejamento de passos, estamos também em busca da trajetória dos pés durante os passos do robô, ou seja, a posição dos pés no espaço ao realizar o movimento. Para isso, utilizamos outra representação, um modelo com dois pêndulos não invertidos, com um mesmo ponto de apoio fixo, de modo que agora as esferas sem massas representem os pés. Nesta fase, estamos planejando trajetórias polinomiais entre as pegadas definidas anteriormente, pois estas curvas representam a flexão e extensão das juntas do robô ao caminhar.

<center><img src="{{ 'assets/img/walker/feettraj.gif' | relative_url }}" alt="Planejamento do movimento dos pés." width="500"/>
</center>

Com isso, obtivemos o planejamento dos passos, em termos de posição das pegadas e trajetória dos pés, para uma caminhada simples, movendo o robô em uma única direção, considerando os passos simétricos e sem perturbações do meio. Essa implementação foi realizada em python, com auxílio da biblioteca *Robotics Toolbox*. Em seguida, obteremos as coordenadas das juntas das pernas durante toda esta movimentação, utilizando algoritmos de cinemática inversa.

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
