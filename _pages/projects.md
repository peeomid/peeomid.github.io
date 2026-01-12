---
layout: single
permalink: /projects/
title: Projects
author_profile: false
---

## Fun projects

{% if site.projects %}
{% for project in site.projects %}
- **[{{ project.title }}]({{ project.url | relative_url }})** - {{ project.excerpt | strip_html | strip_newlines }}
{% endfor %}
{% endif %}
