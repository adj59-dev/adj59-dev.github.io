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
{% assign qcqi_posts = site.categories["Quantum Computation and Quantum Information"] | sort: "date" %}

{%- comment -%}
2. Collect all chapter tags ("chapter 1", "chapter 2", etc.)
{%- endcomment -%}
{% assign chapter_tags = "" | split: "" %}

{% for post in qcqi_posts %}
  {% for tag in post.tags %}
    {% if tag contains "chapter " %}
      {% assign chapter_tags = chapter_tags | push: tag %}
    {% endif %}
  {% endfor %}
{% endfor %}

{%- comment -%}
3. Remove duplicates
{%- endcomment -%}
{% assign chapter_tags = chapter_tags | uniq %}

{%- comment -%}
4. Convert each chapter tag into an object so we can numerically sort them.
   Example:
   "chapter 5" → { "number": 5, "name": "chapter 5" }
{%- endcomment -%}

{% assign chapter_objects = "" | split: "" %}

{% for ch in chapter_tags %}
  {% assign num = ch | remove: "chapter " | plus: 0 %}
  {% assign obj = 
    "{ \"number\": " 
    | append: num
    | append: ", \"name\": \"" 
    | append: ch
    | append: "\" }" 
  %}
  {% assign chapter_objects = chapter_objects | push: obj %}
{% endfor %}

{%- comment -%}
5. Sort numerically by "number"
{%- endcomment -%}
{% assign chapter_objects = chapter_objects | sort: "number" %}

---

{%- comment -%}
6. Render each chapter section
{%- endcomment -%}

{% for c in chapter_objects %}
  {% assign chapter_name = c.name %}

  <h2>{{ chapter_name | capitalize }}</h2>

  {%- comment -%}
  Get the post(s) associated with this chapter tag.
  Typically there is one post per chapter, but this supports more.
  {%- endcomment -%}
  {% assign chapter_posts = qcqi_posts | where_exp: "p", "p.tags contains chapter_name" %}

  {% for post in chapter_posts %}
  - 📄 **[Notes & Solutions for {{ chapter_name | capitalize }}]({{ post.url | relative_url }})**

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

