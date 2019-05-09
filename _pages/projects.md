---
title: Selected Projects
permalink: /projects
layout: default
---

<section class="recent-posts">
    <div class="section-title">
        <h2><span>All Stories & Projects</span></h2>
    </div>
    <div class="row listrecent">
        {% for post in site.categories.projects %}
        {% include postbox.html %}
        {% endfor %}
    </div>
</section>
