---
layout: post-page
title: Arquiteturas de gerenciamento para robôs autônomos
subtitle: Comparação entre FSM, HSFM e Behavior Trees
cover-img: /assets/img/bbot/bbot_cover.png
thumbnail-img: /assets/img/bbot_wide.png
share-img: /assets/img/rosa-logo-redondo.png
comments: true
css: [/assets/css/tango.css]
---

<!-- ## Introdução -->

Na robótica, um desafio muito importante é conseguir alternar diferentes tarefas realizadas por um agente autônomo, uma vez que criar e manter um sistema complexo pode apresentar diversas complicações. Daí vem a necessidade dos robôs autônomos serem reativos e modulares. 

**Reativos**, pois precisam de forma rápida e eficiente a mudanças no ambiente nos quais estão inseridos, e **modulares**, para que seus componentes ou funcionalidades sejam descritos em blocos de funções ou comportamentos, e que estes possam ser desenvolvidos, testados e reutilizados de forma independente. 

Neste artigo, iremos apresentar algumas formas de produzir uma arquitetura de gerenciamento para um robô autônomo, utilizando HFSM (Máquinas de Estados Hierárquicos Finitos, do inglês *Hierarchical Finite State Machine*) e *Behavior Trees*. Também será utilizada como base a FSM (Máquinas de Estados Finitos, do inglês *Finite State Machine*), para efeito comparativo e para ressaltar os prós e contras do uso de cada uma.


## 1. Máquinas de Estados Finitos (FSM)

Uma FSM é um modelo matemático básico de computação, comumente utilizado em programas de computador. A FSM é composta por **estados**, **transições** e **eventos**, e pode ser definida como uma máquina abstrata que só pode estar presente em um dos vários estados predefinidos por vez, entre os quais as transições são executadas para mudar o estado atual. 

Uma vez presente em um estado, a FSM executa uma determinada ação para em seguida realizar a transição para um outro estado. As FSMs são uma maneira comum de resolver problemas de controle de alto nível em robótica, mas a sua utilização traz uma série de desafios e desvantagens na sua implementação e manutenção. Num sistema que utiliza FSM, a representação de ambientes complexos e dinâmicos torna as FSMs incontroláveis.

Neste caso, é necessário pensar no *tradeoff* entre reatividade do sistema e modularidade. Para que o sistema seja reativo, cada estado precisa estar conectado no outro, o que prejudica a modularidade do sistema. Quando um estado é removido, cada transição para este componente precisa ser revisada, e o sistema torna-se propenso a aparição de bugs. A falta de modularidade é um dos principais problemas da utilização da FSM em sistemas robóticos.


<p align="center">
    <img src="{{ 'assets/img/page-gerenciadores/fsm.png' | relative_url }}" alt="FSM" width="600"/>
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

* Capacidade de manutenção: adicionar ou remover estados ainda e difícil;
* Hierarquia criada manualmente: embora os HFSMs tenham sido concebidos como uma versão hierárquica dos FSMs, a hierarquia deve ser definida pelo usuário e modificá-la pode ser uma tarefa desafiadora.

Todo sistema representado por uma *Behavior Tree* teoricamente pode ser representado por uma HFSM, pois HFSM é a arquitetura de controle mais semelhante à *Behavior Tree* em termos de propósito e utilização.

## 3. Behavior Trees

As *Behavior Trees* são formuladas como grafos direcionados com uma estrutura de árvore. A sua estrutura é mostrada na figura abaixo. O nó superior, denotado como o nó **raiz**, tem um ou mais nós filhos, que por sua vez também podem ter filhos. Os nós que têm filhos são chamados de nós de **controle de fluxo**. Um nó filho sem filhos próprios é denominado **folha** ou **nó de execução**, e o nó raiz é o único sem pai.

<p align="center">
    <img src="{{ 'assets/img/page-gerenciadores/BT.png' | relative_url }}" alt="HFSM" width="300"/>
</p>

A *Behavior Tree* inicia sua execução a partir do nó raiz, que gera sinais que permitem
a execução de um nó com uma determinada frequência, conhecidos como **ticks**, que são
enviados para seus filhos. Um nó é executado se e somente se receber ticks. O nó filho
retorna imediatamente Running para o pai, se sua execução está em andamento, Success
se atingiu seu objetivo, ou Fail se falhou.

Cada nó na Behavior Tree pertence a um dos seis tipos de nós mostrados na tabela abaixo.
Para nós não-folha, eles podem ser qualquer um dos quatro tipos, Seletor, Sequência,
Decorador ou Paralelo. Os nós folha vêm na forma de ação ou condição.

<!-- __________________________________________tabela__________________________________________ -->

| **Tipo** 	| **Success** 	| **Fail** 	| **Running** 	|
|---	|---	|---	|---	|
| Selector 	| Se um nó filho  <br>  retorna sucesso 	| Se todos os nós  <br>  filhos falham 	| Se um nó filho  <br>  está rodando 	|
| Sequence 	| Se todos os nós filhos  <br>  retornam sucesso 	| Se um nó  <br>  filho falha 	| Se um nó filho  <br>  está rodando 	|
| Decorator 	| Varia 	| Varia 	| Varia 	|
| Parallel 	| Se N nós filhos  <br>  retornam sucesso 	| Se M-N nós  <br>  filhos falham 	| Se todos os nós filhos  <br>  estão rodando 	|
| Action 	| Após concluído 	| Quando é  <br>  impossível  <br>  completar 	| No decorrer da <br>  conclusão 	|
| Condition 	| Se verdadeiro 	| Se falso 	| Nunca 	|
<!-- __________________________________________tabela__________________________________________ -->



## Conclusão

Estes foram os passos que seguimos para simular matematicamente o Bbot. Utilizamos várias ferramentas do python para isso, porém há muito mais. Caso queiram saber mais sobre os pacotes, basta acessar a documentação online no link deixado no início. E caso queiram saber mais sobre o projeto do Bbot, pode acessar nossa [página oficial](https://mhar-vell.github.io/rasc/project-bbot/).

## Referências

1. <a id="Kollarcik">**Adam Kollarčík**</a>; Modeling and Control of Two-Legged Wheeled Robot; Master’s thesis, CZECH TECHNICAL UNIVERSITY IN PRAGUE. 2021.
2. <a id="Kim">**Kim, Sangtae; Kwon, Sang Joo**</a>; "Dynamic modeling of a two-wheeled inverted pendulum balancing mobile robot", p. 926-933 . In: **International Journal of Control, Automation and Systems**. 2015.

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
