---
layout: page
title: AI Tech blog
css: "/css/index.css"
<!-- subtitle: This is where I will tell my friends way too much about me -->
use-site-title: true
bigimg: /img/cover_image/nasa_space.jpg
---

<div class="list-filters">
  <a href="/" class="list-filter filter-selected">Recent posts</a>
  <a href="/machine_learning/machinelearning" class="list-filter">Machine learning</a>
  <a href="/paper_review/paperreview" class="list-filter">Paper review</a>
  <a href="/algorithm/algorithm" class="list-filter">Algorithm</a>
  <!-- <a href="/tags" class="list-filter">Index</a> -->
</div>
<div class="posts-list">
  {% for post in site.tags.pinned %}
  <article>
    <a class="post-preview" href="{{ post.url | prepend: site.baseurl }}">
	    <h2 class="post-title">{{ post.title }}</h2>
	
	    {% if post.subtitle %}
	    <h3 class="post-subtitle">
	      {{ post.subtitle }}
	    </h3>
	    {% endif %}
      <p class="post-meta">
        Posted on {{ post.date | date: "%B %-d, %Y" }}
      </p>

      <div class="post-entry">
        {{ post.content | truncatewords: 50 | strip_html | xml_escape}}
        <span href="{{ post.url | prepend: site.baseurl }}" class="post-read-more">[Read&nbsp;More]</span>
      </div>
    </a>  
   </article>
  {% endfor %}
</div>

