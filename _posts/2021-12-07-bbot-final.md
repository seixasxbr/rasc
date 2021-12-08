---
layout: post
title: Conclusão do projeto Bbot
subtitle: Um pequeno passo para o homem, mas um grande salto para a humanidade by Matheus França
cover-img: assets/img/bbot/retro.jpg
thumbnail-img: assets/img/bbot/you_win.jpg
share-img: assets/img/bbot/bancada-explode.png
comments: true
tags: [bbot]
---

Como última etapa de desenvolvimento do [projeto Bbot](https://mhar-vell.github.io/rasc/project-bbot/), decidimos realizar mais alguns ajustes no controlador para que o robô conseguisse desenvolver uma estabilidade mais suave. 

Durante alguns testes, para implementar a função de teleoperação do robô, percebemos que a leitura de velocidade linear estava errada. Os valores eram muito mais elevados do que o robô poderia alcançar. O erro era na conversão entre o dado do encoder dos Dynamixels para rad/s. Ao corrigir esse erro, o comportamento do controlador mudou bastante, fazendo necessária novamente a sintonização do controlador. Observamos também que a mudança deste parâmetro causou muita trepidação no robô, muito mais do que ele estava.

Fizemos então um **filtro média móvel** para tentar atenuar o sinal de controle vindo do controlador, porém, embora a resposta tenha ficado menos oscilante, o controlador ficou mais fraco. Então continuamos ajustando os parâmetros do controlador até chegar em um valor ideal para que o robô ficasse mais estável. 

Por fim, conseguimos parametrizar o controlador de forma ideal e **o robô consegue se equilibrar** sem trepidações e está muito mais estável!! 

<center>
<iframe width="720" height="415" src="https://www.youtube.com/embed/p4HWfqaTFYM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

A **fase 1** do Bbot chega a sua conclusão, mas a **fase 2** está prestes a começar e com muitos novos desafios e melhorias!! 

Da equipe de desenvolvimento ([Matheus França](linkedin.com/in/matheus-frança-b62044150) e [Lucas Souza](https://www.linkedin.com/in/lucas-lins-souza-51b1909a/)), um agradecimento especial para nosso orientador [Marco Reis](https://www.linkedin.com/in/marco-reis-061618/) e ao apoio de grande importância dos nossos colegas [Diogo Martins](https://www.linkedin.com/in/diogo-alexandre-martins-02b528163/), [Mateus Seixas](linkedin.com/in/mateus-seixas-59296a190), [Caio Maia](https://www.linkedin.com/in/caiomaia3/) e Luiz Ledezma.

{:.center}
<iframe width="100%" height="166" scrolling="no" frameborder="no" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/123393442&color=%23ff5500&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe><div style="font-size: 10px; color: #cccccc;line-break: anywhere;word-break: normal;overflow: hidden;white-space: nowrap;text-overflow: ellipsis; font-family: Interstate,Lucida Grande,Lucida Sans Unicode,Lucida Sans,Garuda,Verdana,Tahoma,sans-serif;font-weight: 100;"><a href="https://soundcloud.com/justinpfordmusic" title="JustinPatrickFord" target="_blank" style="color: #cccccc; text-decoration: none;">JustinPatrickFord</a> · <a href="https://soundcloud.com/justinpfordmusic/we-are-the-champions" title="We Are The Champions" target="_blank" style="color: #cccccc; text-decoration: none;">We Are The Champions</a></div>

{:.center}
![drawing600](../assets/img/bbot/level.png)


----------------

<br>
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