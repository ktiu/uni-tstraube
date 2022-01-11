---
layout: long_page
hide_brand: true
---


{% include masthead.md %}

{% for section in site.sections %}

<section id="{{ section.slug }}">
  <div class="section-header d-flex flex-row align-items-baseline justify-content-between">
  <h2>{% t section.title %}</h2>
  <div><a href="#"><i class="fas fa-angle-up"></i></a></div>
  </div>
  {{ section.content }}
</section>

{% endfor %}

<script src="https://code.jquery.com/jquery-latest.js"></script>
<script type="text/javascript">
(function($) {
    $(document).ready(function(){
        $(window).scroll(function(){
            if ($(this).scrollTop() > 200) {
                $('.nav-fade').fadeIn(500);
            } else {
                $('.nav-fade').fadeOut(500);
            }
        });
    });
})(jQuery);
</script>

