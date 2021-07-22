---
layout: post
title: Funcionalidades do Bbot
subtitle: Um robô que se equilibra com pernas articuladas
cover-img: assets/img/bbot/bbot_wide.png
thumbnail-img: assets/img/bbot/bbot.png
share-img: assets/img/rosa-logo-redondo (180).png
tags: [bbot]
---

<!-- **************************************** -->
### Anteriormente

É importante que você tenha visto o post anterior (<a href="https://mhar-vell.github.io/rasc/2021-07-21-bbot-definição-do-modelo-bbot/"><font color="#fbb117">[Etapa 1] Definição do modelo Bbot</font></a>), para um completo entendimento do desenvolvimento do projeto.

### Introdução
<p>
Na <strong>etapa dois</strong> do processo de construção do <a href="https://mhar-vell.github.io/rasc/project-bbot/"><font color="#fbb117">Bbot</font></a>, e de qualquer outro projeto de robótica, é <strong>importante</strong> definir as <strong>funcionalidades</strong>. Antes de iniciarmos as próximas etapas, o desenho da arquitetura do robô (mão na massa!! 👷🔧), precisamos listar essas características e analisar como elas estão conectadas entre si, assim tendo um total controle do desenvolvimento do projeto. 
</p>{: style="text-align: justify;"}

<hr>

<!-- **************************************** -->
### Diagrama das funcionalidades

<p>
No diagrama construído para o Bbot, podemos ver as seguintes funcionalidades: 
</p>{: style="text-align: justify;"}

- <p><strong>Subsistema de aquisição:</strong> Responsável pelos dados em baixo nível (dados dos sensores) </p>{: style="text-align: justify;"}
- <p><strong>Percepção:</strong> Compõem os drivers para percepção dos dados sensoriais</p>{: style="text-align: justify;"}
- <p><strong>Mapeamento:</strong> Utilizando as informações da Localização, é possível criar um mapa do ambiente</p>{: style="text-align: justify;"}
- <p><strong>Detecção:</strong> Responsável pela detecção da TAG (importante para missão do robô)</p>{: style="text-align: justify;"}
- <p><strong>Localização:</strong> Recebe dados do bloco de percepção, fazendo com que o robô se localize no ambiente</p>{: style="text-align: justify;"}
- <p><strong>Controle:</strong> Define a estratégia adotada para que o robô consiga se equilibrar. No nosso caso foi escolhido o controlador PID.</p>{: style="text-align: justify;"}
- <p><strong>Comportamento:</strong> Avalia as situações do ambiente e de estado do robô</p>{: style="text-align: justify;"}
- <p><strong>Inatividade:</strong> Posição de proteção do robô por motivos de falha</p>{: style="text-align: justify;"}
- <p><strong>Planejamento de trajetória:</strong> Segue uma trajetória definida na interface</p>{: style="text-align: justify;"}
- <p><strong>Navegação:</strong> Executa a trajetória e na falha de navegação, envia um comando de replanejamento de trajetória </p>{: style="text-align: justify;"}
- <p><strong>Atuação:</strong> Controles nas pernas e de locomoção</p>{: style="text-align: justify;"}

<p align="center">
    <img id="myImg" src="{{ 'assets/img/bbot/diagrama_funcionalidades_v2.png' | relative_url }}" alt="Diagrama de funcionalidades" width="750"/>
</p>

