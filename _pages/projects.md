---
title: Selected Projects
permalink: /projects
layout: default
---

<section class="recent-posts">
    <div class="section-title">
        <h2><span>Selected Projects</span></h2>
    </div>
    <div class="row listrecent">
        {% for post in site.categories.projects %}
        {% include featuredbox.html %}
        {% endfor %}
    </div>
</section>
