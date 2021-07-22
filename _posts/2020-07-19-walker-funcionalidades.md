---
layout: post
title: Walker - Funcionalidades
subtitle: O que o robô será capaz de fazer?
cover-img: /assets/img/path.jpg
thumbnail-img: assets/img/walker/walker_funcionalidades.png
share-img: assets/img/walker/walker_funcionalidades.png
tags: [walker, funcionalidades]
---

No processo de ideação de um projeto, surge a necessidade de analisar e reunir as funcionalidades que o produto deve conter para realizar a tarefa proposta a ele. Ou seja, neste momento é pensado um grupo de pequenas ações que o protótipo deve realizar em prol de uma ação final. Por exemplo para uma microondas esquentar um dado alimento, de forma simplificada, este equipamento deve possuir as seguintes funcionalidades: interface, para interagir com o usuário, geracionamento, que analisa a escolha do usuário e envia as informações de operação, e atuação, para acionar o giro do prato e o sistema de aquecimento.

Durante a etapa de detalhamento e *Design* do robô Walker, foram especificadas as Funcionalidades a serem desenvolvidas no projeto, assim como as relações entre elas. 
Isso é importante para entender o funcionamento do robô, o que ele é capaz de fazer, e como cada subsistema depende dos outros.

A imagem a seguir traz o **Diagrama de Funcionalidades** construído para o robô. Primeiramente, o robô possui o Subsistema de Energia, responsável pela alimentação de todo o sistema. O subsistema de Gestão de Dados está ali para administrar o recebimento e envio de informações entre todos os subsistemas/funcionalidades. E, claro, a Segurança é importante para garantir o seu bom funcionamento. 

<center><img src="{{ 'assets/img/walker/walker_funcionalidades.png' | relative_url }}" alt="Walker_funcionalidades" width="800"/></center>
<p/>

As funcionalidades são as seguintes:

- **Percepção:** É a funcionalidade responsável por receber os dados vindos dos sensores Ultrassônicos, IMU e Câmeras, tornando o robô capaz de perceber o ambiente a sua volta e enviando informações importantes para o funcionamento de outras funcionalidades;

- **Localização:** Através dos dados recebidos pela Percepção, o robô será capaz de se localizar no ambiente, através de sua posição e orientação;

- **Mapeamento:** Utilizando as informações da Localização, é possível criar um Mapa global do ambiente, atualizando assim a Localização do robô;

- **Planejamento:** Dada uma missão para o robô, escolhida através da Interface, o Planejamento é responsável por definir a estratégia e a trajetória que o Walker deverá seguir para cumprir seus objetivos;

- **Interface:** Essa funcionalidade torna possível ao usuário definir a missão do robô, bem como se ele deverá operar de forma autônoma ou teleoperada;

- **Comportamento:** Avalia alguns parâmetros do robô, como a carga na bateria, corrente nos motores e presença de obstáculos, enviando essas informações para a Navegação;

- **Navegação:** Na Navegação, são recebidas informações de diversas Funcionalidades, que juntas irão permitir que o Walker gere seus movimentos, enviando-os à Atuação para permitir o deslocamento seu deslocamento;

- **Atuação:** A Atuação é a funcionalidade responsável por receber os comandos para acionamento dos motores, possibilitando o deslocamento do robô. É nela também que ocorre a odometria dos motores e a leitura de corrente em cada um deles, sendo essas informaões úteis para o Comportamento e a Localização.

Nessa fase foi possível sistematizar as funcionalidades que o robô deverá conter e observar as interdependências entre elas, constituindo um só sistema. Além disso, a organização do projeto em subsistemas facilita o planejamento e execução das próximas etapas.

<h3 class="post-title">Autores</h3><br/></center>
<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><center><img src="{{ 'assets/img/people/brendaalencar-1.png' | relative_url }}" width="100" alt="brenda" class="img-fluid rounded-circle" /></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/felipemohr-1.jpg' | relative_url }}" width="100" alt="felipemohr" class="img-fluid rounded-circle"/></center></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="44.33%"><center>Brenda Alencar</center></td>
          <td></td>
          <td width="44.33%"><center>Felipe Mohr</center></td>
          <td></td>
        </tr>
        <tr style="text-align:center" >
          <td width="44.33%" style="vertical-align: top"><small>Estagiária no CC RoSA, graduanda em Eng. Elétrica. Participou de projetos de Robótica Subaquática e Manipuladores Subaquáticos</small></td>
          <td></td>
          <td width="44.33%" style="vertical-align: top"><small>Estagiário no CC RoSA, graduando em Eng. Elétrica. Participou de projetos de Robótica Subaquática e Robótica Móvel</small></td>
        <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

