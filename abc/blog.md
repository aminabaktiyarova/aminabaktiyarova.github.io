---
layout: page
nav: abc
permalink: /abc/blog/
eyebrow: "AB:C"
title: "Blog"
lede: "Articles, essays, posts, all in one place."
description: "Posts on language learning, living abroad, and studies, from Amina Baktiyarova."
---

<ul class="tag-row">
  <li><a class="tag" href="{{ '/abc/blog/languages/' | relative_url }}">Languages</a></li>
  <li><a class="tag" href="{{ '/abc/blog/studies/' | relative_url }}">Studies</a></li>
  <li><a class="tag" href="{{ '/abc/blog/research/' | relative_url }}">Research</a></li>
</ul>

{% if site.posts.size > 0 %}
<ul class="post-list">
  {% for post in site.posts %}
  <li>
    <p class="post-meta">{{ post.date | date: "%-d %B %Y" }}{% if post.tags.first %} &middot; {{ post.tags.first }}{% endif %}</p>
    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
    <p>{% if post.lede %}{{ post.lede }}{% else %}{{ post.excerpt | strip_html | truncate: 180 }}{% endif %}</p>
  </li>
  {% endfor %}
</ul>
{% else %}
<p class="note">Nothing published here yet. Follow the Telegram channel to know when the first post is up.</p>
{% endif %}
