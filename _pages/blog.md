---
title: Blog Entries
permalink: /blog
layout: default
---

<section class="recent-posts">
    <div class="section-title">
        <h2><span>Blog Entries</span></h2>
    </div>
    <div class="row listrecent">
        {% for post in site.categories.blog %}
        {% include featuredbox.html %}
        {% endfor %}
    </div>
</section>
