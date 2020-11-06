---
title: titles.teaching
short_title: short_titles.teaching
---

{% assign i = 0 %}
{% assign term = "" %}
{% assign sorted = site.data.classes | reverse %}
{% for class in sorted %}
{% assign i = i | plus: 1 %}
{% if i == 6 %}
  <div class="collapse teaching-expand">
{% endif %}
{% capture header %}
  {% if class.term != term %}
    {% assign length = class.term | downcase | size %}
    {% if length > 4 %}
      {% t teaching.winter %}
    {% else %}
      {% t teaching.summer %}
    {% endif %}
    {{ class.term }}
  {% endif %}
{% endcapture %}
{% assign term = class.term %}
{% capture content %}
<p>
<strong>{{ class.title }}</strong><br />
<i>{{ class.module }}</i><br>
{% for link in class.links %}
  {% if link.type == "syllabus" %}
    {% assign text = "<i class='fas fa-file-pdf mr-2'></i>Syllabus" %}
    {% assign url = link.url | prepend: site.doc_path | relative_url %}
  {% elsif link.type == "olat" %}
    {% assign text = "<i class='fas fa-graduation-cap mr-2'></i>OLAT" %}
    {% capture url %}
    https://olat-ce.server.uni-frankfurt.de/olat/auth/RepositoryEntry/{{ link.url }}/
    {% endcapture %}
  {% elsif link.type == "materials" %}
    {% capture text %}
    <i class='fas fa-graduation-cap mr-2'></i>{% t teaching.materials %}
    {% endcapture %}
    {% assign url = link.url | prepend: '/c/' | relative_url %}
  {% elsif link.type == "qis" %}
    {% capture text %}
    <i class='fas fa-university mr-2'></i>{% t teaching.qis %}
    {% endcapture %}
    {% capture url = link.url %}https://qis.server.uni-frankfurt.de/qisserver/rds?state=verpublish&publishid={{ link.url }}&moduleCall=webInfo&publishConfFile=webInfo&publishSubDir=veranstaltung
    {% endcapture %}
  {% else %}
    {% assign text = "<i class='fas fa-link mr-2'></i>Link" %}
    {% assign url = link.url %}
  {% endif %}
  <a class="btn btn-sm btn-outline-primary mt-1" href="{{ url | strip }}">{{ text | strip }}</a>
{% endfor %}
</p>
{% endcapture %}
{% include section_row.html class=div_class header=header content=content %}
{% endfor %}

{% if i > 5 %}
  </div>
  <button class="btn btn-primary form-control collapsed" type="button" data-toggle="collapse" data-target=".teaching-expand">
    <span class="if-collapsed">{% t teaching.show_all %}<i class="fas fa-caret-down ml-2"></i></span>
    <span class="if-not-collapsed">{% t teaching.show_less %}<i class="fas fa-caret-up ml-2"></i></span>
  </button>
{% endif %}
