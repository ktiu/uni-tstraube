---
title: titles.contact
short_title: short_titles.contact
---

{% capture header %}
{% t contact.email %}
{% endcapture %}
{% capture content %}
<p><a href="mailto:{{ site.email }}">{{ site.email }}</a></p>
{% endcapture %}
{% include section_row.html header=header content=content %}

{% capture header %}
{% t contact.pronouns_header %}
{% endcapture %}
{% capture content %}<p>{% t contact.pronouns %}</p>{% endcapture %}
{% include section_row.html header=header content=content %}

{% capture header %}
{% t contact.hours_header %}
{% endcapture %}
{% capture hours %}
{% t contact.office_hours %}
{% endcapture %}
{% capture content %}
{{ hours | markdownify | strip | newline_to_br }}
{% endcapture %}
{% include section_row.html header=header content=content %}


{% capture header %}
{% t contact.phone %}
{% endcapture %}
{% capture content %}<p>{{ site.phone }}</p>{% endcapture %}
{% include section_row.html header=header content=content %}

{% capture header %}
{% t contact.fax %}
{% endcapture %}
{% capture content %}<p>{{ site.fax }}</p>{% endcapture %}
{% include section_row.html header=header content=content %}

{% capture header %}
{% t contact.postal_header %}
{% endcapture %}
{% capture postal %}{% t contact.postal_address %}{% endcapture %}
{% capture content %}<p>{{ postal | newline_to_br }}</p>{% endcapture %}

{% include section_row.html header=header content=content %}

{% capture header %}
{% t contact.office_header %}
{% endcapture %}
{% capture office %}{% t contact.office_address %}{% endcapture %}
{% capture content %}<p>{{ office | newline_to_br }}</p>{% endcapture %}

{% include section_row.html header=header content=content %}
