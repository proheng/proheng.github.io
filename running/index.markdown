---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults


layout: post
---

<p>
你好, 俺是一个985－211毕业，奔四而黑发犹存，无框眼镜，双肩背包，运动鞋，滑板车，具有多年搬砖，平时爱翻翻书喝喝茶的大叔。
</p>
<p>读书之余，我还会练习一下写作，英语不好，所以写中文。这是我每个星期都会更新的读书笔记。欢迎浏览。</p>


<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }} ({{post.date | date_to_long_string }} )</a>
    </li>
  {% endfor %}
</ul>


