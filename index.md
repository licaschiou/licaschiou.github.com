---
layout: page
title: Some Notes
tagline: data vizualization, frond-end, IxD
---
{% include JB/setup %}

{% for post in site.posts %}
   <h1><a href="{{ post.url }}">{{ post.title }}</a></h1>
   <p class="author">
    <span class="date">{{post.date | date: "%Y-%m-%d"}}</span>
  </p>
  <div class="content">
    {{ post.content }}
  </div>
  <div class="content-space"></div>
{% endfor %}

<div class="pagination pagination-centered">
  <ul>
  {% if paginator.previous_page %}
    {% if paginator.previous_page == 1 %}
      <li class="prev"><a href="/" title="Previous page">Prev</a></li>
    {% else %}
      <li class="prev"><a href="/page{{paginator.previous_page}}" title="Previous page">Prev</a></li>
    {% endif %}
  {% else %}
    <li class="prev disabled"><a>Prev</a></li>
  {% endif %}
  {% if paginator.next_page %}
    <li class="next"><a href="/page{{paginator.next_page}}" title="Next page">Next</a></li>
  {% else %}
    <li class="next disabled"><a>Next</a>
  {% endif %}
  </ul>
</div>


