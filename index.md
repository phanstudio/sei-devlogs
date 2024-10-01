---
layout: default
---

# Welcome to My Slate Theme Blog

This is the home page of my blog using the Slate theme on GitHub Pages.

## Recent Posts

<ul>
  {% for post in site.posts %}
    <li>
      <p><a href="{{ post.url | relative_url }}">{{ post.title }}</a></p>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
