---
layout: page
title: QCQI Solutions Index
permalink: /solutions-index/
description: "Index of notes and exercise solutions for Nielsen & Chuang's Quantum Computation and Quantum Information."
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

This page indexes my notes and exercise solutions for Nielsen & Chuang’s *Quantum Computation and Quantum Information*. You can navigate by chapter or jump directly to the exercises I’ve completed. Solutions on each chapter page are collapsed by default—click "Click to view the solution” to expand them. This index will be updated as I work through the book.

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
  <div class="exercise-columns">
    <ul>
      {% for ex in post.exercises %}
      <li>
        <a href="{{ post.url | relative_url }}#{{ ex.anchor }}">{{ ex.label }}</a>
      </li>
      {% endfor %}
    </ul>
  </div>
  {% else %}
  <br><em>No solutions listed.</em>
  {% endif %}
</li>

  {% endif %}
{% endfor %}

</ul>

