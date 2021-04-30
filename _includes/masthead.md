<div class="masthead d-flex flex-column justify-around text-center">
  <h1>{{ site.title }}</h1>
  <div class="d-md-flex my-3 flex-row align-items-stretch justify-content-center">
    <div class="menu d-flex flex-md-column flex-wrap justify-content-center text-md-right px-md-3 py-2">
    {% for section in site.sections %}
      <a href="#{{ section.slug }}" class="mx-2">
        {% t section.short_title %}
      </a>
    {% endfor %}
    </div>
    <div class="text-md-left">
      <div class="my-2 mx-md-4">
        {% tf affiliation.md %}
      </div>
      <div class="d-flex flex-wrap align-items-center justify-content-center justify-content-md-start mx-md-3">
        <img src="{{ "/assets/img/gu.png" | prepend: site.baseurl_root }}" height="50px" class="mx-2 my-2" alt="Goethe-Universität Frankfurt" />
        <img src="{{ "/assets/img/ihg.svg" | prepend: site.baseurl_root }}" height="40px" class="mx-2 my-2" alt="Institut für Humangeographie" />
      </div>
    </div>
  </div>
  <!-- div class="text-center icons mt-4">
  {% include icons.html %}
  </div// -->
</div>
