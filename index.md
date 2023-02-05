---
layout: page
masthead: true
---

{% for section in site.sections %}

<section id="{{ section.slug }}">
  <div class="section-header d-flex flex-row align-items-baseline justify-content-between justify-content-md-start">
  <div class="left-column order-2 order-md-1"><a href="#"><i class="fas fa-lg fa-angle-up"></i></a></div>
  <h2 class="order-1 order-md-2">{% t section.title %}</h2>
  </div>
  {{ section.content }}
</section>

{% endfor %}
