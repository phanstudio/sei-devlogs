---
layout: home
title: Welcome to My Blog
---

# Welcome to My Blog

This is the home page of my simple blog created with GitHub Pages.

## Recent Posts

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}
