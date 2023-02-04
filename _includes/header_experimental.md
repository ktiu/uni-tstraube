<nav class="navbar navbar-expand-lg bg-primary navbar-dark sticky-top">
  <div class="container">
    <button class="order-1 navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <h1 class="me-auto order-2">
      <a class="{% if page.name == "index.md" %}nav-fadex {% endif %}navbar-brand" href="{% unless page.name == "index.md" %}{{ site.baseurl }}/{% endunless %}#">{{ site.title }}</a>
    </h1>
    <ul class="navbar-nav ms-auto mb-0 order-4">
      <li class="nav-item dropdown">
        <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false"><i class="fa fa-language fa-lg mx-2"></i>{{ site.lang  }}</a>
        <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
        {% if site.lang=="de" %}
          <li><a class="dropdown-item" href="{{ site.baseurl_root }}/">English</a></li>
          <li><span class="dropdown-item">Deutsch<i class="fas fa-check ms-2"></i></span></li>
        {% else %}
          <li><span class="dropdown-item">English<i class="fas fa-check ms-2"></i></span></li>
          <li><a class="dropdown-item" href="{{ site.baseurl_root }}/de/">Deutsch</a></li>
        {% endif %}
        </ul>
      </li>
    </ul>
    <div class="collapse navbar-collapse order-md-3 order-5" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="#">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Link</a>
        </li>
        <li class="nav-item">
          <a class="nav-link disabled">Disabled</a>
        </li>
      </ul>
    </div>
  </div>
</nav>
