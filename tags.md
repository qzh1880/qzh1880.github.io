---
layout: page
title: Tags
permalink: /tags/
---

<!-- 1. 顶部所有标签的云/列表 -->
<p>
  {% assign sorted_tags = site.tags | sort %}
  {% for tag in sorted_tags %}
    <a href="#{{ tag[0] | slugify }}">#{{ tag[0] }} ({{ tag[1].size }})</a>{% unless forloop.last %} &nbsp; {% endunless %}
  {% endfor %}
</p>

<hr>

<!-- 2. 按标签分组的文章列表 -->
{% for tag in sorted_tags %}
  <h2 id="{{ tag[0] | slugify }}">{{ tag[0] }}</h2>
  <ul>
    {% for post in tag[1] %}
      <li>
        <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span> — 
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </li>
    {% endfor %}
  </ul>
{% endfor %}