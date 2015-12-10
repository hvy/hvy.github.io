---
layout: page
title: Archive
---

{% for post in site.posts %}
  {{ post.date | date_to_string }} [ {{ post.title }} ]({{ post.url }})
  {% if post.tags.size > 0 %}
    Keywords:
    {% for post_tag in post.tags %}
      {{post_tag}} &nbsp;
    {% endfor %}
  {% endif %}
{% endfor %}
