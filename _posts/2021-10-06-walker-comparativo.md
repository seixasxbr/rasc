---
layout: post
title: Robôs antropomórficos - Introdução ao estudo do estado da arte
subtitle:  Princípais características e comparativo entre modelos by Brenda Alencar
thumbnail-img: assets/img/walker/walker_kinematics_thumb.png
cover-img: assets/img/walker/walker_kinematics_cover.jpg
share-img: /assets/img/rosa-logo-redondo.png
tags: [walker]
---


Robô antropomórfico é o robô que possui uma estrutura parecida com os humanos, com cabeça, tronco, mãos, pernas e pés, sendo assim ele possui habilidades que se assemelham muito com o comportamento humano, que vão além de caminhar para sentar, correr ou até mesmo pular sobre dois pés. Além disso, é esperado que humanóides desempenhem tarefas no futuro que facilitem a vida humana, como cuidar de pessoas de risco.

<center><img src="{{ 'assets/img/walker/boston-dynamics-saltando-degraus.gif' | relative_url }}" alt="Robô Atltas (Boston Dynamics) saltando caixas." width="500"/>
</center>

A estrutura física de humanóides é complexa, pois por possuírem braços e pernas articulados há uma grande quantidade de graus de liberdade, *Degrees of liberty*. DOF diz respeito ao conjunto de deslocamentos e rotações que um corpo pode realizar, ou seja, uma rotação sobre um eixo caracteriza um grau de liberdade,  por exemplo o movimento de subir e descer a palma da mão demonstrado no GIF abaixo. Os atuais robôs apresentam em média 7 graus de liberdade em cada perna e 3 em cada braço, além de 2 na cabeça e 1 no tronco. Ainda sobre a estrutura, a depender do porte do humanóide, a altura pode ir de 50 cm, pequeno porte, até 150 cm, para os de grande porte, e o peso pode variar entre 3 e 80 quilos.

<center><img src="{{ 'assets/img/walker/dof-hand.gif' | relative_url }}" alt="1 DOF na mão" width="300"/>
</center>

Para realizar o movimento das juntas, os robôs são equipados com atuadores, os mais comuns são servomotores e motores *brushless*, ambos DC, mas há exceções como o Atlas, do GIF acima, que é equipado com motores hidraulicos junto a servo válvulas.

Para realizar movimentos elaborados ou andar por terrenos irregulares, é necessário que ele possua um controle robusto. Este processo envolve o planejamento dos passos, para definir a posição e direção dos pés, a geração da trajetória do movimento, definindo as posições de todas as juntas das pernas durante os movimentos, e um controle de estabilidade, para evitar que o robô caia. Para tanto, surgiram diversas abordagens para modelar e estabilizar esses robôs, como os modelos de pêndulo invertido e pêndulo linear invertido. Neste contexto, ainda são envolvidos conceitos de Centro de massa (COM), ponto de momento zero (ZMP) para estabilização do robô e filtros para corrigir erros do processo, como o de Kalman.

Abaixo será apresentado uma tabela para fins comparativos entre os modelos de robôs antropomórficos disponíveis no mercado, que apresentam alto desempenho.


tabela comparativa robos bipedes
