---
layout: default
title: "Home"
description: "The official blog of Rin."
keywords:
 - LevelRin
 - software development blog
 - programming blog
pagination:
  enabled: true
---

{% for post in paginator.posts %}
  <h2><a class="text-dark" href="{{ post.url }}">{{ post.title }}</a></h1>
  <div>
    {% assign right_margin = "mr-2" %}
    {% assign text_color = "text-secondary" %}
    <time class="{{ text_color }}">{{ post.created | date: "%b %d, %Y" }}</time>
    <span>&middot;</span>
    {% capture words %}
      {{ post.content | number_of_words | minus: 180 }}
    {% endcapture %}
    {% if words contains '-' %}
      <span class="{{ right_margin }} {{ text_color }}">1 min read</span>
    {% else %}
      <span class="{{ right_margin }} {{ text_color }}">{{ words | plus: 180 | divided_by: 180 | append: ' min read' }}</span>
    {% endif %}
    <svg class="bi bi-chat" width="1em" height="1em" viewBox="0 0 16 16" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
      <path fill-rule="evenodd" d="M2.678 11.894a1 1 0 0 1 .287.801 10.97 10.97 0 0 1-.398 2c1.395-.323 2.247-.697 2.634-.893a1 1 0 0 1 .71-.074A8.06 8.06 0 0 0 8 14c3.996 0 7-2.807 7-6 0-3.192-3.004-6-7-6S1 4.808 1 8c0 1.468.617 2.83 1.678 3.894zm-.493 3.905a21.682 21.682 0 0 1-.713.129c-.2.032-.352-.176-.273-.362a9.68 9.68 0 0 0 .244-.637l.003-.01c.248-.72.45-1.548.524-2.319C.743 11.37 0 9.76 0 8c0-3.866 3.582-7 8-7s8 3.134 8 7-3.582 7-8 7a9.06 9.06 0 0 1-2.347-.306c-.52.263-1.639.742-3.468 1.105z"/>
    </svg>
    <a class="{{ right_margin }} {{ text_color }}" href="{{ post.url | absolute_url }}#disqus_thread"></a>
  </div>
  <div>
    {% for tag in post.tags %}
      <a href="/tag/{{ tag }}">#{{ tag }}</a>
    {% endfor %}
  </div>
  {{ post.excerpt }}
  <a class="text-secondary" href="{{ post.url }}">Read more</a>
  <div class="mt-5"></div>
{% endfor %}


<!-- pagination -->
{% if paginator.total_pages > 1 %}
  <nav aria-label="page navigation for the blog">
    <ul class="pagination justify-content-center">
      {% if paginator.previous_page %}
        <li class="page-item">
          <a class="page-link" href="{{ paginator.first_page_path | prepend: site.baseurl }}">&laquo;</a>
        </li>
        <li class="page-item">
          <a class="page-link" href="{{ paginator.previous_page_path | prepend: site.baseurl }}">&lsaquo;</a>
        </li>
      {% else %}
        <li class="page-item disabled">
          <a class="page-link" href="#" tabindex="-1">&laquo;</a>
        </li>
        <li class="page-item disabled">
          <a class="page-link" href="#" tabindex="-1">&lsaquo;</a>
        </li>
      {% endif %}
      {% if paginator.page_trail %}
        {% for trail in paginator.page_trail %}
          <li {% if page.url == trail.path %}class="page-item active"{% endif %}>
              <a href="{{ trail.path | prepend: site.baseurl }}" title="{{trail.title}}" class="page-link">{{ trail.num }}</a>
          </li>
        {% endfor %}
      {% endif %}
      {% if paginator.next_page %}
        <li class="page-item">
          <a class="page-link" href="{{ paginator.next_page_path | prepend: site.baseurl }}">&rsaquo;</a>
        </li>
        <li class="page-item">
          <a class="page-link" href="{{ paginator.last_page_path | prepend: site.baseurl }}">&raquo;</a>
        </li>
      {% else %}
        <li class="page-item disabled">
          <a class="page-link" href="#" tabindex="-1">&rsaquo;</a>
        </li>
        <li class="page-item disabled">
          <a class="page-link" href="#" tabindex="-1">&raquo;</a>
        </li>
      {% endif %}
    </ul>
  </nav>
{% endif %}

<script id="dsq-count-scr" src="//levelrin.disqus.com/count.js" async></script>
