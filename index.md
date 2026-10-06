---
layout: default
title: Home
---
<ul class="post-list">
{% for post in site.posts %}
  <li>
    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
    <p class="post-meta">
      <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %-d, %Y" }}</time>
      {% if post.tags and post.tags.size > 0 %}
      · {% for tag in post.tags %}<a class="tag" href="{{ '/tags/' | relative_url }}#{{ tag | slugify }}">#{{ tag }}</a>{% unless forloop.last %} {% endunless %}{% endfor %}
      {% endif %}
    </p>
    <p>{{ post.excerpt | strip_html | truncate: 160 }}</p>
  </li>
{% endfor %}
</ul>
