---
title: Bio & Career Timeline
permalink: /bio
layout: default
skipjumbotron: true
timeline:
  - date: "2019 - Present"
    title: "Sabbatical"
    desc: 
      - "Volunteering for Marine Conservation Projects"
    
  - date: "2016 - 2018"
    title: "Kitty Hawk"
    desc: 
      - "Head of Product"
    
  - date: "2012 - 2016"
    title: "Stanford University"
    desc: 
      - "PhD in Aeronautics & Astronautics"
      - "Thesis: <span class='thigh'>Automated ATC for Non-Towered Airports</span>"
      - "Topics: <span class='thigh'>Markov Process, Machine Learning</span>"
    
  - date: "2012 - 2016"
    title: "Zee.Aero"
    desc: 
      - "Guidance Navigation & Controls Engineer"
    
  - date: "2010 - 2012"
    title: "Zee.Aero"
    desc: 
      - "Software & Avionics Lead"
    
  - date: "2008 - 2010"
    title: "Stanford University"
    desc: 
      - "MSc in Aeronautics & Astronautics"
      - "Outstanding Student Award"
    
  - date: "2004 - 2008"
    title: "McGill University: Bachelors of Engineering"
    desc: 
      - "Mechanical Engineering, Computer Science minor"

  
---

<link rel="stylesheet" type="text/css" href="assets/css/bio.css">

{% assign author = site.authors["zouhair"] %}
<div id="header" class="bg1">
  <div id="headerblob">
    <img src="./assets/img/mypicture.png" class="img-circle imgme">
    <div id="headertext">
      <div id="htname">{{ author.name }}</div>
      <div id="htdesc">{{ author.description }}</div>
      <div id="icons">
        {% for social in author.social %}
           {% if social.url contains "://" %}
              {% assign faclass = "fab" %}
           {% else %}
              {% assign faclass = "fa" %}
           {% endif %}
        <div class="svgico">
          <a href="{{ social.url }}" target="_blank">
            <i class="{{ faclass }} fa-{{ social.title }} fa-lg" style="color:white"></i>
          </a>
        </div>
        {% endfor %}
      </div>
      <div class="container">
        <div id="timeline">
          {% for event in page.timeline %}
          <div class="timelineitem">
            <div class="tdate"> {{ event.date }} </div>
            <div class="ttitle">{{ event.title }}</div>
            {% for desc in event.desc %}
            <div class="tdesc"> {{ desc }} </div>
            {% endfor %}
          </div>
          {% endfor %}
        </div>
      </div>
    </div>
  </div>



</div>

