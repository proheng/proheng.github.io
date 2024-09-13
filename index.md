<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ date }} - {{ post.title }}</a>
    </li>
  {% endfor %}
</ul>




