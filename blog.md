---
layout: homepage
title: Blog
permalink: /blog/
description: Blog posts by Masoud Jafaripour.
---

<h2 id="blog">Blog</h2>

{%- comment %} Posts go in _posts/ as YYYY-MM-DD-title.md and are listed here, newest first. {% endcomment %}
{% if site.posts.size > 0 %}
<ul class="blog-list">
  {%- for post in site.posts %}
  <li><span class="blog-date">{{ post.date | date: "%b %-d, %Y" }}</span> <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
  {%- endfor %}
</ul>
{% else %}
<p class="blog-empty">No posts yet. Check back soon.</p>
{% endif %}
