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
  <div class="collapse teaching-expand">
{% endif %}

{% assign this_year = publication.date | date: '%Y' %}

{% capture header %}
  {% if year != this_year %} {{ this_year }} {% endif %}
{% endcapture %}

{% assign year = this_year %}

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
{% endif %}
{% endcapture %}

{% capture content %}
<p>
{{ authors | strip }}. {{ this_year }}.<strong>{% if publication.title %}<br />
{{ publication.title }}{% endif %}{% if publication.subtitle %}.
{{ publication.subtitle }}{% endif %}.</strong><br />
{{ published }}<br />
{% for link in publication.links %}
  {% if link.type == "pdf" %}
    {% assign text = "<i class='fas fa-file-pdf mr-2'></i>PDF" %}
    {% assign url = link.url | relative_url %}
  {% elsif link.type == "publisher" %}
    {% capture publisher %}{% t publications.publisher %}{% endcapture %}
    {% assign text = "<i class='fas fa-link mr-2'></i>" | append: publisher %}
    {% assign url = link.url %}
  {% else %}
    {% assign text = "Link" %}
    {% assign url = link.url %}
  {% endif %}
  <a class="btn btn-sm btn-outline-primary mt-1" href="{{ url }}">{{ text }}</a>
{% endfor %}
</p>
{% endcapture %}

{% include section_row.html header=header content=content %}

{% endfor %}

{% if i > 5 %}
  </div>
  <button class="btn btn-primary form-control" type="button" data-toggle="collapse" data-target=".teaching-expand">Show all</button>
{% endif %}
