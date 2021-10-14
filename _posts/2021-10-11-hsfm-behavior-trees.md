---
layout: post-page
title: Arquiteturas de gerenciamento para robôs autônomos
subtitle: Comparação entre FSM, HSFM e Behavior Trees
cover-img: /assets/img/page-gerenciadores/ai.jpg
thumbnail-img: /assets/img/page-gerenciadores/ai.jpg
share-img: /assets/img/rosa-logo-redondo.png
comments: true
css: [/assets/css/tango.css]
---

<!-- ## Introdução -->

Na robótica, um desafio muito importante é conseguir alternar diferentes tarefas realizadas por um agente autônomo, uma vez que criar e manter um sistema complexo pode apresentar diversas complicações. Daí vem a necessidade dos robôs autônomos serem reativos e modulares. 

**Reativos**, pois precisam reagir de forma rápida e eficiente a mudanças no ambiente nos quais estão inseridos; **modulares**, para que seus componentes ou funcionalidades sejam descritos em blocos de funções ou comportamentos, e que estes possam ser desenvolvidos, testados e reutilizados de forma independente. 

Neste artigo, iremos apresentar algumas formas de produzir uma arquitetura de gerenciamento para um robô autônomo, utilizando HFSM (Máquinas de Estados Hierárquicos Finitos, do inglês *Hierarchical Finite State Machine*) e *Behavior Trees*. Também será utilizada como base a FSM (Máquinas de Estados Finitos, do inglês *Finite State Machine*), para efeito comparativo e para ressaltar os prós e contras do uso de cada uma.


## 1. Máquinas de Estados Finitos (FSM)

Uma FSM é um modelo matemático básico de computação, comumente utilizado em programas de computador. A FSM é composta por **estados**, **transições** e **eventos**, e pode ser definida como uma máquina abstrata que só pode estar presente em um dos vários estados predefinidos por vez, entre os quais as transições são executadas para mudar o estado atual. 

Uma vez presente em um estado, a FSM executa uma determinada ação para em seguida realizar a transição para um outro estado. As FSMs são uma maneira comum de resolver problemas de controle de alto nível em robótica, mas a sua utilização traz uma série de desafios e desvantagens na sua implementação e manutenção. Num sistema que utiliza FSM, a representação de ambientes complexos e dinâmicos torna as FSMs incontroláveis.

Neste caso, é necessário pensar no *tradeoff* entre reatividade do sistema e modularidade. Para que o sistema seja reativo, cada estado precisa estar conectado no outro, o que prejudica a modularidade do sistema. Quando um estado é removido, cada transição para este componente precisa ser revisada, e o sistema torna-se propenso a aparição de bugs. A falta de modularidade é um dos principais problemas da utilização da FSM em sistemas robóticos.


<p align="center">
    <img src="{{ 'assets/img/page-gerenciadores/fsm.png' | relative_url }}" alt="FSM" width="1000"/>
</p>

Um exemplo da aplicação de uma FSM na robótica é mostrada na imagem acima, retratando uma tarefa de *pick & place* com um objeto. Onde os **estados** estão representados por retângulos, e o retângulo em negrito é o estado inicial, **transições** são as setas e os **eventos** são os nomes situados acima de cada transição.

Conforme o observado, as FSMs possuem algumas vantagens e desvantagens. As principais vantagens das FSMs são:

* Estrutura muito comum de ser encontrada;
* Intuitiva e fácil de entender;
* Fácil de implementar.

As desvantagens das FSMs são listadas a seguir:

* Manutenibilidade: Adicionar ou remover estados requer a analise de um número potencialmente grande de transições e estados internos, tornando as FSMs altamente suscetíveis a erros de projeto e impraticáveis de uma perspectiva de projeto automatizado;
* Escalabilidade: FSMs com muitos estados e muitas transições entre eles são difíceis de modificar;
* Reutilização: As transições entre estados podem depender de variáveis internas, tornando impraticável a reutilização de um estado em outros projetos.

## 2. Máquina de Estados Finitos Hierárquica (HFSM)

As HFSMs foram desenvolvidas para lidar com algumas deficiências presentes nas FSMs, tentando lidar com a duplicação de transições necessárias em FSMs complexas, bem como adicionar uma estrutura para facilitar a compreensão de sistemas complexos. A grande mudança das HFSMs para as HFSMs é a capacidade de conter **subestados** e **superestados**. Um estado pode conter um ou mais subestados, sendo chamado de **superestado**, onde todos os seus subestados compartilham implicitamente o mesmo superestado.

Nas HFSMs, uma transição generalizada é uma transição entre superestados, e podem reduzir o número de transições internas, pois conectam dois superestados ao invés de vários subestados individualmente. Nesta estrutura, cada superestado tem um subestado inicial, que é executado primeiro quando ocorre a transição para aquele superestado.

<p align="center">
    <img src="{{ 'assets/img/page-gerenciadores/hsfm.png' | relative_url }}" alt="HFSM" width="600"/>
