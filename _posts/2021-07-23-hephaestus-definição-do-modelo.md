---
layout: post
title: Definição do modelo Hephaestus 
subtitle: conceitos do robô
cover-img: assets/img/hefesto/hephaestus_wide.png
thumbnail-img: assets/img/hefesto/hephaestus.png
share-img: assets/img/rosa-logo-redondo (180).png
author: Matheus França
comments: true
tags: [hephaestus]
---

<!-- **************************************** -->
<!-- ### Introdução -->

<p>
O protótipo do humanoide será utilizado como objeto de testes e assim promoverá os avanços nas mais diversas técnicas de robótica e inteligência artificial. A plataforma robótica será desenvolvida utilizando o ROS (Robot Operating System), que é uma coleção de frameworks de software para desenvolvimento de robôs, que fornece a funcionalidade de um sistema operacional em um cluster de computadores heterogêneos. Nesta etapa do projeto encontra-se descrito detalhadamente todas as explicações do modelo do robô. 
</p>{: style="text-align: justify;"}

<p>
Para iniciarmos a construção do robô, definimos como prioridade utilizar componentes já disponíveis no laboratório da instituição (<a target="_blank" href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>). Além disso, o <a href="https://mhar-vell.github.io/rasc/project-hephaestus/"><font color="#fbb117">projeto Hephaestus</font></a> deverá atender requisitos baseados nas necessidades e expectativas de pesquisa. 
</p>{: style="text-align: justify;"}


<hr>

<!-- **************************************** -->
### Especificações técnicas 

Para nortear nosso projeto, seguimos algumas especificações técnicas. São estes:

<p>
<strong>Utilizar um Framework de robótica conhecido</strong>, que vai nos garantir ter uma base maior de pacotes já disponíveis. Deve ter uma altura aproximada de <strong>510mm</strong> e pesar por volta de <strong>3.5kg</strong>, tudo isso comportando um total de <strong>22 Graus de Liberdade</strong>. Além disso, deve comportar um <strong>controlador</strong> de baixo nível e um de alto nível, isso vai ser importante na aquisição de dados e na interface com o operador do robô. 
</p>{: style="text-align: justify;"}

<p>
O <strong>Hephaestus</strong> também deve ser capaz de perceber o mundo a sua volta, por tanto, utilizar uma câmera estéreo é fundamental. 
</p>{: style="text-align: justify;"}

<!-- **************************************** -->
### Selecionando os componentes 

<p>
Aqui está uma lista completa de peças até o momento (sujeito a alterações):
</p>{: style="text-align: justify;"}

