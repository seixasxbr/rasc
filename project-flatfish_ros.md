---
layout: page
title: FlatFish
subtitle: FlatFish on ROS
---
{% assign date_format = site.date_format | default: "%B %-d, %Y" %}
{%- capture site_tags -%}
    {%- for tag in site.tags -%}
      {% if tag contains 'flatfish' %}
        {{- tag | first -}}{%- unless forloop.last -%},{%- endunless -%}
      {% endif %} 
    {%- endfor -%}
{%- endcapture -%}
{%- assign tags_list = site_tags | split:',' | sort -%}

<center><img src="{{ 'assets/img/flatfish_ros/ff_no_background.png' | relative_url }}" alt="flatfish" width="600"/></center>

<div class="before-content">
  <center>
    {%- for tag in tags_list -%}
      <br>
      <a href="#{{- tag -}}" class="btn btn-primary tag-btn"><i class="fas fa-tag" aria-hidden="true"></i>&nbsp;{{- tag -}}-posts&nbsp;({{site.tags[tag].size}})</a>
    {%- endfor -%}
  </center>    
  <!--hr class="mark"-->
</div>

### General Objective

The FlatFish prototype was developed with the software layer based on the robotics framework ROCK (Robot Construction Kit), originally developed by the CIMATEC partner [DFKI](https://www.dfki.de/web/) during the first phases of the project. However, ROCK has a very restricted community of users among institutions that practice robotics, and even smaller are the teams of developers that keep the framework up to date. Thus, to guarantee the dynamic and consistent performance of the development of several researches with the prototype, it is necessary to update it to a more robust framework with broader support.

<center><img src="{{ 'assets/img/flatfish_ros/ff_under_water.jpg' | relative_url }}" alt="flatfish" width="600"/></center>

This work aimed to update the robotics framework used in the FlatFish vehicle prototype, migrating the ROCK software components to the [ROS](https://www.ros.org/) framework (Robot Operating System). ROS is a flexible and comprehensive framework for writing robot software widely used in institutions that work with robotics development and innovation around the world. It has a large active community of users on forums. In addition, the release of new versions of ROS are scheduled and supported with well-known deadlines.


### Specific Objectives

1. Develop FF Concept Map
2. Create FF package set (Autoproj)
3. Create FF ROS Simulation
4. Thrusters ROS package
5. Camera ROS package
6. Sonar ROS package
7. Laser ROS package
8. EFuse ROS package
9. SMB ROS package
10. Basic navigation package
11. Pipeline Following
12. Bowtech ROS package
13. Basic Operation

## FlatFish

FlatFish is an autonomous vehicle developed by the Brazilian Institute of Robotics (BIR) in partnership with the Robotics Innovation Center (RIC) which belongs to the Bremen location of the German Research Center for Artificial Intelligence (DFKI GmbH). The Aim of FlatFish is to perform repeated inspection of Oil and Gas subsea structures, such as pipelines, manifolds and subsea isolation valve (SSIV). It was designed to be a subsea-resident AUV, meaning that a docking station present on the sea bottom enables the vehicle to recharge its battery and exchange data with a topside base while underwater.

<center>
<img src="{{ 'assets/img/flatfish_ros/flatfish1.jpeg' | relative_url }}" alt="FlatFish" width="550"/><br>
</center>

### Sensors and Features

FlatFish has advanced sensors and features, listed below, that allows it to accomplish its goals.

<center>
<table style="border-collapse:collapse;border-color:#ccc;border-spacing:0" class="tg"><thead><tr><th style="background-color:#f0f0f0;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Depth rating </th><th style="background-color:#f0f0f0;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">300 m</th></tr></thead><tbody><tr><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Weight <br>(in air) </td><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">275 kg</td></tr><tr><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Size (LWH) </td><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">220 cm x 105 cm x 50 cm</td></tr><tr><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Propulsion </td><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">6x 60N Enitech ring thrusters (120N in each direction)</td></tr><tr><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Battery </td><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Lithium-Ion battery 5,8 kWh (11,6 kWh) @ 48V</td></tr><tr><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Communication <br>(surface)</td><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Rock7mobile RockBlock Iridium satellite modem (1,6 GHz)<br><br>Digi XBee-Pro-868 (868 MHz)<br><br>Ubiquiti PicoStation M2 HP WLAN-Modul (2,4 GHz)</td></tr><tr><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Communication <br>(tethered)</td><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">10 GBit/s optical fibre<br><br>1 GBit/s Cat5e (max. 50m)</td></tr><tr><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Communication <br>(submerged)</td><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Evologics S2CR 48/78 kHz <br>usable as USBL transponder</td></tr><tr><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Light </td><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">4x Bowtech LED-K-3200 (3200 lumen each)</td></tr><tr><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Laser Line projector</td><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">2x Picotronic LD532-20-3(20x80)45-PL line laser<br> 20mW each @ 532nm</td></tr><tr><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Sonar </td><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">BlueView MB1350-45 Multibeam Profiler (inspection sonar)<br><br>Tritech Gemini 720i Multibeam Imager (navigation sonar)<br><br>2x Tritech Micron Sonar (obstacle avoidance)</td></tr><tr><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Camera </td><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">4x Basler ace acA2040-gc25 <br>2048x2048 at 25 frames/s,<br>colour, GigabitEthernet</td></tr><tr><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Depth sensor </td><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Paroscientific 8CDP700-I, <br>sampling rate of 5Hz</td></tr><tr><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">INS/AHRS </td><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">KVH 1750 IMU, <br>sampling rate of 100Hz</td></tr><tr><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">DVL </td><td style="background-color:#fff;border-color:inherit;border-style:solid;border-width:1px;color:#333;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;text-align:center;vertical-align:top;word-break:normal">Rowe SeaProfiler DualFrequency 300/1200 kHz, <br>sampling rate of 4Hz</td></tr></tbody></table>
</center>
<br>

## Sneak Peek

### Simulation

<center>
<iframe width="598" height="336" src="https://www.youtube.com/embed/0JDZHnm6zg8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

### Live Action
<center>
<img src="{{ 'assets/img/flatfish_ros/FF.jpg' | relative_url }}" alt="Thruster Test" width="598"/>

</center>

<br>

<!--equipe-->

<center><h3 class="post-title">Development Team</h3><br/></center>
<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><center><img src="{{ 'assets/img/people/diogomartins-1.png' | relative_url }}" width="100" alt="diogo" class="img-fluid rounded-circle" /></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/lucas-silva-1.jpg' | relative_url }}" width="100" alt="lucas" class="img-fluid rounded-circle"/></center></th>
          <th></th>
          <th><center><img src="{{ 'assets/img/people/marcoreis8b&w-1.png' | relative_url }}" width="100" alt="marco" class="img-fluid rounded-circle"/></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="33.33%">Diogo Martins</td>
          <td></td>
          <td width="33.33%">Lucas Silva</td>
          <td></td>
          <td width="33.33%">Marco Reis</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Robotics Enthusiast. Master student in Mechatronics, Specialist in Robotics and Autonomous Systems, Engineer in Automation and Control.</small></td>
          <td></td>
          <td style="vertical-align: top"><small>~</small></td>
          <td></td>
          <td style="vertical-align: top"><small>Senior Researcher - Master in Production Engineering and Electrical Engineer.</small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>

<div class="row">
  <div class=" col-xl-auto offset-xl-0 col-lg-4 offset-lg-0">
    <table class="table-borderless highlight">
      <thead>
        <tr>
          <th><center><img src="{{ 'assets/img/people/azielfreitas-1.png' | relative_url }}" width="100" alt="aziel" class="img-fluid rounded-circle" /></center></th>
        </tr>
      </thead>
      <tbody>
        <tr class="font-weight-bolder" style="text-align: center margin-top: 0">
          <td width="80%">Aziel Freitas</td>
        </tr>
        <tr style="text-align: center" >
          <td style="vertical-align: top"><small>Electrical Engineer and Robotics specialist.</small></td>
          <td></td>
          <td style="vertical-align: top"><small></small></td>
          <td></td>
          <td style="vertical-align: top"><small></small></td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

<br>

### Project Overview
1. Category: <font color="#fbb117">Maritime Robotics</font>
2. Duration: <font color="#fbb117">9 months </font>
3. Start: <font color="#fbb117">19/11/2020</font>
4. End: <font color="#fbb117">30/09/2021</font>
5. Repositories: 
* [bir.flatfish_ros-buildconf](https://github.com/Brazilian-Institute-of-Robotics/bir.flatfish_ros-buildconf)
* [bir.flatfish_ros-package_set](https://github.com/Brazilian-Institute-of-Robotics/bir.flatfish_ros-package_set)
* [flatfish_ros_lights_bowtech](https://github.com/Brazilian-Institute-of-Robotics/flatfish_ros_lights_bowtech)
* [flatfish_ros_camera_basler](https://github.com/Brazilian-Institute-of-Robotics/flatfish_ros_camera_basler)
* [flatfish_ros_efuse_serial](https://github.com/Brazilian-Institute-of-Robotics/flatfish_ros_efuse_serial)
* [flatfish_ros_simulation](https://github.com/Brazilian-Institute-of-Robotics/flatfish_ros_simulation)
* [flatfish_ros_thrusters_enitech](https://github.com/Brazilian-Institute-of-Robotics/flatfish_ros_thrusters_enitech)
* [flatfish_ros_system_mgm_board](https://github.com/Brazilian-Institute-of-Robotics/flatfish_ros_system_mgm_board)
* [flatfish_ros_sonar_tritech](https://github.com/Brazilian-Institute-of-Robotics/flatfish_ros_sonar_tritech)

6. Sponsor: <a href="http://www.senaicimatec.com.br/en/"><font color="#fbb117">Senai CIMATEC</font></a>


<br>

##### References
1. Britto Neto, João da Costa. Parameters identification of dynamic model and simulation of autonomous underwater vehicles. MS thesis. Federal University of Bahia, 2019.
2. Fossen, Thor I. Handbook of marine craft hydrodynamics and motion control. John Wiley & Sons, 2011.
3.  Saback, Rafael, et al. "Fault-tolerant control allocation technique based on explicit optimization applied to an autonomous underwater vehicle." OCEANS 2016 MTS/IEEE Monterey. IEEE, 2016.
4.  Albiez, Jan, et al. "Flatfish-a compact subsea-resident inspection auv." OCEANS 2015-MTS/IEEE Washington. IEEE, 2015.
5.  Saback, Rafael, et al. "Fault-tolerant control allocation technique based on explicit optimization applied to an autonomous underwater vehicle." OCEANS 2016 MTS/IEEE Monterey. IEEE, 2016. 


<br>
<hr class="mark">
<div id="full-tags-list">
<h3 class="post-title"><font color="#fbb117">Posts</font></h3>
  {%- for tag in tags_list -%}
      <h4 id="{{- tag -}}" class="linked-section">
          <i class="fas fa-tag" aria-hidden="true"></i>
          &nbsp;{{- tag -}}&nbsp;({{site.tags[tag].size}})
      </h4>
      <div class="post-list">
          {%- for post in site.tags[tag] -%}
              <div class="tag-entry">
                  <a href="{{ post.url | relative_url }}">{{- post.title -}}</a>
                  <div class="entry-date">
                      <time datetime="{{- post.date | date_to_xmlschema -}}">{{- post.date | date: date_format -}}</time>
                  </div>
              </div>
          {%- endfor -%}
      </div>
  {%- endfor -%}
</div>