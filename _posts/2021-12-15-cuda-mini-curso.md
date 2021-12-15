---
layout: post
title: CUDA
subtitle: Programação Paralela by Mateus Seixas
cover-img: #assets/img/2021-12-15-kinematics-article/aplica2.jpg
thumbnail-img: #assets/img/2021-12-15-kinematics-article/scara.png
share-img: /assets/img/rosa-logo-redondo.png
comments: true
tags: [rasc]
---
## O que é CUDA? Porque utilizar?

CUDA, acrônimo de Compute Unified Device Architecture, é um modelo de programação em paralelo que permite o uso das GPUs (Graphics Processing Unit) para processamento de dados em programas. As GPUs são dispositivos que possuem enorme poder de processamento para dados em paralelo, como processamento de imagens e matrizes, e sua capacidade de processamento tem aumentado muito superiormente a capacidade de processamento das CPUs nos últimos anos, como mostrado na figura a seguir. Com o uso dessa ferramenta, muitos problemas complexos podem ser resolvidos com um menor tempo de execução. 

{:.center}
[![drawing500](../assets/img/2021-12-15-cuda-mini-curso/gpuvccpu.png)](../assets/img/2021-12-15-cuda-mini-curso
/gpuvccpu.png) 

A programação em CUDA pode ser utilizada em diversas aplicações que envolvem processamento de muitas informações em paralelo, como processamento de imagens, simulações, cálculos matriciais e vetoriais, algoritmos de busca, química computacional, ordenação, inteligência computacional, deep learning, entre outros.

## Diferenças entre CPU e GPU

As CPUs tem uma grande parte do sua área de silício dedicada a unidades de controle e de memória cache e possui apenas algumas Unidades Lógicas Aritméticas (ULA). Enquanto isso, as GPUs possuem a maior parte de sua área de silício preenchidas por ULAs.

{:.center}
[![drawing500](../assets/img/2021-12-15-cuda-mini-curso/Cpu-gpu.svg)](../assets/img/2021-12-15-cuda-mini-curso
/Cpu-gpu.svg) 



<!-- A linguagem CUDA é praticamente C/C++ com algumas extensões. Sendo que é possível usar o recurso  -->

<center>
  <img src="{{ 'assets/img/2021-12-15-cuda-mini-curso/gpuvccpu.png' | relative_url }}" width="600" text-align=center alt="img1" />
</center>
<br>



<br>
<iframe src ="https://drive.google.com/file/d/1bdZ56AsbMFPB-PsMLYJCUCNfLarYLGr3/preview" width='740' height='430' allowfullscreen mozallowfullscreen webkitallowfullscreen></iframe>
<br>

---------------------
<br>

<!-- autor -->
<center><h3 class="post-title">Autor</h3><br/></center>
<div class="row">
  <div class="col-xl-auto offset-xl-0 col-lg-4 offset-lg-0 center">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><img src="{{ 'assets/img/people/mateusseixas-1.png' | relative_url }}" width="100" alt="mateusseixas" class="img-fluid rounded-circle" /></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td>Mateus Seixas</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Pesquisador Jr. <br>Engenheiro Eletricista</small></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>