---
layout: page
permalink: /repositories/
title: Repositories
description: A selection of research software and computational methods.
nav: true
nav_order: 5
---



{% if site.data.repositories.github_users %}

## GitHub users

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for user in site.data.repositories.github_users %}
    {% include repository/repo_user.liquid username=user %}
  {% endfor %}
</div>

---

{% if site.repo_trophies.enabled %}
{% for user in site.data.repositories.github_users %}
{% if site.data.repositories.github_users.size > 1 %}

  <h4>{{ user }}</h4>
  {% endif %}
  <div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% include repository/repo_trophies.liquid username=user %}
  </div>

---

{% endfor %}
{% endif %}
{% endif %}



{% for group in site.data.repositories.repository_groups %}

## {{ group.title }}

{{ group.description }}

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">

{% for repo in group.repos %}
  {% include repository/repo.liquid repository=repo %}
{% endfor %}

</div>

{% endfor %}
