---
layout: post
title: Modelo matemático do Bbot
subtitle: Uma abordagem em controle by Matheus França
cover-img: assets/img/bbot/bbot_wide.png
thumbnail-img: assets/img/bbot/bbot.png
share-img: assets/img/rosa-logo-redondo.png
comments: true
tags: [bbot]
---

<!------------------------------------------------------------------- 
>  Intro:
>    - O que é modelo matemático
>    - Pq fazer
>    - Referencias utilizadas.
>
>  Modelo:
>    - Qual modelo foi utilizado
>    - Quais aproximações foram feitas
>    - Como foi calculado o modelo e os parâmetros do robô
>
>  Controle:
>    - Qual controlador foi utilizado e pq
>    - Como foi linearizado e discretizado
>    - Quais estados foram usados
>    - Observabilidade e controladbilidade
>    - Matriz de ganho e análise dos polos
>
>  Simulação em python:
>    - Mostrar todo o processo feito no jupyter com o sympy e o python.control
>    - Mostrar gráficos e gifs de simulação com o scipy
>
>  ROS:
>    - Falar sobre o controlador para o ros_control
>    - Mostrar simulação no Gazebo
>
>  Próximos passos:
>    - Implementar o controlador da prática 
------------------------------------------------------------------->

Os sistemas de controle podem ser representados por um conjunto de equações matemáticas conhecidas como **modelo matemático**. Esses modelos são úteis para análise e projeto de sistemas de controle. 
Como descrevemos no post anterior, [Testes reais do Bbot](https://mhar-vell.github.io/rasc/2021-09-02-bbot-testes-reais/), o controlador **PID** não conseguiu sustentar o robô. Portanto, decidimos fazer um estudo mais aprofundado do modelo matemático e de controle do robô. 
Foi feito então uma busca de artigos e trabalhos similares aos robôs self-balancing, no fim, 2 artigos se destacaram e formaram uma base para o nosso desenvolvimento, sendo eles, [Modeling and Control of Two-Legged Wheeled Robot](https://wiki.control.fel.cvut.cz/mediawiki/images/9/92/Dp_2021_kollarcik_adam.pdf) por Adam Kollarčík e [Dynamic modeling of a two-wheeled inverted pendulum balancing mobile robot](https://link.springer.com/article/10.1007/s12555-014-0564-8) por Sangtae Kim e Sang Joo Kwon

## Modelo

Sabemos que os modelos da maioria dos sistemas semelhantes ao pêndulos são conhecidos, e o nosso modelo (**Bbot**) não é uma exceção. Portanto, como referenciado, nós utilizamos um modelo usado nos artigos anteriores. O modelo de espaço de estado é o seguinte:
<br>

<p align="center">
$$
\begin{bmatrix}\ddot{x}\\
\ddot{φ}\\
\ddot{ψ}
\end{bmatrix} =
\begin{bmatrix}m_{11} & m_{12} & 0\\
m_{21} & m_{22} & 0\\
0 & 0 & m_{33}
\end{bmatrix}^{-1}
\begin{pmatrix}
\begin{bmatrix}
\frac{1}{r_0}(u_{0R} + u_{0L}) \\
m_plg\sin φ - u_{0R} - u_{0L} \\
\frac{w}{2}(u_{0R} - u_{0L})
\end{bmatrix}
-
\begin{bmatrix}
\frac{2b}{r_0^2} & d_{12} & d_{13}\\ 
\frac{-2b}{r_0} & 2b & d_{23}\\
d_{31} & d_{32} & d_{33}
\end{bmatrix}
\begin{bmatrix}\dot{x}\\
\dot{φ}\\
\dot{ψ}
\end{bmatrix}
\end{pmatrix}
$$
</p>

Onde:

<p align="center">
$$
m_{11} = m_p + 2m_0 + 2\frac{I_0}{r_0^2}, m_{12} = m_{21} = m_pl\cos φ, m_{22} = I_{py} + m_pl^2, 
$$
$$
m_{33} = I_{pz} + 2I_{0xy} + (m_0 + \frac{I_0}{r_0^2})\frac{w^2}{2} - (I_{pz} - I_{px} - m_pl^2) \sin^2 φ,
$$
$$
d_{12} = -m_pl\dot{φ}\sin φ - \frac{2b}{r_0}, d_{13} = m_pl\dot{ψ}\sin φ, d_{23} = (I_{pz} - I_{px} - m_pl^2)\dot{ψ}\sin φ\cos φ,
$$
$$
d_{31} = m_pl\dot{ψ}\sin φ, d_{32} = -d_{23}, d_{33} = -(I_{pz} - I_{px} - m_pl^2)\dot{φ}\sin φ \cos φ + \frac{w^2}{2r_0^2}b
$$
</p>

Temos parâmetros como inércia, massa, distância entre as rodas, torque nas rodas, gravidade e coeficiente de atrito. Vale mencionar que $x$ é a distância percorrida pelo pêndulo, $φ$ é o ângulo em pitch e $ψ$ é o ângulo em yaw.

Nós decidimos simplificar o modelo de forma que utilizamos as juntas estáticas. O movimento das juntas superiores será implementado nas próximas etapas.
Todos os valores dos parâmetros citados foram retirados do desenho técnico feito no software _Onshape_.

A próxima etapa para o desenvolvimento é a linearização do sistema, obtendo as matrizes $Ac$ e $Bc$. Essas matrizes são encontradas a partir da jacobiana em relação ao vetor de estados e do torque das rodas. Essas matrizes são avaliadas em um ponto fixo, que no nosso caso, foram todas em 0.

O sistema então é discretizado, obtendo as matrizes $Ad$ e $Bd$, usando o método de _zero-order hold_ com uma frequência setada para 25 Hz.

## Controle

Em muitos artigos nos deparamos com o controlador **LQR**, e observamos o seu bom desempenho nos sistemas. Já que não tivemos uma implementação muito eficiente com o **PID**, optamos por seguir para implementação de um método semelhante, porém, com uma diferença, que é usar o LQR no sistema discretizado, usamos então a função **Discrete-time Linear Quadratic Regulator** (DLQR). 

Já com o modelo linearizado, retiramos o ângulo em yaw e a distância percorrida pelo pêndulo, já que não são estados necessários para a estabilização do mesmo. Em seguida criamos um sistema aumentado ($Aaug$, $Baug$, $Caug$ e $Daug$), permitindo a implementação de uma ação integral para a velocidade linear e velocidade em yaw, a fim de controlá-la por um valor de referência definido pelo operador.  

A partir destas matrizes, podemos fazer análises para saber se o sistema pode ser controlado e se o sistema é observável. A **controlabilidade** mede a capacidade de uma configuração particular do atuador controlar todos os estados do sistema, já a **observabilidade** mede a capacidade da configuração particular do sensor de fornecer todas as informações necessárias para estimar todos os estados do sistema. O sistema é controlável se a matriz de controlabilidade for _full rank_ e observável se a matriz de observabilidade for _full rank_. Nosso sistema passou nos dois testes. 

Então, seguimos para o procedimento de design do DLQR no sistema aumentado, obtendo a matriz de ganho K para a estabilização do pêndulo, e tendo como parâmetro as matriz de peso de entrada Q e R (já normalizadas). No final, temos uma matriz com os seguintes pesos: 
<br>

<p align="center">
$$ 
\tiny  
K = 
\begin{bmatrix}
-0.359816139587012 & -0.16899712716524 & -0.062273242637461 & -1.04054845575376 & 0.00552059416223505 & 0.0178652255170376\\
-0.359816139587049 & -0.168997127165247 & 0.062273242637461 & -1.04054845575384 & 0.00552059416223684 & -0.0178652255170376
\end{bmatrix}
$$
</p>

O dlqr pode ter sua estabilidade testada com seus autovalores. Se o valor absoluto deles estiver abaixo de 1, o sistema é estável. Nosso sistema retornou os seguintes valores:

<p align="center">
$$
\tiny
E =  
\begin{bmatrix}
0.00995189968460506 & 0.958224659846958 & 0.958224659846958 & 0.928541227517652 & 0.664161585872212 & 0.664161585872212
\end{bmatrix}
$$
</p>

Os valores satisfazem a regra de estabilidade do sistema. 

## Simulação em python

Para validar o modelo foi importante realizar a simulação do mesmo. Utilizamos o software _Matlab - Simulink_ para gerar o modelo linearizado (gif da esquerda) do sistema e com o Python, criamos o modelo não linear (gif da direita). 

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/bbot-pend_model-linear_matlab.gif' | relative_url }}" alt="Linear model" width="475"/>
    <img id="myImg" src="{{ 'assets/img/bbot/bbot-pend_model-nonlinear_python.gif' | relative_url }}" alt="Nonlinear model" width="250"/>
</p>

Após carregar o modelo na simulação, implementamos o controlador no sistema e ele respondeu muito bem aos testes.

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/model_control.gif' | relative_url }}" alt="Nonlinear model" width="800"/>
</p>

## ROS

Seguimos então para a simulação no _Gazebo - ROS_. E o controlador proposto pode ser visto no data flow em seguida. 

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/bbot-dlqr-ros-control.png' | relative_url }}" alt="Linear model" width="550"/>
</p>

Podemos ver nos vídeos seguintes que o controlador se comportou bem no simulador. Continuou estável contra distúrbios externos de até 800 N e se comportou bem ao receber comandos de movimentos lineares e angulares.

<center>
<iframe width="360" height="315" src="https://www.youtube.com/embed/ycF7wwak_io" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<iframe width="360" height="315" src="https://www.youtube.com/embed/yk-3Swis2Z4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>


## Próximos passos

Nesta etapa do projeto, nós apresentamos o modelo matemático do **Bbot**. <img src="{{ 'assets/img/bbot/bbot.png' | relative_url }}" alt="Bbot" width="17"/> 📚📖 <img src="{{ 'assets/img/bbot/bbot_stand.png' | relative_url }}" alt="Bbot" width="15"/>
<br>

Os resultados para os testes foram apresentados nas suas respectivas descrições. Para as próximas etapas, serão apresentados os testes com o robô real, demonstrando o controle e seus ajustes na prática.

Para uma abordagem mais abrangente do projeto e de como ele foi feito com o python control, siga para esse [link](https://mhar-vell.github.io/rasc/2021-09-24-py-control-bbot). 

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
          <td style="vertical-align: top;text-align: justify;"><small>Pesquisador Júnior (estagiário) no laboratório de Robótica e Sistemas Autônomos (RoSA), Senai Cimatec, graduando em Engenharia de Controle e Automação.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>

<!-- **************************************** MATH script **************************************** -->
<style TYPE="text/css">
code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}
</style>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
    tex2jax: {
        inlineMath: [['$','$'], ['\\(','\\)']],
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'] // removed 'code' entry
    }
});
MathJax.Hub.Queue(function() {
    var all = MathJax.Hub.getAllJax(), i;
    for(i = 0; i < all.length; i += 1) {
        all[i].SourceElement().parentNode.className += ' has-jax';
    }
});
</script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-AMS_HTML-full"></script>