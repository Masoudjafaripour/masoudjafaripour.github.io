---
layout: homepage
title: Blog
permalink: /blog/
description: Blog posts by Masoud Jafaripour.
---

<h2 id="blog">Blog</h2>

{%- comment %} Posts go in _posts/ (see _layouts/post.html) and are listed here, newest first. {% endcomment %}
{% if site.posts.size > 0 %}
<ul class="blog-list">
  {%- for post in site.posts %}
  <li>
    <a class="blog-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span class="blog-date">{{ post.date | date: "%B %-d, %Y" }}</span>
    {%- if post.description %}
    <p class="blog-desc">{{ post.description }}</p>
    {%- endif %}
  </li>
  {%- endfor %}
</ul>
{% else %}
<p class="blog-empty">No posts yet. Check back soon.</p>
{% endif %}
