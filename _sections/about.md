---
title: titles.about
short_title: short_titles.about
---

{% capture header %}
{% t about.short_bio %}
{% endcapture %}

{% capture content %}
{% tf bio.md %}
{% endcapture %}

{% include section_row.html header=header content=content %}

{% capture header %}
{% t about.interests %}
{% endcapture %}

{% capture content %}
{% tf interests.md %}
{% endcapture %}

{% include section_row.html header=header content=content %}

{% capture header %}
{% t about.education %}
{% endcapture %}

{% capture content %}
{% tf education.md %}
{% endcapture %}

{% include section_row.html header=header content=content %}
