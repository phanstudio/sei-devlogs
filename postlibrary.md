---
layout: default
title: Posts
permalink: /posts/
---

<section class="posts-section">
  <header>
    <h1>Welcome to the Sei Devlog!</h1>
    <h2>Post Library</h2>
    <p>Stay updated with my latest insights! Below are my most recent posts:</p>
  </header>

  <div class="post-cards-container">
    {% if site.posts.size > 0 %}
      {% for post in site.posts %}
        <div class="post-card">
          <article>
            <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
            <p>{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
            <a class="read-more" href="{{ post.url | relative_url }}">Read more</a>
          </article>
        </div>
      {% endfor %}
    {% else %}
      <p class="no-posts">No posts available yet. Check back soon!</p>
    {% endif %}
  </div>
</section>
