---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: page
redirect_from: "/projects"
---

This is my personal site with information on various projects I'm working, I'll probably eventually set up some kind of tech blog here as well.

## Projects

{% if site.projects.size > 0 %}
<!-- <h2 class="post-list-heading">{{ page.list_title | default: "Projects" }}</h2> -->
{% assign projects = site.projects | sort: 'order' %}
<ul class="post-list">
  {% for project in projects %}
  <li>
    <h3>
      <a class="post-link" href="{{ project.url | relative_url }}">
        {{ project.title | escape }}
      </a>
    </h3>
    {% if site.show_excerpts %}
      {{ project.excerpt }}
      <a href="{{ project.url | relative_url }}">Read more...</a>
    {% endif %}
  </li>
  {% endfor %}
</ul>

{% endif %}

