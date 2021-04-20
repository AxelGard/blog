---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---


<div id="archives">
{% for category in site.categories %}
 <div class="archive-group">
   {% capture category_name %}{{ category | first }}{% endcapture %}
   <div id="#{{ category_name | slugize }}"></div>
   <p></p>

   <h3 class="category-head">{{ category_name }}</h3>
   <a name="{{ category_name | slugize }}"></a>
   {% for post in site.categories[category_name] %}
   <article class="archive-item">
     <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h4>
   </article>
   {% endfor %}
 </div>
{% endfor %}
</div>



{% capture get_items %}
{% for cat in site.categories %}
{{ cat | first | replace: ' ', '_' }}
{% endfor %}
{% endcapture %}
{% capture num_words %}
{{ get_items | split:' ' | join:' ' | number_of_words }}
{% endcapture %}

{% for item in (1..num_words) %}

{% capture this_word %}{{ get_items | split:' ' | sort | join:' ' | truncatewords:item | remove:'...' | split:' ' | last | replace: '_', ' '  }}{% endcapture %}

<a name="{{ this_word  }}"></a>
<h3>{{ this_word }}</h3>
<ul class="related-posts">
{% for post in site.categories[this_word] %}
   {% if post.url %}<li><a href="{{ post.url }}">{{ post.title }}</a> <small>{{ post.date | date_to_string }}</small></li>{% endif %}
{% endfor %}
</ul>
{% endfor %}
