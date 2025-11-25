---
layout: page
title: Blog Archive
---

<h1>Blog Archive</h1>

{% for category in site.categories %}
  <h2>{{ category[0] }}</h2>
  <ul>
    {% assign posts = category[1] | sort: "date" | reverse %}
    {% for post in posts %}
      <li>
        {{ post.date | date: "%B %Y" }} – 
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </li>
    {% endfor %}
  </ul>
{% endfor %}
