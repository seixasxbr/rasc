---
layout: post
title: Walker - Quality Function Deployment 
subtitle: Ferramentas para deteterminar as qualidades do projeto
cover-img: /assets/img/walker/carlos-arthur-m-r-dSINOJrEdfw-unsplash.jpg
thumbnail-img: assets/img/walker/walker_funcionalidades.png
share-img: /assets/img/rosa-logo-redondo.png
tags: [walker]
---

Durante a fase de ideação de um produto é necessário determinar as qualidades do projeto de acordo com as necessidades apresentadas pelo cliente, assim garante-se que o produto final possua as funcionalidades esperadas e opere corretamente. Neste contexto, é interessante utilizar ferramentas que facilitem a tradução da voz do cliente na voz do processo, como por exemplo a ferramenta QFD, *Desdobramento da Função Qualidade* (Quality Function Deployment), criada por Yoji Akao em 1966 e popularizada durante a década de 80 ao ser implementada em empresas como a Mitsubishi Heavy, Ford e Xerox.

O QFD propõe a criação de uma matriz comumente chamada de "Casa de Qualidade", na qual avalia-se os requisitos do cliente atribuindo a cada um destes uma pontuação, além de correlacioná-los entre si. O preenchimento da matriz é feito no formato de uma casa, seguindo o modelo apresentado na Figura 1, inclui-se primeiramente os requisitos do cliente e o grau de importância dado a cada um com base na opinião do cliente. Em seguida, são inseridos os requisitos técnicos, que são ações e características que agregam as qualidades do produto. Para exemplificar, podemos dizer que na produção de um suco os requisitos do cliente são: apresentar ótimo sabor, ser uma bebida integral, conter baixa adição de açucar e ter um bom preço; já os requisitos técnicos são: qualidade e quantidade das frutas, quantidade de açúcares, tipo e quantidade de conservantes, preço do produto e volume da embalagem. 

<center><img src="{{ 'assets/img/walker/walker_qfd_ex.png' | relative_url }}" alt="Estrutura QFD" width="500"/>
</center>
<center>Figura 1: Estrutura de uma matriz QFD. Fonte: voitto</center>
<p/>

Para relacionar os requisitos do cliente com os técnicos existe a matriz de relacionamentos, na qual classifica as relações como fraco, médio ou forte. Estas relações devem ser pensadas pela equipe, de modo a avaliar quais as características que interferem ou não nas necessidades do cliente. Voltando ao exemplo anterior, observa-se que existe uma forte relação entre o suco ser integral e a quantidade de frutas e conservantes, mas há uma fraca relação com o preço do produto. Além disso, o QFD contém uma área destinada à análise da concorrência, na lateral direita, que busca qualificar o desempenho de produtos com funções similares de acordo com a opinião dos clientes sobre os requisitos apresentados. Por fim, é realizada pela equipe a avaliação técnica, a fim de determinar a importância técnica dos requisitos por meio de pesos, em porcentagem.

Após o entendimento da ferramenta, a equipe a aplicou durante a ideação do robô Walker, resultando na casa de qualidade ilustrada na Figura 2. Para facilitar o entendimento foi criada também uma legenda com os símbolos utilizados no desenho, apresentada na Figura 3. Vale lembrar que por se tratar de um projeto acadêmico, feito para um estudo, não foi necessário nem interessante realizar a "análise da concorrência". Os requisitos do cliente e o grau de importância deles foram elaborados em uma reunião e os requisitos técnicos e demais componentes foram pensados em equipe.

<center><img src="{{ 'assets/img/walker/walker_QFD.png' | relative_url }}" alt="Estrutura QFD" width="800"/>
</center>
<center>Figura 2: QFD do projeto Walker. Fonte própria. </center>
<p/>

<center><img src="{{ 'assets/img/walker/walker_QFD_legenda.png' | relative_url }}" alt="Estrutura QFD" width="500"/>
</center>
<center>Figura 3: Legenda para o QFD do projeto Walker. Fonte própria. </center>
<p/>
<!-- melhorar figura da legenda-->
Com isso, foi observado que a qualidade mais importante ao nosso produto é a capacidade de detectar obstáculos, que está fortemente correlacionada com várias competências estipuladas e fortemente relacionada com o requisito mais importante para o cliente, ser capaz de desviar de obstáculos. Já sobre os requistos técnicos com menor peso, estão fracamente relacionados e com poucas correlações, mas ainda assim são relevantes ao produto. Conclui-se que a ferramenta QFD foi de enorme auxílio para ouvir de maneira eficiente as necessidades do nosso cliente e definir as qualidades necessárias ao produto, assim como os focos de desenvolvimento do nosso produto. 

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

<br>