---
layout: page
title: Alex's Blog
permalink: /
---


This blog documents my learning journey through quantum computing, mathematics, and engineering topics.

## Posts

<ul class="post-list">
  {% for post in site.posts %}
    <li class="post-list-item">

      <h4 class="post-title">
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h4>

      {% if post.description %}
        <p class="post-description">
          {{ post.description }}
        </p>
      {% else %}
        <p class="post-description">
          {{ post.excerpt | strip_html | truncate: 180 }}
        </p>
      {% endif %}
      
      <p class="post-meta">
        {{ post.date | date: "%B %-d, %Y" }}
      </p>

    </li>
  {% endfor %}
</ul>
