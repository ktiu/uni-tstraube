---
layout: default
hide_brand: true
---

{% for section in site.sections %}

<section id="{{ section.slug }}" class="row my-4">
  <div class="col-sm-3 text-muted">
    <h2>{% t section.title %}</h2>
  </div>
  <div class="col">
    {{ section.content }}
  </div>
</section>

{% endfor %}
