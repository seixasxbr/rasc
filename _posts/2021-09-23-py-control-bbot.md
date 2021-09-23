---
layout: post-page
title: Análise de sistemas e projetos de controladores em Python
subtitle: Uso do pacote *control* para análise e projeto de controladores para o Bbot em Python
cover-img: /assets/img/wesley-pribadi-iS1NV9yN0Lg-unsplash.jpg
thumbnail-img: /assets/img/ubuntu.png
share-img: /assets/img/rosa-logo-redondo.png
comments: true
---

<!-- ## Introdução -->

Quando imaginamos robôs interagindo com humanos ou realizando tarefas precisas antes feitas pro seres humanos, pensamos sempre na efetividade e precisão que eles conseguem atingir. Diferente de uma pessoa, um robô pode ser projetado para lidar com vários níveis de distúrbios externos para que estes não impactem no resultado final de sua missão. Para isso, a teoria de controle é fundamental, poi fornece várias ferramentas que nos permitem analisar os sistemas dos robôs e projetar controladores para que estes realizem as tarefas com bastante precisão e confiabilidade.

Hoje em dia, quando pensamos em analisar sistemas de controle, lembramos de softwares como MATLAB ou Octave, que possuem diversas ferramentas para análise de sistemas e projeto de controladores. Hoje em dia, contudo, existem bibliotecas em Python que nos fornecem algumas dessas ferramentas, e juntas com toda a diversa gama de aplicações implementadas para a linguagem, podem tornar a análise de sistemas extremamente rica e acessível, por ser Open Source.

