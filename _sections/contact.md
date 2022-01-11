---
title: titles.contact
short_title: short_titles.contact
---

{% capture header %}
<i class="fas fa-at mr-2"></i>{% t contact.email %}
{% endcapture %}
{% capture content %}
<p><a href="mailto:{% t global.email %}">{% t global.email %}</a></p>
{% endcapture %}

{% include section_row.html header=header content=content %}

{% capture header %}
<i class="fas fa-door-open mr-2"></i>{% t contact.hours_header %}
{% endcapture %}
{% capture hours %}
{% t contact.office_hours %}
{% endcapture %}
{% capture content %}
{{ hours | markdownify }}
{% endcapture %}

{% include section_row.html header=header content=content %}

{% capture header %}
<i class="fas fa-phone mr-2"></i>{% t contact.phone %}
{% endcapture %}
{% capture content %}<p>{% t global.phone %}</p>{% endcapture %}
{% include section_row.html header=header content=content %}

{% capture header %}
<i class="fas fa-fax mr-2"></i>{% t contact.fax %}
{% endcapture %}
{% capture content %}<p>{% t global.fax %}</p>{% endcapture %}

{% include section_row.html header=header content=content %}

{% capture header %}
<i class="fas fa-envelope-open-text mr-2"></i>{% t contact.postal_header %}
{% endcapture %}
{% capture postal %}{% t contact.postal_address %}{% endcapture %}
{% capture content %}<p>{{ postal | newline_to_br }}</p>{% endcapture %}

{% include section_row.html header=header content=content %}

{% capture header %}
<i class="fas fa-map-marker-alt mr-2"></i>{% t contact.office_header %}
{% endcapture %}
{% capture office %}{% t contact.office_address %}{% endcapture %}
{% capture content %}<p>{{ office | newline_to_br }}</p>{% endcapture %}

{% include section_row.html header=header content=content %}
