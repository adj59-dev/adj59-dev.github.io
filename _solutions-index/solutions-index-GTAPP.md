---
layout: page
title: GTAPP Solutions Index
permalink: /solutions-index/GTAPP
description: "Index of notes and exercise solutions for Group Theory and Its Application to Physical Problems by Morton Hamermesh."
tags:
  - Group Theory and Its Application to Physical Problems
  - GTAPP
  - GTIAPP
  - Morton Hamermesh
  - Hamermesh
  - exercise solutions
  - textbook solutions
---

This page indexes my notes and exercise solutions for *Group Theory And Its Application To Physical Problems* by Morton Hamermesh. You can navigate by chapter or jump directly to the exercises I’ve completed. This index will be updated as I work through the book.

{%- assign qcqi_posts = site.categories["Group Theory and Its Application to Physical Problems"] | sort: "chapter" -%}
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