<!--  **************************************** MODAL IMG ****************************************-->
  <html>
  <head>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
  body {font-family: Arial, Helvetica, sans-serif;}

  #myImg {
      border-radius: 5px;
      cursor: pointer;
      transition: 0.3s;
      display: block;
      margin-left: auto;
      margin-right: auto
  }
  #myImg:hover {opacity: 0.7;}

  /* The Modal (background) */
  .modal {
      display: none; /* Hidden by default */
      position: fixed; /* Stay in place */
      z-index: 99; /* Sit on top */
      padding-top: 50px; /* Location of the box */
      left: -70px;
      top: 0;
      width: 115%; /* Full width */
      height: 115%; /* Full height */
      overflow: auto; /* Enable scroll if needed */
      background-color: rgb(0,0,0); /* Fallback color */
      background-color: rgba(0,0,0,0.9); /* Black w/ opacity */
  }

  /* Modal Content (image) */
  .modal-content {
      margin: auto;
      display: block;
      width: 75%;
      //max-width: 75%;
  }

  /* Caption of Modal Image */
  #caption {
      margin: auto;
      display: block;
      width: 80%;
      max-width: 700px;
      text-align: center;
      color: #ccc;
      padding: 10px 0;
      height: 150px;
  }

  @-webkit-keyframes zoom {
      from {-webkit-transform:scale(1)}
      to {-webkit-transform:scale(2)}
  }
  
  @keyframes zoom {
      from {transform:scale(0.4)}
      to {transform:scale(1)}
  }

  @-webkit-keyframes zoom-out {
      from {transform:scale(1)}
      to {transform:scale(0)}
  }
  @keyframes zoom-out {
      from {transform:scale(1)}
      to {transform:scale(0)}
  }

  /* Add Animation */
  .modal-content, #caption {
      -webkit-animation-name: zoom;
      -webkit-animation-duration: 0.6s;
      animation-name: zoom;
      animation-duration: 0.6s;
  }

  .out {
    animation-name: zoom-out;
    animation-duration: 0.6s;
  }

  /* 100% Image Width on Smaller Screens */
  @media only screen and (max-width: 700px){
      .modal-content {
          width: 100%;
      }
  }

  </style>
  </head>
  <body>

  <!-- The Modal -->
  <div id="myModal" class="modal">
    <img class="modal-content" id="img01">
  <div id="caption"></div>
  </div>

  <script>
  // Get the modal
  var modal = document.getElementById('myModal');
  
  // Get the image and insert it inside the modal - use its "alt" text as a caption
  var img = document.getElementById('myImg');
  var modalImg = document.getElementById("img01");
  var captionText = document.getElementById("caption");
  img.onclick = function(){
      modal.style.display = "block";
      modalImg.src = this.src;
      modalImg.alt = this.alt;
      captionText.innerHTML = this.alt;
  }
  
  
  // When the user clicks on <span> (x), close the modal
  modal.onclick = function() {
      img01.className += " out";
      setTimeout(function() {
        modal.style.display = "none";
        img01.className = "modal-content";
      }, 400);
      
  } 

  </script>

  </body>
  </html>
<!--  **************************************** MODAL IMG ****************************************-->

### Conclusão

<p>
Na <strong>segunda etapa</strong> do projeto, foram apresentadas as funcionalidades e como elas estão relacionadas. Com base nos parâmetros propostos aqui, podemos partir para a construção do Bbot!! <img src="{{ 'assets/img/bbot/bbot.png' | relative_url }}" alt="Bbot" width="17"/> &#128295; <img src="{{ 'assets/img/bbot/bbot_stand.png' | relative_url }}" alt="Bbot" width="15"/>
</p>{: style="text-align: justify;"}

<!-- **************************************** -->
<!-- ### Veja a seguir

<a href="https://mhar-vell.github.io/rasc/2021-07-28-bbot-modelo-3d-do-bbot-etapa-2/"><font color="#fbb117">[Etapa 2] Construindo o Bbot (Modelo 3d)</font></a> - disponivel em 28/07/2021
 
<a href="https://mhar-vell.github.io/rasc/2021-08-04-bbot-esquematico-ee-etapa-3/"><font color="#fbb117">[Etapa 3] Esquemático EE</font></a> - disponivel em 04/08/2021

<a href="https://mhar-vell.github.io/rasc/2021-08-11-bbot-simulacao-etapa-4/"><font color="#fbb117">[Etapa 4] Simulação</font></a> - disponivel em 11/08/2021

<a href="https://mhar-vell.github.io/rasc/2021-08-18-bbot-montagem-e-teste-etapa-5/"><font color="#fbb117">[Etapa 5] Montagem final e teste</font></a> - disponivel em 18/08/2021 -->

<br>
<hr>

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
<hr>


<!-- **************************************** BT TOP **************************************** -->
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 20px;
}

#myBtn {
  display: none;
  position: fixed;
  bottom: 20px;
  right: 30px;
  z-index: 99;
  font-size: 18px;
  border: none;
  outline: none;
  background-color: red;
  color: white;
  cursor: pointer;
  padding: 15px;
  border-radius: 4px;
}

#myBtn:hover {
  background-color: #555;
}
</style>
</head>
<body>

<button onclick="topFunction()" id="myBtn" title="Go to top">Top</button>

<script>
//Get the button
var mybutton = document.getElementById("myBtn");

// When the user scrolls down 20px from the top of the document, show the button
window.onscroll = function() {scrollFunction()};

function scrollFunction() {
  if (document.body.scrollTop > 20 || document.documentElement.scrollTop > 20) {
    mybutton.style.display = "block";
  } else {
    mybutton.style.display = "none";
  }
}

// When the user clicks on the button, scroll to the top of the document
function topFunction() {
  document.body.scrollTop = 0;
  document.documentElement.scrollTop = 0;
}
</script>

</body>
</html>
