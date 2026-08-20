---
layout: page
nav: abc
permalink: /abc/blog/research/
eyebrow: "AB:C blog"
title: "Research"
lede: "How to find a research project, work with an advisor, and get it into a real application."
description: "Posts on finding a research topic, working with an advisor, and building a research project for your application, from Amina Baktiyarova."
---

<ul class="tag-row">
  <li><a class="tag" href="{{ '/abc/blog/' | relative_url }}">All posts</a></li>
  <li><a class="tag" href="{{ '/abc/blog/languages/' | relative_url }}">Languages</a></li>
  <li><a class="tag" href="{{ '/abc/blog/studies/' | relative_url }}">Studies</a></li>
  <li><a class="tag" href="{{ '/abc/blog/research/' | relative_url }}" aria-current="page">Research</a></li>
</ul>

{% assign tagged = site.tags['research'] %}
{% if tagged and tagged.size > 0 %}
<ul class="post-list">
  {% for post in tagged %}
  <li>
    <p class="post-meta">{{ post.date | date: "%-d %B %Y" }}</p>
    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
    <p>{% if post.lede %}{{ post.lede }}{% else %}{{ post.excerpt | strip_html | truncate: 180 }}{% endif %}</p>
  </li>
  {% endfor %}
</ul>
{% else %}
<p class="note">Nothing published here yet. Follow the Telegram channel to know when the first post is up.</p>
{% endif %}
