---
layout: page
title: "Paper review"
css: "/css/index.css"
subtitle: 3D vision
bigimg: /img/cover_image/review.jpg
---

<div class="list-filters">
  <a href="/index" class="list-filter">Back to Home</a>
  <a href="/paper_review/classification" class="list-filter">Classification</a>
  <a href="/paper_review/segmentation" class="list-filter">Segmentation</a>
   <a href="/paper_review/3D_vision" class="list-filter filter-selected">3D vision</a>
   <a href="/paper_review/others" class="list-filter">Others</a>
  <!-- <a href="/tags" class="list-filter">Index</a> -->
</div>

<div class="posts-list">
  {% for post in site.tags.review_3d %}
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