---
layout: default
title: "Home"
description: "The official blog of Rin."
keywords:
 - LevelRin
 - software development blog
 - programming blog
---

<ul>
  {% for post in site.posts %}
    <li>
      <h1><a href="{{ post.url }}">{{ post.title }}</a></h1>
      <ul>
        <li>{{ post.created }}</li>
        <li>{{ post.content | number_of_words }} words</li>
        <li>
          {% capture words %}
            {{ post.content | number_of_words | minus: 180 }}
          {% endcapture %}
          {% if words contains '-' %}
            less than a minute to read
          {% else %}
            {{ words | plus: 180 | divided_by: 180 | append: ' minutes to read' }}
          {% endif %}
        </li>
      </ul>
    </li>
  {% endfor %}
</ul>
