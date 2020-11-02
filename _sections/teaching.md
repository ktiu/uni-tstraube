---
title: titles.teaching
---

{% assign term="" %}
{% assign sorted = site.data.classes | reverse %}
{% for class in sorted %}

{% if class.term != term %}
{% assign term = class.term %}
<h3>{{ class.term }}</h3>
{%endif %}

**{{ class.title }}**  
*{{ class.module}}*

{% endfor %}

