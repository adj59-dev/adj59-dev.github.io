---
layout: page
title: FPOL Solutions Index
permalink: /solutions-index/FPOL
description: "Index of notes and exercise solutions for Nielsen & Chuang's Quantum Computation and Quantum Information."
tags:
  - FPOL
  - FPOL solutions
  - Mack
  - Mack solutions
  - Lithography
  - Optical Lithography
  - problem solutions
  - textbook solutions
---

This page indexes my notes and problem solutions for Chris Mack’s *Fundamental Principles of Optical Lithography*. You can navigate by chapter or jump directly to the exercises I’ve completed. This index will be updated as I work through the book.

{%- assign qcqi_posts = site.categories["Fundamental Principles of Optical Lithography"] | sort: "chapter" -%}
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