<style type="text/css">.tg-sort-header::-moz-selection{background:0 0}.tg-sort-header::selection{background:0 0}.tg-sort-header{cursor:pointer}.tg-sort-header:after{content:'';float:right;margin-top:7px;border-width:0 5px 5px;border-style:solid;border-color:#404040 transparent;visibility:hidden}.tg-sort-header:hover:after{visibility:visible}.tg-sort-asc:after,.tg-sort-asc:hover:after,.tg-sort-desc:after{visibility:visible;opacity:.4}.tg-sort-desc:after{border-bottom:none;border-width:5px 5px 0}@media screen and (max-width: 767px) {.tg {width: auto !important;}.tg col {width: auto !important;}.tg-wrap {overflow-x: auto;-webkit-overflow-scrolling: touch;margin: auto 0px;}}</style><div class="tg-wrap"><table id="tg-hI3V7" style="border-collapse:collapse;border-color:#9ABAD9;border-spacing:0;margin:0px auto" class="tg"><thead><tr><th style="background-color:#409cff;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#fff;font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">COMPONENTES</th><th style="background-color:#409cff;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#fff;font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">QTD</th><th style="background-color:#409cff;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#fff;font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">LINK</th><th style="background-color:#409cff;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#fff;font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">VALOR TOTAL ($USD)</th></tr></thead><tbody><tr><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">DYNAMIXEL MX-106</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">2</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://www.robotis.us/dynamixel-mx-106t/" target="_blank" rel="noopener noreferrer">Dynamixel Robotis</a></td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><span style="font-weight:400;font-style:normal">1079,8</span></td></tr><tr><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">DYNAMIXEL MX-28</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">18</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://www.robotis.us/dynamixel-mx-28t/" target="_blank" rel="noopener noreferrer">Dynamixel Robotis</a></td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">4318,2</td></tr><tr><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">OpenCR</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://www.robotis.us/opencr1-0/" target="_blank" rel="noopener noreferrer">Robotis</a></td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">196,1</td></tr><tr><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">MPU6050</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://produto.mercadolivre.com.br/MLB-1820250930-acelermetro-e-giroscopio-3-eixos-gy521-mpu6050-gy521-c-nfe-_JM?matt_tool=87716990&amp;amp;matt_word=&amp;amp;matt_source=google&amp;amp;matt_campaign_id=12413740998&amp;amp;matt_ad_group_id=119070072438&amp;amp;matt_match_type=&amp;amp;matt_network=g&amp;amp;matt_device=c&amp;amp;matt_creative=500702333978&amp;amp;matt_keyword=&amp;amp;matt_ad_position=&amp;amp;matt_ad_type=pla&amp;amp;matt_merchant_id=164968240&amp;amp;matt_product_id=MLB1820250930&amp;amp;matt_product_partition_id=337120033364&amp;amp;matt_target_id=pla-337120033364&amp;amp;gclid=CjwKCAjwiLGGBhAqEiwAgq3q_ly8hxZFz8qCPXFHc8ORE4E79RhaUB8MnjT3uuzdJ6T3VrzeIPiazBoCMR0QAvD_BwE" target="_blank" rel="noopener noreferrer">IMU MercadoLivre</a></td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">3,28</td></tr><tr><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal"><span style="font-weight:400;font-style:normal">Mynt Eye S1030</span></td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://www.mynteye.com/products/mynt-eye-stereo-camera" target="_blank" rel="noopener noreferrer">mynteye</a></td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">199,0</td></tr><tr><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">RaspberryPI 4</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://www.raspberrypi.org/" target="_blank" rel="noopener noreferrer">RPI 4 raspberrypi</a></td><td style="background-color:#EBF5FF;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">80,93</td></tr><tr><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:left;vertical-align:top;word-break:normal">Lipo 3s (11.1v)</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">1</td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal"><a href="https://produto.mercadolivre.com.br/MLB-1589040239-bateria-lipo-2200mah-111v-3s-40c-80c-xt60-aero-drone-heli-_JM#position=1&search_layout=grid&type=pad&tracking_id=148eeb44-1cce-4313-8fa9-78ecc0a35ac7&is_advertising=true&ad_domain=VQCATCORE_LST&ad_position=1&ad_click_id=Njg2OWMxZDUtMzdmOS00NjA4LTk0YjYtNjk0ZWE1YTU0NTJh" target="_blank" rel="noopener noreferrer">Bateria MercadoLivre</a></td><td style="background-color:#D2E4FC;border-bottom-width:1px;border-color:inherit;border-style:solid;border-top-width:1px;border-width:0px;color:#444;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">41,72</td></tr></tbody></table></div><script charset="utf-8">var TGSort=window.TGSort||function(n){"use strict";function r(n){return n?n.length:0}function t(n,t,e,o=0){for(e=r(n);o<e;++o)t(n[o],o)}function e(n){return n.split("").reverse().join("")}function o(n){var e=n[0];return t(n,function(n){for(;!n.startsWith(e);)e=e.substring(0,r(e)-1)}),r(e)}function u(n,r,e=[]){return t(n,function(n){r(n)&&e.push(n)}),e}var a=parseFloat;function i(n,r){return function(t){var e="";return t.replace(n,function(n,t,o){return e=t.replace(r,"")+"."+(o||"").substring(1)}),a(e)}}var s=i(/^(?:\s*)([+-]?(?:\d+)(?:,\d{3})*)(\.\d*)?$/g,/,/g),c=i(/^(?:\s*)([+-]?(?:\d+)(?:\.\d{3})*)(,\d*)?$/g,/\./g);function f(n){var t=a(n);return!isNaN(t)&&r(""+t)+1>=r(n)?t:NaN}function d(n){var e=[],o=n;return t([f,s,c],function(u){var a=[],i=[];t(n,function(n,r){r=u(n),a.push(r),r||i.push(n)}),r(i)<r(o)&&(o=i,e=a)}),r(u(o,function(n){return n==o[0]}))==r(o)?e:[]}function v(n){if("TABLE"==n.nodeName){for(var a=function(r){var e,o,u=[],a=[];return function n(r,e){e(r),t(r.childNodes,function(r){n(r,e)})}(n,function(n){"TR"==(o=n.nodeName)?(e=[],u.push(e),a.push(n)):"TD"!=o&&"TH"!=o||e.push(n)}),[u,a]}(),i=a[0],s=a[1],c=r(i),f=c>1&&r(i[0])<r(i[1])?1:0,v=f+1,p=i[f],h=r(p),l=[],g=[],N=[],m=v;m<c;++m){for(var T=0;T<h;++T){r(g)<h&&g.push([]);var C=i[m][T],L=C.textContent||C.innerText||"";g[T].push(L.trim())}N.push(m-v)}t(p,function(n,t){l[t]=0;var a=n.classList;a.add("tg-sort-header"),n.addEventListener("click",function(){var n=l[t];!function(){for(var n=0;n<h;++n){var r=p[n].classList;r.remove("tg-sort-asc"),r.remove("tg-sort-desc"),l[n]=0}}(),(n=1==n?-1:+!n)&&a.add(n>0?"tg-sort-asc":"tg-sort-desc"),l[t]=n;var i,f=g[t],m=function(r,t){return n*f[r].localeCompare(f[t])||n*(r-t)},T=function(n){var t=d(n);if(!r(t)){var u=o(n),a=o(n.map(e));t=d(n.map(function(n){return n.substring(u,r(n)-a)}))}return t}(f);(r(T)||r(T=r(u(i=f.map(Date.parse),isNaN))?[]:i))&&(m=function(r,t){var e=T[r],o=T[t],u=isNaN(e),a=isNaN(o);return u&&a?0:u?-n:a?n:e>o?n:e<o?-n:n*(r-t)});var C,L=N.slice();L.sort(m);for(var E=v;E<c;++E)(C=s[E].parentNode).removeChild(s[E]);for(E=v;E<c;++E)C.appendChild(s[v+L[E-v]])})})}}n.addEventListener("DOMContentLoaded",function(){for(var t=n.getElementsByClassName("tg"),e=0;e<r(t);++e)try{v(t[e])}catch(n){}})}(document)</script>


<!-- **************************************** -->
### Diagrama de componentes

<p>
Já com o diagrama de componentes, podemos definir as conexões entre os componentes e obter uma visão geral do projeto.
</p>{: style="text-align: justify;"}

<p>
O diagrama se divide em <strong><i>head</i></strong>, <strong><i>arms</i></strong>, <strong><i>spine</i></strong> e <strong><i>legs</i></strong>. No bloco <i>head</i> se encontra a câmera estéreo (<i>Mynt Eye S1030</i>), e dois controladores para modificar a orientação da cabeça. O bloco <i>arms</i> comporta 6 atuadores. A <i>spine</i> comporta a eletrônica principal do robô, com os controladores e a fonte de alimentação do sistema (lipo 11.1v), além do IMU, sensor responsável pela medição de inclinação do robô. Já no bloco <i>legs</i>, é distribuído 10 atuadores para cada perna, sendo que dois deles tem uma capacidade de esforço maior, para a demanda da junta (<i>dynamixel mx-106</i>).
</p>{: style="text-align: justify;"}


<p>
É possível notar que as conexões entre os  componentes se dividem em <strong>potência</strong> (vermelho) e <strong>data</strong> (preto). Os atuadores são apresentados apenas com uma “linha” de potência, pois são conectados em cadeia, então optamos por essa descrição no diagrama.
</p>{: style="text-align: justify;"}

<p align="center">
    <img src="{{ 'assets/img/hefesto/components_diagram.png' | relative_url }}" alt="Diagrama de componentes" width="750"/>
</p> 

<!-- **************************************** -->
### Conclusão

<p>
Nessa primeira etapa do projeto Hephaestus, foi apresentado a metodologia do projeto e a definição do modelo. Com base nos parâmetros propostos aqui, podemos partir para descrição das funcionalidades!! <img src="{{ 'assets/img/hefesto/Hephaestus_front_back.png' | relative_url }}" alt="Hephaestus" width="17"/>
</p>{: style="text-align: justify;"}


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