Neste artigo, iremos mostrar como utilizamos Python para analisar os sistemas de controle do Bbot (um robô *self-balancing*) e projetar um controlador LQR (Linear Quadratic Regulator) através do uso de alguns pacotes essenciais:
1. [Control](https://python-control.readthedocs.io/en/0.9.0/intro.html)
2. [Sympy](https://www.sympy.org/en/index.html)
3. [Scipy](https://www.scipy.org/)

Se você caiu aqui e não sabe o que é o Bbot, não se preocupe, abaixo haverá uma breev descrição dele, mas caso você queira sabe mais sobre o projeto pode acessar a [página oficial](https://mhar-vell.github.io/rasc/project-bbot/) e acompanhar todos os nossos posts sobre seu desenvolvimento.

Uma dica, caso você queira acompanhar este artigo, é utilizar o [Jupyter notebook](https://jupyter.org/try), pois este facilita bastante ao mostrar automaticamente plots e as equações do sympy em Latex, que facilita muito o debug.

<br>

<!-- detalhamento -->

## 1. Geração do medelo matemático

O Bbot é um robô *self-balancing* que se equilibra em duas rodas e, assim, pode navegar por ambientes *indoor*. Seu princípio de funcionamento é extremamente semelhante ao do pêndulo invertido: ele precisa de um controlador que o mantenha sempre na vertical e que lhe permita de deslocar em duas dimensões espaço.

<!-- IMAGEM -->

Como pode ser visto na imagem acima, o Bbot possui duas pernas que o possibilitam agachar e levantar, logo, este não é extremamente semelhante o pêndulo invertido. Porém, como estas articulação devem ficar estáticas na maior parte do tempo, assumimos similaridade suficiente, para que pudéssemos nos basear em modelos pré-prontos deste tipo de robô, ao invés de criar um modelo mais específico para o Bbot (cenas para os próximos capítulos, quem sabe...). Em nossa análise, nos baseamos no modelo utilizado por Kollarčík em [SK8], que foi gerado por Kim e Kwon em [Model]. O processo de análise mostrado também seguirá o projeto de controle mostrado em [SK8].

Começamos a análise transcrevendo as matrizes do modelo mostradas em [Model] para o python. Como este modelo está em função de diversos parâmetros físicos do robô como massa, momentos de inércia, raio das rodas, etc., utilizamos o poder da matemática simbólica do Sympy para isso. O código ficou como o abaixo. 

```python
import numpy as np
from sympy import *
import matplotlib.pyplot as plt

#--- Model Parameters ---
d       = symbols('d',    real=True, positive=True)         # Distance between wheels
visc    = symbols('c_alpha',real=True)                      # Viscous, damping constant 
l       = symbols('l',    real=True, positive=True)         # Height of the COM
r       = symbols('r',    real=True, positive=True)         # Radius of the wheel
Mp      = symbols('M_p',  real=True, positive=True)         # Mass of the pendulum without the wheels
Mw      = symbols('M_w',  real=True, positive=True)         # Mass of each wheel
Iw_c    = symbols('I_wc',  real=True)                       # MOI wheel center
Iw_r    = symbols('I_wr',  real=True)                       # MOI wheel radial
Ip_x    = symbols('I_px',  real=True)                       # MOI pendulum x
Ip_y    = symbols('I_py',  real=True)                       # MOI pendulum y
Ip_z    = symbols('I_pz',  real=True)                       # MOI pendulum z

#--- Constants & Aux. variables ---
g = symbols('g', constant=True)                             # Gravity acceleration
t = symbols('t', real=True)                                 # Time

#--- State Variables ---
x           = symbols('x',  real=True)                      # Linear pos
pitch       = symbols('theta',  real=True)                  # Pitch angle
yaw         = symbols('psi',  real=True)                    # Yaw angle
x_vel       = Derivative(x,t)                               # Linear vel
pitch_vel   = Derivative(pitch,t)                           # Pitch vel
yaw_vel     = Derivative(yaw,t)                             # Yaw vel
x_acc       = Derivative(x_vel,t)                           # Linear acc
pitch_acc   = Derivative(pitch_vel,t)                       # Pitch acc
yaw_acc     = Derivative(yaw_vel,t)                         # Yaw acc

#--- Inputs ---
Tl = symbols('T_L', real=True)                              # Torque of the left wheel
Tr = symbols('T_R', real=True)                              # Torque of the right wheel

#*--- Matrices for the 3 states model
M = Matrix([[Mp+2*Mw+2*Iw_c/r**2, Mp*l*cos(pitch) ,                                                                     0],
            [ Mp*l*cos(pitch)   , Ip_y+Mp*l**2    ,                                                                     0],
            [0                  ,                0, Ip_z+2*Iw_r+(Mw+Iw_c/r**2)*d**2/2-(Ip_z-Ip_x-Mp*l**2)*sin(pitch)**2  ]])

C = Matrix([[                      0, -Mp*l*pitch_vel*sin(pitch),                          -Mp*l*yaw_vel*sin(pitch)],
            [                      0,                          0, (Ip_z-Ip_x-Mp*l**2)*yaw_vel*sin(pitch)*cos(pitch)],
            [Mp*l*yaw_vel*sin(pitch), -(Ip_z-Ip_x-Mp*l**2)*yaw_vel*sin(pitch)*cos(pitch), -(Ip_z-Ip_x-Mp*l**2)*pitch_vel*sin(pitch)*cos(pitch)]])

D = Matrix([[2*visc/r**2, -2*visc/r, 0],
            [-2*visc/r, 2*visc, 0],
            [0, 0, (d**2/(2*r**2))*visc]])

B = Matrix([[     1/r,     1/r],
            [      -1,      -1],
            [-d/(2*r), d/(2*r)]])

G = Matrix([[0],[-Mp*l*g*sin(pitch)], [0]])

q = Matrix([[x],[pitch],[yaw]])

q_diff = Matrix([[x_vel],[pitch_vel],[yaw_vel]])

q_2diff = Matrix([[x_acc],[pitch_acc],[yaw_acc]])

u = Matrix([[Tl],[Tr]])

M_inv = M.inv()
```


No trecho acima, nós definimos todos os símbolos que iremos utilizar, criamos as matrizes do sistema utilizando a classe `Matrix` do sympy e, devido a necessidade, computamos a matriz inversa de `M` chamando um dos métodos da classe. A vantagem de trabalhar com matemática simbólica é que todas as contas ficam em função de símbolos, portando não há erros de aproximação ou truncagem, como em operações em ponto flutuante.

Seguindo os artigos, geramos um vetor com as três esquações diferencias e mostramos da tela o resultado.

```python
expr_model = M_inv*((B*u-G)-(C+D)*q_diff)
eqts_model = Eq(q_2diff,expr_model)
eqts_model # Chamar a variável sozinha no Jupyter a faz mostrá-la na tela.
```

Como pode ser visto na saída, este modelo é um sistema de 3 equações diferenciais não-lineares modelando as velocidades linear, de yaw (ângulo em torno do eixo-z) e pitch (ângulo em torno do eixo-y). A partir destas equações, podemos gerar um modelo em epaço de estados do sistema com estas variáveis como estados. Porém, para este robô, podemos ampliar o modelo para controlar outras informações, como a posição linear, de pitch e de yaw. A posição de pitch é especialmente importante, pois não queremos apenas que o robô não caia (velocidade de pitch = 0), mas que mantenha a posição ereta (posição de pitch = 0). Logo, podemos adicionar estes 3 estados no modelo como mostrado no trecho abaixo. Para facilitar a análise posteriormente, trocamos os símbolos para `x1, x2, x3, ...` e mostramos na tela sua relação com os simbolos anteriores na última linha.

```python
#* Convert real variables into state-space variables

# Build state vector
real_state_vec = q_diff.row_insert(4,q)
state_vec = Matrix(list(symbols('x1:7',real=True)))
state_eq = Eq(state_vec,real_state_vec)
state_eq
```

Podemos agora incluir os novos estados no sistema anterior e substituir seus símbolos para `x1, x2, x3, ...`.

```python
#* Build the vector of system equations

system_equations = expr_model.row_insert(4,q_diff)

#* Substitute the real variables with the state-stape model variables: x1:x6

for i in range(6):
  system_equations = system_equations.subs(real_state_vec[i],state_vec[i])

#* Show the system of equations that will be used in the state space form 

eq_sys = Eq(state_diff_vec,system_equations)
eq_sys
```

## 2. Linearização do sistema

Até este ponto, temos um sistema de equações diferencias não-lineares com todas as informações que queremos para controlar o robô. Porém, como dito, este sistema é não-linear (devido a todos os senos e cossenos), e para projetar um controlador LQR, precisamos lenearizar este sistema. Se utilizarmos a aproximação de que senos e cossenos, para ângulos próximos de 0, são aproximadamente o próprio valor do ângulo e 1, respectivamente, podemos trabalhar com um sistema linear, caso o robô esteja próximo da posição vertical (ângulos de pitch pequenos). O que fazemos, portanto, é linearizar o sistema em torno de um posto fixo. Este ponto fixo, embora seja um ponto de equilíbrio do sistema, é instável, pois o mínimo desvio deste fará o robô cair. Logo nosso sistema é instável, por isso precisamos de um controlador para estabilizá-lo.

Para linearizar o sistema, calcularemos a matriz Jacobiana do sistema em função dos estados e das entradas de controle. Os estados foram citado acima, mas nossa entradas de controle são os torques em cada uma das rodas. Ou seja, pretendemos controlar o sistema mandando valores de torque para os motores da rodas, de forma que a valor dos estados tendam a 0 (ou qualquer outro ponto fixo que você escolher, mas para este sistema, será 0) ao longo do tempo. Calculamos a matriz Jacobina utilizando o sympy como mostrado abaixo.

```python

#* Calcualte the jacobian for the A and B matrix of the continuos time system
Ac = system_equations.jacobian(state_vec)
Bc = system_equations.jacobian(u)
# Ac
# Bc
```

Na primeira linha, calculamos a matriz `Ac` (matriz A do modelo em espaço de estados a partir do modelo em tempo contínuo), que é a Jacobina do sistema, que são as derivadas parcias das equações do sistema em relação os estados. Já a matriz `Bc` é a Jacobina em relação as entradas de controle. Você pode descomentar as últimas linhas para que o notebook mostre as matrizes.

Já temos as matrizes lenearizadas, porém ainda em símbolos, para os próximos passo, faremos a substituição destes para valores numéricos usando o método `subs` do sympy, como mostrado abaixo.

```python

#* Evaluate Ac and Bc at the fixed points

fixed_point = [0,0,0,0,0,0] # Values for dx/dt
input_fixed_points = [0,0]

Ac_eval = Ac.subs([(state_vec[0], fixed_point[0]),
                   (state_vec[1], fixed_point[1]),
                   (state_vec[2], fixed_point[2]),
                   (state_vec[3], fixed_point[3]),
                   (state_vec[4], fixed_point[4]),
                   (state_vec[5], fixed_point[5]),
                   (Tl,input_fixed_points[0]),
                   (Tr,input_fixed_points[1])])

Bc_eval = Bc.subs([(state_vec[0], fixed_point[0]),
                   (state_vec[1], fixed_point[1]),
                   (state_vec[2], fixed_point[2]),
                   (state_vec[3], fixed_point[3]),
                   (state_vec[4], fixed_point[4]),
                   (state_vec[5], fixed_point[5]),
                   (Tl,input_fixed_points[0]),
                   (Tr,input_fixed_points[1])])


# Define the values of each Model Parameter

d_v    = (d,    0.1431)
visc_v = (visc, 0.01)
r_v    = (r,    0.05)
Mp_v   = (Mp,   2.036)
Mw_v   = (Mw,   0.268)
Iw_c_v = (Iw_c, 0.00033613)
Iw_r_v = (Iw_r, 0.00018876)
g_v    = (g,    9.81)

#-- Pose A ---
l_v    = (l,   0.1806)
Ip_x_v = (Ip_x, 0.02500992)
Ip_y_v = (Ip_y, 0.02255237)
Ip_z_v = (Ip_z, 0.00546422)

#-- Pose B ---
# l_v    = (l,   0.17348)
# Ip_x_v = (Ip_x, 0.02387201)
# Ip_y_v = (Ip_y, 0.02163341)
# Ip_z_v = (Ip_z, 0.00568317)

#-- Pose C ---
# l_v    = (l,   0.13329)
# Ip_x_v = (Ip_x, 0.01811608)
# Ip_y_v = (Ip_y, 0.01688458)
# Ip_z_v = (Ip_z, 0.00669026)


#* Plug in the Model parameters values 

Ac_lin = Ac_eval.subs([d_v,visc_v,l_v,r_v,Mp_v,Mw_v,Iw_c_v,Iw_r_v,Ip_x_v,Ip_y_v,Ip_z_v,g_v])
Bc_lin = Bc_eval.subs([d_v,visc_v,l_v,r_v,Mp_v,Mw_v,Iw_c_v,Iw_r_v,Ip_x_v,Ip_y_v,Ip_z_v,g_v])

Ac_np = np.array(Ac_lin) # Converts it into a numpy array
Bc_np = np.array(Bc_lin) # Converts it into a numpy array
```

Para substituir o valor de vários símbolos de uma vez só, devemos passar uma lista de tuples contendo a variácel do símbolo e o valor. Primeiro, substituimos os valores do ponto fixo, que é 0 para todas as variáveis. Depois, criamos tuples com cada símbolo referente a um parâmetro do modelo e o valor referente ao modelo 3D do Bbot. Estes valores foram calculados pelo [Oneshape](https://www.onshape.com/en/). Devido ao fato do Bbot possuir pernas que modificam alguns parâmetros do modelo, calculamos os valores para 3 poses diferentes, como pode ser visto nas imagens abaixo. Por último, geramos uma `numpy.array()` destas matrizes.

<!-- POSES BBOT -->

## 3. Discretização do sistema

O modelo no qual nos baseamos considera um sistema em tempo contínuo, porém nós pretendemos gerar controladores possíveis de serem implementados num microcontrolador, que opera em tempo discreto. Portando, devemos discretizar o sistema. E aqui a biblioteca `control` começa a ajudar bastante. Podemos gerar um sistema em espaço de estados com as matrizes que calculamos e discretizar o sistema em apens duas linhas de código.

```python
import control

Ts = 0.01 # Sampling period. Fs = 100 hz

sysc = control.ss(Ac_np,Bc_np,np.eye(6),np.zeros((6,2)))
sysd = control.c2d(sysc,Ts,method='zoh')
Ad = sysd.A
Bd = sysd.B
```

Ao final, armazemos as matrizes do sistema discretizado nas variáveis `Ad` e `Bd`. O método de discretização utilizado, foi *zero-order hold* e o período de amostragem foi 0.01 segundos, o equivalente a uma frequência de amostragem de 100 Hz. Este valor é completamente arbritrário e o utilizamos como ponto de partida para a simulação. Futuramente, considerando a dinâmica dos motores reais do robô (não abordado neste artigo), poderemos modificar esse período para se adequar melhor à dinâmica do sistema. O período de amostragem delimita a frequência do loop de controle que será implmentado no robô. Ou seja, neste caso, nosso controlador deveria enviar esforços de controle para o sistema numa frequência de 100 Hz.

Como mostrado nos artigos, este robô não necessita controlar a posição linear e de yaw para se equilibrar. Portanto podemos reduzir o sistema para 4 estados, sendo eles: velocidade linear, velocidade de pitch, velocidade de yaw e ângulo de pitch. Fazer isso é bastante simples, basta remover as linhas das matrizes `Ad` e `Bd` correspontes a estes dois estados. Ao final, ficamos com a matriz `Ar` 4x4 e a matriz `Br` 4x2.

```python
Ar = np.vstack(( np.hstack((Ad[0:3,0:3], Ad[0:3,4].reshape(3,1))) , np.hstack((Ad[4,0:3], Ad[4,4])) ))
Br = np.vstack(( Bd[0:3,:], Bd[4,:] ))
```

## 4. Adição de ação integral no sistema

Com as matrizes `Ar` e `Br`, podemos projetar um controlar, implementá-lo em um microcontrolador e o robô será capaz de se equilibrar. Mas o Bbot é um robô móvel, e deve ser capaz de receber entradas de velocidade linear e de yaw e seguir essa referência. Dessa forma, será possível teleoperá-lo ou até implementar algoritmos de navegação autônoma. Para isso, precisamos garantir que o controlador consiga receber uma valor de referência controlar o sistema seguindo essa referência. Se falarmos "ande para frente a 0.3 m/s" ou "gire para a esquerda a 0.15 rad/s", este controlador deverá ser capaz de equilibrar o sistema equando este se move nesta velocidade. Para isso, devemos computar o erro entre a velocidade atual do robô e a referência e mandar para o controlador a integral deste erro. A integral irá garantir que este erro tenda a 0, ou seja, a velocidade atual seja igual à referência. 

Para isso, criamos um modelo aumentado do sistema, incluindo a integral do erro de velocidade linear e de yaw como estados. Modificamos as matrizes do sistema como mostrado abaixo.

```python
L_aug = np.hstack((np.array([[-1,0,0,0],
                             [0,0,-1,0]]), np.eye(2) ))
Upper_aug = np.hstack((Ar, np.zeros((4,2))))
A_aug = np.vstack((Upper_aug, L_aug))

B_aug = np.vstack((Br,np.zeros((2,2))))

# Matrix(A_aug)
# Matrix(B_aug)
```

## 4. Sistema de controle

Em posse das matrizes A e B para o sistema aumentado, presseguiremos com análise do sistema e o projeto do controlador. O primeiro passo que faremos é checar se este sistema é controlável, ou seja, checar se apenas com o torque das rodas como entradas de controle é possível levar os estados do sistema para o ponto fixo ao redor do qual nos o linearizamos. Também testaremos se o sistema é observável. Sistemas de controle podem possuir dezenas de estados, porém nem todos são capazes de serem medidos com sensores. Portanto, indicando apenas os estados que podemos medir (estes são as saídas do nosso sistema) podemos testar se os sistema ainda é observável. Caso seja, é possível projetar um estimador (um filtro de Kalman) que com apenas os dados dos estados medidos, é possível prever o valor dos outros estados e mandar estes dados para o controlador. No caso do Bbot, nos temos encoders nas rodas, do qual podemos calcular a velocidade lienar do robô sabendo o raio das rodas e um IMU, que nos fornece a posição, aceleração e velocidade angular do robô nos 3 eixos espaciais. Portando sabemos que podemos medir todos os estados, mas fizemos o teste apenas para completude da análise.

No trecho de código abaixo, usamos as funções `control.ctrb` e `control.obsv`, que nos retornam as matrizes de controlabilidade e observabilidade do sistema. Caso o rank dessas matrizes seja igual ao número de estados do sistema, o sistema é controlável e observável.

```python
#* Controlability and Observability for the augmented model

C_ss_aug = np.diag([1,1,1,1,1,1])
D_ss_aug = np.zeros((6,2))

ctrb_m = control.ctrb(A_aug,B_aug)
rank_ctrb = np.linalg.matrix_rank(ctrb_m) # If result is 6, the system is controlable

obs_m = control.obsv(A_aug,C_ss_aug)
rank_obs = np.linalg.matrix_rank(obs_m) # If result is 6, the system is controlable

print(rank_ctrb)    # 6 means Controllable
print(rank_obs)     # 6 means Observable
```

Podemos também avaliar os polos do sistema e confirmar nossa intuição de que o sistema é instável.

```python
sys_aug = control.ss(A_aug, B_aug, C_ss_aug, D_ss_aug)
abs(sys_aug.pole())
```

Como nosso sistema é discreto, analisamos a estabilidade seguindo a teoria de transformada Z. Analisando os polos do sistema, podemos ver que há polos cujo módulo é meior ou igual a 1.0, logo ele é instável.

Executando o código, vemos que o rank de ambas as matrizes é de fato 6, logo podemos gerar um controlador LQR para o sistema e, como temos todas as medidas, não precisamos projetar o estimador. Para projetar o controlador, precisamos das matrizes de custo `Q` e `R`. Essas matrizes contém valores de custo definidos pelo projetista, indicando suas prioridades de performance do sistema em relação a cada estado (matriz `Q`) e o custo da energia possível de ser demandado dos motores (matriz `R`). A biblioteca `control` possui uma função `control.lqr()` que, dadas as matrizes do sistema e matrizes `Q` e `R`, é retornada a matriz de ganho `K` do controlador. A função também retorna a resolução da equação de Ricatti (necessário no cálculo de `K`) e os polos do sistema controlado. Contudo essa função é destinada a sistemas de tempo contínuo. Até a data de publicação deste artigo não há a função para tempo discreto na biblioteca, porém um usuário fez a função e deixou o código disponível em uma [issue](https://github.com/python-control/python-control/issues/359#issuecomment-759423706) no repositório do python-control. O uso da função segue a mesma lógica. Abaixo está a função e o trecho de código conde calulamos a matriz `K` e os polos do sistema controlado, e vemos que todos estes têm módulo < 1.0.

```python
def dlqr_calculate(G, H, Q, R, returnPE=False):
  '''
  Discrete-time Linear Quadratic Regulator calculation.
  State-feedback control  u[k] = -K*x[k]

  How to apply the function:    
      K = dlqr_calculate(G,H,Q,R)
      K, P, E = dlqr_calculate(G,H,Q,R, return_solution_eigs=True)

  Inputs:
    G, H, Q, R  -> all numpy arrays  (simple float number not allowed)
    returnPE: define as True to return Ricatti solution and final eigenvalues

  Returns:
    K: state feedback gain
    P: Ricatti equation solution
    E: eigenvalues of (G-HK)  (closed loop z-domain poles)
  '''
  from scipy.linalg import solve_discrete_are, inv, eig
  P = solve_discrete_are(G, H, Q, R)  #Solução Ricatti
  K = inv(H.T@P@H + R)@H.T@P@G    #K = (B^T P B + R)^-1 B^T P A 

  if returnPE == False:   return K

  from numpy.linalg import eigvals
  eigs = np.array([eigvals(G-H@K)]).T
  return K, P, eigs

Q_lqr_aug = np.diag([1 /(0.5**2), 
                     100 /(0.1**1), 
                     1 /(1**1), 
                     1 /(0.14**2), 
                     2 /(1**2), 
                     2 /(2**2)])

R_lqr_aug = np.diag([1e2 /(0.5**2),
                     1e2 /(0.5**2)])

K_dlqr_aug, S_dlqr_aug, E_dlqr_aug = dlqr_calculate(A_aug,B_aug,Q_lqr_aug,R_lqr_aug,True)

# Matrix(K_dlqr_aug)
# Matrix(abs(E_dlqr_aug).reshape(1,6)) # If all are below 1, the system is stable
```
## 5. Simulação do sistema

Já temos as equações diferencias do nosso sistema e o controlador. Agora, devemos simular nosso sistema não-linear e checar se com este controlador é possível estabilizá-lo. Para simular o sistema, utilizaremos um solucionador de equações diferencias, o qual o pacote `scipy` fornece para a gente. Utilizaremos o vetor de equações diferencias do nosso sistema que criamos no início (apenas com os 4 estados que escolhemos) para criar uma função que, dados os valores atuais dos estados, é calculada as derivadas definidas no lado esquerdo da equação. O `scipy` utilizará isto para solucionar o sistema. 

Abaixo criamos um outro vetor com os valores dos parâmetros do robô já substituidos. Definimos as condições iniciais de cada estado,entradas, tempo inicial e referências de velocidade linear e de yaw. Usando a função `sympy.lambdify` podemos transformar uma expressão simbólica do `sympy` em uma função `lambda` do python, cujos parâmetros serão o tempo, o vetor dos estados e o vetor de entradas. Descomentado a última linha, podemos avaliar o sistema para os valores inicias definidos.

```python
#* Apply model parameters to the system equations

sys2sim = system_equations.subs([d_v,visc_v,l_v,r_v,Mp_v,Mw_v,Iw_c_v,Iw_r_v,Ip_x_v,Ip_y_v,Ip_z_v,g_v])
sys2sim.row_del(3)
sys2sim.row_del(4)

state_initial_conditions = [0,0,0,0]
initial_inputs = [0,0]
x_yaw_refs = np.array([0.2, 1]) # 0.2 m/s and 1 rad/s
t0 = 0

#* Create lambda functions of the system
reduced_state_vec = Matrix(list(symbols('x1:4, x5',real=True)))
func = lambdify([t, reduced_state_vec, u],sys2sim,'numpy')

# func(0,state_initial_conditions, initial_inputs) # Test the lambda function
```

Utilizando a classe `integrate.ode` do `scipy`, simulamos o sistema até 10 segundos e com passo de 0.01 segundos. Incluimos também ruído branco e um pulso de torque nas rodas de 6 a 6.3 segundos com valor de 0.3 Nm. Ao longo da simulação, vamos armazenando os valores dos estados, das entradas e do tempo em uma `numpy.array` para podermos plotar os resultados futuramente. Ao final da simulação, calculamos a integral da curva de velocidade linear para plotar a posição do robô ao longo do tempo.

```python
from scipy import integrate

simulator = integrate.ode(func)                                     # Ode class object used for simulation
simulator.set_initial_value(state_initial_conditions, t0)           # Set initial consitions of the system
simulator.set_integrator('vode')
simulator.set_f_params(initial_inputs)                              # Set the initial inputs (wheel torques) values in the system
# simulator.set_jac_params(initial_inputs)                            # Set the initial inputs (wheel torques) values in the jacobian

t1 = 10                                                           # Max. time for simulation  
dt = 0.01                                                          # Simulation time step
controller_time = 0                                                # Initial controller time (-1 means: "provide a control effort based on the initial states") 
controller_calls = 0                                                # Counts how many times the controller was called (just debug)

history = np.array([state_initial_conditions]).reshape(4,1)
# time_history = [t0]
time_history = np.arange(start=0,stop=t1+2*dt,step=dt)
input_history = np.array(initial_inputs).reshape(2,1)

Kp = K_dlqr_aug[:,0:4]
Ki = K_dlqr_aug[:,4:]

x_error = 0
yaw_error = 0
x_yaw_refs = np.array([0.2, 1])

mag_NOISE_y = 1e-3 # Magnitude of white noise

while simulator.successful() and simulator.t <= t1:                 # Simulation main loop
    history = np.hstack((history,np.array([simulator.integrate(simulator.t+dt)]).reshape(4,1) + np.random.rand(4,1)*mag_NOISE_y))        # Simulate one time step and save in history
    # time_history.append(simulator.t+dt)
    
    if simulator.t > 3:                         # Apply a reference change for X and Yaw vel
        x_yaw_refs = np.array([-0.3, 0])
    
    if simulator.t > 6 and simulator.t < 6.3: uIMPULSE = 0.3                      # Apply a torque pulse as external disturbance from time 3 - 4
    # elif simulator.t in time_history[int(3/dt):int(4/dt)]: uIMPULSE = -0.3
    else: uIMPULSE = 0.0
    controller_time += 1
    
    x_error += x_yaw_refs[0] - history[0,-1] 
    yaw_error += x_yaw_refs[1] - history[2,-1]
    error_matrix = np.array([x_error,yaw_error]).reshape(2,1)
    
    regulatory_part = -Kp@history[:,-1]
    integral_part = -Ki@error_matrix
    
    # Call the controller
    input_history = np.hstack((input_history,regulatory_part.reshape(2,1) + 
                               integral_part.reshape(2,1) + 
                               uIMPULSE))
    
    simulator.set_f_params(input_history[:,-1])       # Update the controller values in the systems equations
    
print(simulator.get_return_code())

x_pos = integrate.cumtrapz(y = history[0,:],x = time_history,initial=0) # Integrate the Velocity values to get position information
```

Em seguida, plotamos os resultados utilizando `matplotlib`.

```python
fig1 = plt.figure()
plt.plot(time_history,history[0,:])
plt.title("Linear vel")
plt.xlabel("time (s)")
plt.ylabel("m/s")
plt.grid()

fig2 = plt.figure()
plt.plot(time_history,history[1,:])
plt.title("Pitch vel")
plt.xlabel("time (s)")
plt.ylabel("rad/s")
plt.grid()

fig3 = plt.figure()
plt.plot(time_history,history[2,:])
plt.title("Yaw vel")
plt.xlabel("time (s)")
plt.ylabel("rad/s ")
plt.grid()

fig4 = plt.figure()
plt.plot(time_history,history[3,:])
plt.title("Pitch")
plt.xlabel("time (s)")
plt.ylabel("rad")
plt.grid()

fig5 = plt.figure()
plt.plot(time_history,input_history[0,:], label='Left Torque')
plt.plot(time_history,input_history[1,:], label='Rigth Torque')
plt.title("Wheel Torques")
plt.legend()
plt.xlabel("time (s)")
plt.ylabel("N.m")
plt.grid()

fig7 = plt.figure()
plt.plot(time_history,x_pos)
plt.title("X positions")
plt.xlabel("time (s)")
plt.ylabel("m")
plt.grid()
```

Exemplos de gifs gerados:

<!-- IMAGENS -->

Pelos gráficos, podemos analisar a performance do sistema ao longo de todo o tempo. Com os dados de torque e velocidade linear, por exemplo, podemos avaliar se estes estão dentro do range de trabalho dos atuadores do robô. Caso não estejam, podemos alterar os custos das matrizes do controlador ou simular distúrbios menores e ver os limites de funcionamento do robô.

Por fim, para ter uma análise mais visual do sistema, criamos uma animação usando também a biblioteca `matplotlib`.

```python
#Generates an animation using Matplotlib

from matplotlib.patches import Circle
from matplotlib.animation import FuncAnimation

xlim = (-1.5,1.5)
ylim = (-0.1,1.0)

fig = plt.figure(figsize=(8.3333, 7.25), dpi=72) #figsize=(8.3333, 7.25), dpi=72
ax = fig.add_subplot(111,xlim=xlim,ylim=ylim)
ax.set_aspect('equal')
ax.grid(alpha = 0.3)

height = 0.354

ax.plot([xlim[0],xlim[1]],[0,0],'-k')         # Ground

pend_rod, = ax.plot([x_pos[0], x_pos[0]+height*np.math.sin(history[3,0])],[r_v[1],r_v[1] + height*np.math.cos(history[3,0])], 'r', lw=3)
pend_wheel = ax.add_patch(Circle((x_pos[0],r_v[1]), r_v[1], fc='b', zorder=3))
time_template = 'time = %.3fs'
x_ref_template = 'X_vel input = %.1f m/s'
yaw_ref_template = 'Yaw_vel input = %.1f rad/s'

x_curr_template = 'Current X_vel = %.3f m/s'
yaw_curr_template = 'Current Yaw_vel = %.3f rad/s'


time_text = ax.text(0.02, 0.9, '', transform=ax.transAxes)
x_ref_text = ax.text(0.02, 0.8, '', transform=ax.transAxes)
yaw_ref_text = ax.text(0.02, 0.7, '', transform=ax.transAxes)
x_curr_text = ax.text(0.35, 0.8, '', transform=ax.transAxes)
yaw_curr_text = ax.text(0.35, 0.7, '', transform=ax.transAxes)

def init_anim():
  pend_rod, = ax.plot([x_pos[0], x_pos[0]+height*np.math.sin(history[3,0])],[r_v[1],r_v[1] + height*np.math.cos(history[3,0])], 'r', lw=3)
  pend_wheel = ax.add_patch(Circle((x_pos[0],r_v[1]), r_v[1], fc='b', zorder=3))
  time_text.set_text('')
  x_ref_text.set_text('')
  yaw_ref_text.set_text('')
  x_curr_text.set_text('')
  yaw_curr_text.set_text('')
  return pend_rod, pend_wheel, time_text, x_ref_text, yaw_ref_text, x_curr_text, yaw_curr_text
  
def animate(i):
  xaxis = [x_pos[i], x_pos[i] + height*np.math.sin(history[3,i])]
  yaxis = [r_v[1], r_v[1] + height*np.math.cos(history[3,i])]
  pend_rod.set_data(xaxis,yaxis)
  pend_wheel.set_center((x_pos[i],r_v[1]))
  
  time_text.set_text(time_template % (time_history[i]))
  x_curr_text.set_text(x_curr_template % (history[0,i]))
  yaw_curr_text.set_text(yaw_curr_template % (history[2,i]))
  
  if time_history[i] > 3:
    x_ref_text.set_text(x_ref_template % (-0.3))
    yaw_ref_text.set_text(yaw_ref_template % (0.0))
  else:
    x_ref_text.set_text(x_ref_template % (0.2))
    yaw_ref_text.set_text(yaw_ref_template % (1.0))
  
  return pend_rod, pend_wheel, time_text, x_ref_text, yaw_ref_text

anim = FuncAnimation(fig, animate,frames=len(time_history),interval=10,blit=True)
```

Para vizualisar, salvamos a animação em um arquivo `.gif`.

```python
anim.save("Gifs/disturbance3.gif", fps=36) #Generates a .gif for the animation
```

Exemplos de gifs gerados:


## 6. Conclusão

Estes foram os passos que seguimos para simular matematicamente o Bbot. Utilizamos várias ferramentas do python para isso, há muito mais. Caso queiram saber mais sobre os pacotes, basta acessar a documentação online no link deixado no início. E caso queiram saber mais sobre o projeto do Bbot, acesso nossa [página oficial](https://mhar-vell.github.io/rasc/project-bbot/). Obrigado!

<br>

<hr>

<!-- autor -->
<center><h3 class="post-title">Autor</h3><br/></center>
<div class="row">
  <div class="col-xl-8 offset-xl-0 col-lg-4 offset-lg-0 center">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><img src="{{ 'assets/img/people/lucaslins-1.png' | relative_url }}" width="100" alt="amarco" class="img-fluid rounded-circle" /></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td>Marco Reis</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top; text-align: justify"><small>Estagiário no laboratório de Robótica e Sistemas Autônomos (RoSA), SENAI CIMATEC, graduando em Engenharia Elétrica.</small></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>
