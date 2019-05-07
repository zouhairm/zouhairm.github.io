---
layout: bio
title: Bio & Career Timeline
permalink: /bio
comments: false
---
<div id="header" class="bg1">
  <div id="headerblob">
    <img src="./assets/img/me.png" class="img-circle imgme">
    <div id="headertext">
      <div id="htname">{{ page.title }}</div>
      <div id="htdesc">{{ site.author.description }}</div>
      <div id="htem">{{ site.author.email }}</div>
      <div id="icons">
        {% for social in site.author.social %}
        <div class="svgico">
          <a href="{{ social.url }}"><i class="fa fa-{{ social.title }} fa-lg" style="color:white"></i></a>
        </div>
        {% endfor %}
      </div>
      <div id="resume">
        <ul>
          <li><a href={{ site.author.cv }}>Resume</a></li>
        </ul>
      </div>  
    </div>
  </div>
</div>

<div class="container">
  <div id="timeline">
    <div class="timelineitem">
      <div class="tdate">2019 - Present</div>
      <div class="ttitle">Sabbatical</div>
      <div class="tdesc">Volunteering for Marine Conservation Projects</div>
    </div>
    <div class="timelineitem">
      <div class="tdate">2016 - 2018</div>
      <div class="ttitle">Kitty Hawk</div>
      <div class="tdesc">Director of Strategy and Partnerships</div>
      <div class="tdesc">Head of Product - Technical</div>
    </div>
    <div class="timelineitem">
      <div class="tdate">2012 - 2016</div>
      <div class="ttitle">Stanford University</div>
      <div class="tdesc">Ph.D. in Aeronautics and Astronautics</div>
      <div class="tdesc"> Thesis: <span class="thigh">Automated ATC for Non-Towered Airports</span></div>
      <div class="tdesc"> Topics: <span class="thigh">Markov Process, Machine Learning</span></div>
    </div>
    <div class="timelineitem">
      <div class="tdate">2012 - 2016</div>
      <div class="ttitle">Zee.Aero</div>
      <div class="tdesc">Guidance Navigation & Controls Engineer</div>
    </div>
    <div class="timelineitem">
      <div class="tdate">2010 - 2012</div>
      <div class="ttitle">Zee.Aero</div>
      <div class="tdesc">Software & Avionics Lead</div>
    </div>
    <div class="timelineitem">
      <div class="tdate">2008 - 2010</div>
      <div class="ttitle">Stanford Aero/Astro: Masters of Science</div>
      <div class="tdesc">Outstanding Student Award</div>
    </div>
    <div class="timelineitem">
     <div class="tdate">2004 - 2008</div>
      <div class="ttitle">McGill University: Bachelors of Engineering</div>
      <div class="tdesc">Mechanical Engineering, Computer Science minor</div>
    </div>
  </div>
</div>
