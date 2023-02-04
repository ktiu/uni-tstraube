---
title: titles.publications
short_title: short_titles.publications
---

{% assign sorted = site.data.publications | sort: 'date' | reverse %}
{% assign i = 0 %}
{% assign year = "" %}

{% for publication in sorted %}

{% assign i = i | plus: 1 %}
{% if i == 6 %}
  <div class="collapse publications-expand">
{% endif %}

{% assign this_year = publication.date | date: '%Y' %}

{% capture header %}
  {% if year != this_year %} {{ this_year }} {% endif %}
{% endcapture %}

{% assign year = this_year %}

{% capture show_date %}
{% if publication.type == "submitted" %}
{% t publications.submitted %}
{% else %}
{{ this_year }}
{% endif %}
{% endcapture %}

{% assign first_author = publication.authors | first %}
{% assign author_count = publication.authors | size %}
{% assign all_but_last = author_count | minus: 2 %}
{% assign last_author = publication.authors | last %}
{% assign middle_authors = publication.authors | slice: 1, all_but_last %}

{% capture authors %}
{{ first_author.last_name }}, {{first_author.first_name}}{% for author in middle_authors %},
{{ author.first_name }} {{ author.last_name }}{% endfor %}
{% if author_count > 1 %}
{% t publications.and %} {{ last_author.first_name }} {{ last_author.last_name }}
{% endif %}
{% endcapture %}

{% assign first_editor = publication.editors | first %}
{% assign editor_count = publication.editors | size %}
{% assign all_but_last = editor_count | minus: 2 %}
{% assign last_editor = publication.editors | last %}
{% assign middle_editors = publication.editors | slice: 1, all_but_last %}

{% capture editors %}
{{ first_editor.first_name }} {{first_editor.last_name}}{% for editor in middle_editors %},
{{ editor.first_name }} {{ editor.last_name }}{% endfor %}
{% if editor_count > 1 %}
{% t publications.and %} {{ last_editor.first_name }} {{ last_editor.last_name }}
{% endif %}
({% t publications.editors %})
{% endcapture %}

{% capture published %}
{% if publication.type == "article" %}
  <em>{{ publication.journal }}{% if publication.issue %}
  {{ publication.issue }}{% endif %}{% if publication.volume %}
  ({{ publication.volume }}){% endif %}</em>{% if publication.pages %},
  {{ publication.pages | join: '–' }}{% endif %}.
{% elsif publication.type == "chapter" %}
  {% t publications.in %}:
  {% if editors %}{{ editors | strip  }}.{% endif %}
  <em>{% if publication.in_title %} {{ publication.in_title | strip }}{% endif %}{% if publication.in_subtitle %}.
  {{ publication.in_subtitle }}{% endif %}</em>{% if publication.in_place %}.
  {{ publication.in_place }}{% endif %}{% if publication.in_publisher %}: 
  {{ publication.in_publisher }}{% endif %}{% if publication.pages %},
  {{ publication.pages | join: '–' }}{% endif %}.
{% elsif publication.type == "book" %}
  {% if publication.format %}{{ publication.format }}{% endif %}{% if publication.place %}.
  {{ publication.place }}{% endif %}{% if publication.publisher %}: 
  {{ publication.publisher }}{% endif %}.
{% endif %}
{% endcapture %}

{% capture content %}
<p>
{{ authors | strip }}. {{ show_date | strip }}.<strong>{% if publication.title %}<br />
{{ publication.title }}{% endif %}{% if publication.subtitle %}.
{{ publication.subtitle }}{% endif %}.</strong><br />
{% if publication.type != "submitted" %}
{{ published }}<br />
{% endif %}
{% for link in publication.links %}
  {% if link.type == "pdf" %}
    {% assign text = "<i class='fas fa-file-pdf me-2'></i>PDF" %}
    {% assign url = link.url | relative_url %}
  {% elsif link.type == "publisher" %}
    {% capture publisher %}{% t publications.publisher %}{% endcapture %}
    {% assign text = "<i class='fas fa-link me-2'></i>" | append: publisher %}
    {% assign url = link.url %}
  {% elsif link.type == "doi" %}
    {% assign text = "<i class='ai ai-doi me-2'></i>" | append: "DOI" %}
    {% capture url %}
    https://doi.org/{{ link.url }}
    {% endcapture %}
  {% else %}
    {% assign text = "Link" %}
    {% assign url = link.url %}
  {% endif %}
  <a class="btn btn-sm btn-outline-primary mt-1" href="{{ url | strip }}">{{ text }}</a>
{% endfor %}
</p>
{% endcapture %}

{% include section_row.html header=header content=content %}

{% endfor %}

{% if i > 5 %}
  </div>
  <button class="btn btn-secondary collapsed show-more" type="button" data-bs-toggle="collapse" data-bs-target=".publications-expand">
    <span class="if-collapsed">{% t publications.show_all %}<i class="fas fa-caret-down ms-2"></i></span>
    <span class="if-not-collapsed">{% t publications.show_less %}<i class="fas fa-caret-up ms-2"></i></span>
  </button>
{% endif %}