</p>

As vantagens da utilização de HFSMs são listadas a seguir:

* Aumento da Modularidade: é possível separar as tarefas em subtarefas. No entanto, essas subtarefas frequentemente ainda dependem umas das outras por meio de transições dependentes de estado;
* Herança de comportamento: A herança de comportamento permite que os subestados herdem comportamentos do superestado.

Apesar de se comportar de forma mais modular que as FSMs, as HFSMs herdam a maioria das desvantagens:

* Capacidade de manutenção: adicionar ou remover estados ainda é difícil;
* Hierarquia criada manualmente: embora os HFSMs tenham sido concebidos como uma versão hierárquica dos FSMs, a hierarquia deve ser definida pelo usuário e modificá-la pode ser uma tarefa desafiadora.

## 3. Behavior Trees

As *Behavior Trees* são formuladas como grafos direcionados com uma estrutura de árvore. A sua estrutura é mostrada na figura abaixo. O nó superior, denotado como o nó **raiz**, tem um ou mais nós filhos, que por sua vez também podem ter filhos. Os nós que têm filhos são chamados de nós de **controle de fluxo**. Um nó filho sem filhos próprios é denominado **folha** ou **nó de execução**, e o nó raiz é o único sem pai.

<p align="center">
    <img src="{{ 'assets/img/page-gerenciadores/BT.png' | relative_url }}" alt="HFSM" width="300"/>
</p>

A *Behavior Tree* inicia sua execução a partir do nó raiz, que gera sinais que permitem
a execução de um nó com uma determinada frequência, conhecidos como **ticks**, que são
enviados para seus filhos. Um nó é executado se e somente se receber ticks. O nó filho
retorna imediatamente **Running** para o pai, se sua execução está em andamento, **Success**
se atingiu seu objetivo, ou **Fail** se falhou.

Cada nó na Behavior Tree pertence a um dos seis tipos de nós mostrados na tabela abaixo.
Para nós não-folha, eles podem ser qualquer um dos quatro tipos, **Seletor**, **Sequência**,
**Decorador** ou **Paralelo**. Os nós folha vêm na forma de ação ou condição.

<!-- __________________________________________tabela__________________________________________ -->



