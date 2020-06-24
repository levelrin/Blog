---
layout: default
title: "All"
permalink: /all.html
created: 2020-06-16
description: "This page shows all tags and contents of the blog."
---

There are {{ site.tags.size }} tags and {{ site.posts.size }} posts so far.

All tags:
{% for tag in site.tags %}
  * [{{ tag[0] }}](/tag/{{ tag[0] }})
{% endfor %}

All posts:
{% for post in site.posts %}
  * [{{ post.title }}]({{ post.url }})
    * {{ page.created | date: "%-d %B %Y" }}
{% endfor %}
