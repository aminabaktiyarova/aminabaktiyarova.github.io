---
layout: page
nav: abc
permalink: /abc/blog/languages/
eyebrow: "AB:C blog"
title: "Language learning"
lede: "Everything on IELTS, English, and other languages, in one place."
description: "Posts on language learning and exam prep, including IELTS, from Amina Baktiyarova."
---

<ul class="tag-row">
  <li><a class="tag" href="{{ '/abc/blog/' | relative_url }}">All posts</a></li>
  <li><a class="tag" href="{{ '/abc/blog/languages/' | relative_url }}" aria-current="page">Languages</a></li>
  <li><a class="tag" href="{{ '/abc/blog/studies/' | relative_url }}">Studies</a></li>
  <li><a class="tag" href="{{ '/abc/blog/research/' | relative_url }}">Research</a></li>
</ul>

{% assign tagged = site.tags['languages'] %}
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