<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-3je9{background-color:#464646;border-color:#ffffff;color:#FFF;text-align:center;vertical-align:middle}
.tg .tg-7ogr{background-color:#464646;border-color:#ffffff;color:#ffffff;text-align:center;vertical-align:top}
.tg .tg-dbpp{background-color:#464646;border-color:#ffffff;color:#ffffff;text-align:left;vertical-align:top}
</style>

<table class="tg">
<thead>
  <tr>
    <th class="tg-7ogr"><span style="font-weight:bold">Tipo</span><br></th>
    <th class="tg-7ogr"><span style="font-weight:bold">Success</span></th>
    <th class="tg-7ogr"><span style="font-weight:bold">Fail</span></th>
    <th class="tg-7ogr"><span style="font-weight:bold">Running</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-3je9">Selector</td>
    <td class="tg-3je9">Se um nó filho retorna sucesso</td>
    <td class="tg-3je9">Se todos os nós filhos falham</td>
    <td class="tg-3je9">Se um nó filho está rodando</td>
  </tr>
  <tr>
    <td class="tg-3je9">Sequence</td>
    <td class="tg-3je9">Se todos os nós filhos retornam sucesso</td>
    <td class="tg-3je9">Se um nó filho falha</td>
    <td class="tg-3je9">Se um nó filho está rodando</td>
  </tr>
  <tr>
    <td class="tg-3je9">Decorator</td>
    <td class="tg-3je9">Varia</td>
    <td class="tg-3je9">Varia</td>
    <td class="tg-3je9">Varia</td>
  </tr>
  <tr>
    <td class="tg-3je9">Parallel</td>
    <td class="tg-3je9">Se N nós filhos retornam sucesso</td>
    <td class="tg-3je9">Se M-N nós filhos falham</td>
    <td class="tg-3je9">Se todos os nós filhos estão rodando</td>
  </tr> 
  <tr>
    <td class="tg-3je9">Action</td>
    <td class="tg-3je9">Após concluído</td>
    <td class="tg-3je9">Quando é impossível completar</td>
    <td class="tg-3je9">No decorrer da conclusão</td>
  </tr> 
  <tr>
    <td class="tg-3je9">Condition</td>
    <td class="tg-3je9">Se verdadeiro</td>
    <td class="tg-3je9">Se falso</td>
    <td class="tg-3je9">Nunca</td>
  </tr> 
</tbody>
</table>
<!-- __________________________________________tabela__________________________________________ -->


A *Behavior Tree* utilizada como exemplo é mostrada na figura abaixo, e é responsável por fazer um robô procurar uma bola, se aproximar, pegar a bola, se aproximar de uma caixa e colocar a bola na caixa.

<p align="center">
    <img src="{{ 'assets/img/page-gerenciadores/BT_structure.png' | relative_url }}" alt="FSM" width="800"/>
</p>

Quando a *Behavior Tree* é executada, os *ticks* percorrem a *Behavior Tree* atingindo o nó condição `Achou a bola`. Como o robô não sabe a posição da bola,  o nó condição  retorna *Failure* e os ticks alcançam a ação `Achar bola`, que retorna *Running*. Ao executar esta ação, o robô vê a bola com a câmera. Agora o robô sabe a posição da bola. Então, o nó de condição `Achou a bola` agora retorna *Success*, não percorrendo mais o nó de ação `Achar bola` e interrompendo-a.

Os *ticks* continuam explorando a árvore, e ao atingir o nó de condição `Perto da bola`, este  retorna *Failure* (pois a bola está longe). Logo em seguida, alcança o nó de ação `Aproximar-se da bola`, que retorna *Running*. Então, o robô alcança a bola, pega-a e vai em direção à caixa.

Se alguém tirar a bola da mão do robô e jogar no chão (em um local visível), o nó de condição `Achou a bola` retorna *Success* enquanto o nó de condição `Perto da bola` retorna *Failure*. Nesta situação, o *tick* não passa para `Aproximar-se da caixa` (que sofre *preemption*) e, em vez disso, passa para `Aproximar-se da bola`.

Conforme anteriormente já citado, as *Behavior Trees* possuem algumas vantagens. Podendo ser listadas:


* Modularidade: são modulares, uma vez que cada subárvore de uma *Behavior Tree* pode ser vista como um módulo;

* Organização hierárquica: contém vários níveis de tomada de decisão, logo pode ser considerada hierárquica;

* Código reutilizável: permitem o reutilização de código, uma vez que, dada a implementação adequada, qualquer subárvore pode ser reutilizada em vários locais de uma *Behavior Tree*; 

* Reatividade: são reativas, uma vez que a geração contínua de *ticks* e sua passagem na árvore
resultam em uma execução de loop fechado. As ações são executadas e abortadas de acordo com a travessia dos *ticks*, que dependem dos status de retorno dos nós folha. Assim, os BTs são altamente responsivos às mudanças no ambiente;

* Legível por humanos: são legíveis por humanos devido à sua estrutura em árvore e modularidade;

* Expressividade: uma arquitetura de gertenciamento deve ser suficientemente expressiva para codificar uma grande variedade de comportamentos;

* Adequado para análise: aplicações de robôs essenciais para a segurança muitas vezes requerem uma análise de propriedades qualitativas e quantitativas do sistema e *Behavior Trees* possuem estas ferramentas;

* Adequado para síntese automática: são adequadas para síntese automática em termos de planejamento e aprendizado.

As desvantagens da utilização de *Behavior Trees* são listadas a seguir:

* Complexidade de implementação: Para garantir a funcionalidade total, a geração e travessia do *tick* deve ser executada em paralelo com a execução da ação;

* Custo computacional: precisa verificar várias condições para implementar a execução da tarefa de loop fechado, e a depender da aplicação pode ter um custo alto; 

* Ferramentas de desenvolvimento: embora existam softwares para desenvolvimento, ainda é muito aquém da quantidade e maturidade dos softwares disponível para, por exemplo, FSMs.

## Conclusão

Todo sistema representado por uma *Behavior Tree* teoricamente pode ser representado por uma HFSM, pois HFSM é a arquitetura de controle mais semelhante à *Behavior Tree* em termos de propósito e utilização. Em aplicações onde o robô opera em um ambiente muito estruturado, previsível no espaço e no tempo, as *Behavior Trees* não tem nenhuma vantagem sobre outras arquiteturas mais simples.

Mas em arquiteturas mais complexas, a modularidade e a reatividade das *Behavior Trees* se destacam, juntamente com a facilidade de visualização dos sistemas,  o que torna uma ferramenta poderosíssima na construção de arquiteturas de gerenciamento de robôs autônomos.


## Referências

1. <a id="COLLEDANCHISE">**COLLEDANCHISE, Michele; ÖGREN, Petter**</a>. Behavior trees in robotics and AI: An introduction. CRC Press, 2018.

<br>

<hr>

<!-- autor -->
<center><h3 class="post-title">Autor</h3><br/></center>
<div class="row">
  <div class="col-xl-8 offset-xl-0 col-lg-4 offset-lg-0 center">
    <table class="table-borderless highlight" style="background: #00000000">
      <thead>
        <tr>
          <th><img src="{{ 'assets/img/people/israelneto-1.png' | relative_url }}" width="100" alt="amarco" class="img-fluid rounded-circle" /></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td>Israel Motta</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top; text-align: justify"><small>Pesquisador bolsista no CC RoSA, Engenheiro Mecatrônico, Especialista em Robótica e Sistemas Autonônomos.</small></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>
