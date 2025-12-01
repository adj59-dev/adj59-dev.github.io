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
{%- endcomment -%}
{%- assign qcqi_posts = site.categories["Quantum Computation and Quantum Information"] -%}

{%- comment -%}
2. Collect all chapter numbers from posts that define `chapter`.
{%- endcomment -%}
{%- assign chapters = "" | split: "" -%}

{% for post in qcqi_posts %}
  {% if post.chapter %}
    {% assign chapters = chapters | push: post.chapter %}
  {% endif %}
{% endfor %}

{%- comment -%}
3. Remove duplicates and sort numerically.
{%- endcomment -%}
{%- assign chapters = chapters | uniq | sort -%}

---

{%- comment -%}
4. Render each chapter section.
{%- endcomment -%}

{% for chapter_number in chapters %}
  <h2>Chapter {{ chapter_number }}</h2>

  {%- comment -%}
  Get the post(s) associated with this chapter.
  Typically there is one post per chapter, but this supports more.
  {%- endcomment -%}
  {% assign chapter_posts = qcqi_posts | where: "chapter", chapter_number | sort: "date" %}

  {% for post in chapter_posts %}
  - 📄 **[Notes & Solutions for Chapter {{ chapter_number }}]({{ post.url | relative_url }})**

    {% if post.exercises %}
    <br>
    **Solutions**
    <ul>
      {% for ex in post.exercises %}
        {%- comment -%}
        ex.label → "Exercise 4.6"
        ex.anchor → "exercise-4-6"
        {%- endcomment -%}
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

{% endfor %}
