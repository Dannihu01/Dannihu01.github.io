---
title: News
layout: default
permalink: /news/
published: true
---

<div class="news-archive">
  <div class="news-section-heading"><h2>News</h2></div>

  {% include news-list.html excerpt_words=60 %}

  <p class="news-see-all">
    <a href="{{ '/' | relative_url }}">← Back to home</a>
  </p>
</div>
