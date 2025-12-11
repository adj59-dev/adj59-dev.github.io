---
layout: page
title: Blog Archive
---

This archive organizes my notes and solution write-ups by book. Each section collects all posts related to a specific text, listed in chronological order as I work through each chapter.

{% for category in site.categories %}
  <h2>{{ category[0] }}</h2>
  <ul>
    {% assign posts = category[1] | sort: "date"  %}
    {% for post in posts %}
      <li>
        {{ post.date | date: "%b %Y" }} – 
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </li>
    {% endfor %}
  </ul>
{% endfor %}
