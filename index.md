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
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
