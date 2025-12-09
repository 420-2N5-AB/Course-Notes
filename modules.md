---
layout: default
title: Course Modules
permalink: /modules/
---

# Course Modules

Browse through the different modules of the Networking course:

<div class="module-list">
{% for module in site.modules %}
  <div class="module-item">
    <h2><a href="{{ module.url | relative_url }}">{{ module.title }}</a></h2>
    <p class="module-meta">Module {{ module.module_number }}</p>
    <p>{{ module.description }}</p>
  </div>
{% endfor %}
</div>

*New modules are added regularly as the course progresses.*
