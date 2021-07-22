---
layout: post
title: Definição do modelo Bbot 
subtitle: Um robô que se equilibra com pernas articuladas
cover-img: assets/img/bbot/bbot_wide.png
thumbnail-img: assets/img/bbot/bbot.png
share-img: assets/img/rosa-logo-redondo (180).png
tags: [bbot]
---

<!-- **************************************** -->
<!-- ### Introdução -->

Motivados pelo desejo de contribuir para a inovação no campo dos robôs auto-balanceados e suas tecnologias, e com o avanço da investigação da robótica internacional, decidimos avançar com a criação de uma nova plataforma com características especiais face a soluções previamente definidas.

Para iniciarmos a <strong>etapa 1</strong> da construção do robô, definimos como prioridade utilizar componentes já disponíveis no laboratório da instituição (<a target="_blank" href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>). Além disso, o <a href="https://mhar-vell.github.io/rasc/project-bbot/"><font color="#fbb117">projeto Bbot</font></a> deverá atender requisitos baseados nas necessidades e expectativas de pesquisa. A adição de servos para manipular membros sobre rodas traz um desafio com uma série de benefícios. Ou seja, ser capaz de ajustar a altura de cada perna para permanecer estável mesmo ao tombar de um lado para o outro e com maior capacidade off-road, bem como até mesmo pular. 


<hr>

<!-- **************************************** -->

### Requisitos 

Para nortear nosso projeto, seguimos alguns requisitos. São estes:

- O robô deve se equilibrar sobre duas rodas;
- O robô deve ser capaz de receber uma posição de destino;
- O robô deve ser capaz de navegar até o destino de forma autônoma;
- O robô deve ser capaz de desviar de obstáculos enquanto navega de forma autônoma até o objetivo.

São necessários, então, condições e critérios para a satisfação dos objetivos estabelecidos. São estas:

- Utilizar um Framework de robótica;
- Deve ser capaz de ler uma TAG;
- Deve mapear o ambiente ao seu redor e se localizar nele;
- Detectar variações de inclinação;
- Pernas articuladas com 2 DOF em sentido pitch (Y);
- Deve ser capaz de controlar a velocidade das rodas.

<!-- **************************************** -->
### Selecionando os componentes 

Aqui está uma lista completa de peças até o momento (sujeito a alterações):

Todas essas peças tem o valor aproximado de $USD 3162,64. 

<!-- **************************************** -->
### Definindo o modelo

Feito a seleção dos componentes e definindo as peças que vamos utilizar, podemos definir a arquitetura geral do Bbot. 


É possível analisar que a arquitetura está dividida em três grandes blocos, que compõem a <strong>interface do usuário</strong>, a <strong>central de gerenciamento do sistema</strong> (Ubuntu 20.04 + ROS Noetic) e a <strong>interface com o hardware</strong>. 


Podemos notar que existem pontos de conexão entre os blocos, são eles: 

- **OpenCM 9.04:** responsável pela aquisição de dados dos sensores e da comunicação com os atuadores
- **Wi-fi:** Disponibiliza o acesso remoto com a Raspberry Pi

<p align="center">
    <img src="{{ 'assets/img/bbot/arquitetura_geral.png' | relative_url }}" alt="Arquitetura geral" width="750"/>
</p>

<!-- **************************************** -->
### Diagrama de componentes

Já com o diagrama de componentes, podemos definir as conexões entre os componentes e obter uma visão geral do projeto.

O diagrama se divide em <strong>base</strong> e <strong>pernas</strong>. Na base do robô, nós temos os controladores, a bateria e os sensores. As pernas ficam com os atuadores. 

É possível notar que as conexões entre os  componentes se dividem em <strong>potência</strong> (vermelho) e <strong>data</strong> (preto). Os atuadores são apresentados apenas com uma “linha” de potência, pois são conectados em cadeia, então optamos por essa descrição no diagrama.

<p align="center">
    <img src="{{ 'assets/img/bbot/components_diagram.png' | relative_url }}" alt="Diagrama de componentes" width="750"/>
</p>

<!-- **************************************** -->
### Conclusão
Nessa primeira etapa do projeto Bbot, foi apresentado a metodologia do projeto e a definição do modelo. Com base nos parâmetros propostos aqui, podemos partir para descrição das funcionalidades do Bbot!! <img src="{{ 'assets/img/bbot/bbot.png' | relative_url }}" alt="Bbot" width="17"/> <img src="{{ 'assets/img/bbot/bbot_stand.png' | relative_url }}" alt="Bbot" width="15"/>


<!-- **************************************** 

###Veja a seguir

#Aqui você encontra os posts relacionados às etapas de projeto do Bbot. <strong>Fique atento!!</strong>


<a href="https://mhar-vell.github.io/rasc/2021-07-22-bbot-funcionalidades-do-bbot/"><font color="#fbb117">[Etapa 2] Funcionalidades do Bbot</font></a>
-->
<!-- <a href="https://mhar-vell.github.io/rasc/2021-07-28-bbot-modelo-3d-do-bbot-etapa-2/"><font color="#fbb117">[Etapa 2] Construindo o Bbot (Modelo 3d)</font></a> -->
 
<!-- <a href="https://mhar-vell.github.io/rasc/2021-08-04-bbot-esquematico-ee-etapa-3/"><font color="#fbb117">[Etapa 3] Esquemático EE</font></a> - disponivel em 04/08/2021 -->

<!-- <a href="https://mhar-vell.github.io/rasc/2021-08-11-bbot-simulacao-etapa-4/"><font color="#fbb117">[Etapa 4] Simulação</font></a> - disponivel em 11/08/2021 -->

<!-- <a href="https://mhar-vell.github.io/rasc/2021-08-18-bbot-montagem-e-teste-etapa-5/"><font color="#fbb117">[Etapa 5] Montagem final e teste</font></a> - disponivel em 18/08/2021 -->

<br>

----------------

<br>

<!-- **************************************** Autor **************************************** -->
<center><h3 class="post-title">Autor</h3><br/></center>

<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
            <th><center><a href="https://www.linkedin.com/in/matheus-fran%C3%A7a-b62044150/" target="_blank">
                <p align="center">
                    <img src="{{ 'assets/img/people/matheusfrança-1.png' | relative_url }}" alt="Not found" width="100" class="img-fluid rounded-circle" />
                </p>
            </a></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center; margin-top: 0">
          <td width="33.33%">Matheus França</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top;text-align: justify;"><small>Estagiário no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia de Controle e Automação na Área 1.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>