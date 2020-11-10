{% if include.index %}
<nav class="navbar navbar-light fixed-top navbar-expand-md">
  <div class="w-100 h-100 position-absolute nav-fade bg-light border-bottom" style="z-index:-1"></div>
{% else %}
<nav class="navbar navbar-light navbar-expand-md w-100 bg-light border-bottom"></div>
{% endif %}
  <div class="container z-index-1">
    <h1 class="mr-auto order-1">
      <a{% if include.index %} class="nav-fade"{% endif %} href="#">{{ site.title }}</a>
    </h1>
    <div class="{% if include.index %}nav-fade {% endif %} nav-menu order-3 order-md-2">
      <ul class="nav navbar-nav mb-0" id="menu">
{% for section in site.sections %}
{% capture uri %}
{% unless include.index %}{{ site.baseurl }}/{% endunless %}#{{section.slug}}
{% endcapture %}
        <li class="nav-item">
          <a class="nav-link" aria-current="page" href="{{ uri | strip }}">{% t section.short_title %}</a>
        </li>
{% endfor %}
      </ul>
    </div>
    <ul class="navbar-nav ml-auto mb-0 order-2 order-md-3">
      <li class="nav-item dropdown">
        <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-expanded="false"><i class="fa fa-language fa-lg mx-2"></i>{{ site.lang  }}</a>
        <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
        {% if site.lang=="de" %}
          <li><a class="dropdown-item" href="{{ site.baseurl_root }}/">English</a></li>
          <li><span class="dropdown-item">Deutsch<i class="fas fa-check ml-2"></i></span></li>
        {% else %}
          <li><span class="dropdown-item">English<i class="fas fa-check ml-2"></i></span></li>
          <li><a class="dropdown-item" href="{{ site.baseurl_root }}/de/">Deutsch</a></li>
        {% endif %}
        </ul>
      </li>
    </ul>
{% if include.index %}
  </div>
{% endif %}
</nav>
