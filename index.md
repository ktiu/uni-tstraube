---
layout: long_page
hide_brand: true
---

{% include masthead.md %}

{% for section in site.sections %}

<section id="{{ section.slug }}">
  <div class="section-header d-flex flex-row align-items-baseline justify-content-between">
  <h2>{% t section.title %}</h2>
  <div><a href="#"><i class="fas fa-angle-up"></i></a></div>
  </div>
  {{ section.content }}
</section>

{% endfor %}

