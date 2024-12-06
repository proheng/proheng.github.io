---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults


layout: post
---



<h1>Posts in "Running"</h1>
<ul>
  {% for post in site.posts %}
    {% if post.categories contains "running" %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a>
        <small>({{ post.date | date: "%B %d, %Y" }})</small>
      </li>
    {% endif %}
  {% endfor %}
</ul>