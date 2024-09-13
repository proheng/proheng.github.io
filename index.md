<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{post.date | date: '%Y %b'}} {{ post.title }}</a>
    </li>
  {% endfor %}
</ul>




