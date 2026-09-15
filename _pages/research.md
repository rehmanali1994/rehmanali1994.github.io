---
layout: page
title: Research
permalink: /research/
description: Research Statement & Computational Ultrasound Imaging Research Projects.
nav: true
nav_order: 5
display_categories: [Pulse-Echo Ultrasound, Full-Waveform Inversion (FWI) for UST/USCT, Clinical Applications]
horizontal: false
---

## Research Statement Overview

My research focuses on developing computational ultrasound imaging techniques that treat image formation and reconstruction as inverse problems rooted in wave physics.  My work spans <ins>***conventional pulse-echo ultrasound***</ins> and an emerging modality known as <ins>***ultrasound [computed] tomography (UST/USCT)***</ins>, which records the transmission of ultrasound through tissue.  Clinical applications include breast cancer screening, point-of-care assessment of acute neurological conditions, and quantitative imaging of the liver.  

### ***[Download my complete Research Statement for more details.](/assets/pdf/ResearchStatement.pdf)***


<!-- pages/research.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
