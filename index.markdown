---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults


layout: post
---

<span>
  一个985，211毕业的，奔四尚未秃头的，带无框眼镜的，背着书包的，骑着滑板车上班的，高级软件程序男砖家的。
</span>

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }} ({{post.date | date_to_long_string }} )</a>
    </li>
  {% endfor %}
</ul>


