---
layout: default
---

# Welcome to My Slate Theme Blog

This is the home page of my blog using the Slate theme on GitHub Pages.

## Recent Posts

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url | relative_url }})
  {{ post.excerpt }}
{% endfor %}
