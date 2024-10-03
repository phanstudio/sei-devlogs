---
layout: default
title: Posts
permalink: /posts/
---

# Welcome to the Sei Devlog!
# Post library

Stay updated with my latest insights! Below are my most recent posts:

<ul>
  {% for post in site.posts %}
    <li>
      <p><a href="{{ post.url | relative_url }}">{{ post.title }}</a></p>
      <p>{{post.extent limit=30}}</p>
    </li>
  {% endfor %}
</ul>
