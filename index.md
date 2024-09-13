<ul>
  {% for post in site.pages %}
    <li>
      <a href="{{ page.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>




