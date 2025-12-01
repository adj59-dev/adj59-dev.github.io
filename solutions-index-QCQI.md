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

{%- comment -%}
1. Get all posts that belong to QCQI (based on category).
   Each relevant post should have:
   - category: Quantum Computation and Quantum Information
   - chapter: <number>  (e.g., 5)
{%- endcomment -%}
{%- assign qcqi_posts = site.categories["Quantum Computation and Quantum Information"] -%}

{%- comment -%}
2. Loop over chapter numbers in order.
   Adjust 1..12 if you add more chapters later.
{%- endcomment -%}
{% for ch in (1..12) %}
  {%- assign chapter_posts = qcqi_posts | where: "chapter", ch | sort: "date" -%}
  {%- if chapter_posts.size > 0 -%}

    <h2>Chapter {{ ch }}</h2>

    {%- comment -%}
    List all posts for this chapter.
    {%- endcomment -%}
    {% for post in chapter_posts %}
  - 📄 **[{{ post.title }}]({{ post.url | relative_url }})**

    {% if post.exercises %}
    <br>
    **Solutions**
    <ul>
      {% for ex in post.exercises %}
        <li>
          <a href="{{ post.url | relative_url }}#{{ ex.anchor }}">
            {{ ex.label }}
          </a>
        </li>
      {% endfor %}
    </ul>
    {% else %}
      <br><em>No solutions listed.</em>
    {% endif %}
    {% endfor %}

  {% endif %}
{% endfor %}
