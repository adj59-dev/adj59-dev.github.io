---
layout: page
title: Solutions Hub
permalink: /solutions-index/
description: "Landing page linking to all my textbook solution indices: QCQI, GTAPP, and future books."
tags:
  - solutions index
  - textbook solutions
  - QCQI
  - GTAPP
  - quantum computing
  - group theory
---

This page collects all of my solution indices for the textbooks I'm studying. Each index links to notes and worked exercises, written as I progress through the material. As I continue working through topics, this hub will grow to include new books and expanded solution sets.


{% assign grouped = site.solutions-index | group_by: "category" %}

{% for group in grouped %}
  <h2>{{ group.name }}</h2>
  <ul>
    {% assign items = group.items | sort: "title" %}
    {% for index in items %}
      <li>
        <a href="{{ index.url | relative_url }}">{{ index.title }}</a>
        {% if index.description %}
          <div class="index-description">{{ index.description }}</div>
        {% endif %}
      </li>
    {% endfor %}
  </ul>
{% endfor %}
