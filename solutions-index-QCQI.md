---
layout: page
title: QCQI Solutions Index
permalink: /solutions-index/
description: "Complete index of notes and exercise solutions for Nielsen & Chuang's Quantum Computation and Quantum Information."
tags:
  - QCQI
  - QCQI solutions
  - Nielsen & Chuang
  - Nielsen & Chuang solutions
  - Nielsen Chuang solutions
  - quantum computing
  - quantum information
  - exercise solutions
  - textbook solutions
---

# QCQI Solutions Index

{%- assign qcqi_posts = site.categories["Quantum Computation and Quantum Information"] | sort: "chapter" -%}
{%- assign current_chapter = nil -%}

{% for post in qcqi_posts %}
  {% if post.chapter %}
    {% if post.chapter != current_chapter %}
      {% unless forloop.first %}
</ul>
      {% endunless %}

<h2>Chapter {{ post.chapter }}</h2>

<ul>
      {% assign current_chapter = post.chapter %}
    {% endif %}

<li>
  📄 <strong><a href="{{ post.url | relative_url }}">{{ post.title }}</a></strong>

  {% if post.exercises %}
  <br>
  <strong>Solutions</strong>
  <ul>
    {% for ex in post.exercises %}
    <li>
      <a href="{{ post.url | relative_url }}#{{ ex.anchor }}">{{ ex.label }}</a>
    </li>
    {% endfor %}
  </ul>
  {% else %}
  <br><em>No solutions listed.</em>
  {% endif %}
</li>

  {% endif %}
{% endfor %}

</ul>

