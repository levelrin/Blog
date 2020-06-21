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
      </ul>
    </li>
  {% endfor %}
</ul>
