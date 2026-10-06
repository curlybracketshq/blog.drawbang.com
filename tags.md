---
layout: default
title: Tags
permalink: /tags/
---
<h1>Tags</h1>
<div class="tag-cloud">
{% assign tags = site.tags | sort %}
{% for tag in tags %}
  <a class="tag" href="#{{ tag[0] | slugify }}">#{{ tag[0] }}</a>
{% endfor %}
</div>
{% for tag in tags %}
<div class="tag-section" id="{{ tag[0] | slugify }}">
  <h2>#{{ tag[0] }}</h2>
  <ul class="archive-list">
  {% for post in tag[1] %}
    <li><time>{{ post.date | date: "%b %-d, %Y" }}</time><a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
  {% endfor %}
  </ul>
</div>
{% endfor %}
