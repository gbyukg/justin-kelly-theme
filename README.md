justin-kelly-theme
==================

This is a git repository reproduction of the theme detailed at http://blog.justin.kelly.org.au/octopress-theme/ with [a few changes.](https://github.com/wallace/justin-kelly-theme/commits/master)

See https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes for more themes.

    $ cd octopress
    $ git clone https://github.com/wallace/justin-kelly-theme.git .themes/justin-kelly-theme
    $ rake install['justin-kelly-theme']
    $ rake generate

add plugins
---
[在sidebar中按月份显示发布的文件](https://github.com/rcmdnk/monthly-archive)

[3D tag标签](https://github.com/josephcc/octopress-cumulus)

[一般设置](http://www.tuicool.com/articles/ZzeqieQ)

[文本高亮显示](https://github.com/thesp0nge/octopress_highlight_plugin)  
`{% highlight this is a great piece of wisdom %}, this is not.`

[注释，警告高亮](https://github.com/aar0nTw/Ribbonp)  
[提高索引速度](http://tonyarnold.com/2014/03/27/speeding-up-jekylls-latent-semantic-mapping.html)

[为文章内容添加索引](http://brizzled.clapper.org/blog/2012/02/04/generating-a-table-of-contents-in-octopress/#styling)

```
{%ribbonp (info|warning) <custom title>%}
Woooo Ribbon P
{%endribbonp%}
```

[相关阅读](https://github.com/huangbowen521/octopress-syncPost)

修正
---
修改`source/index.html`,修正翻页

```
---
layout: default
---

<div class="blog-index">
  {% assign index = true %}
  {% for post in paginator.posts %}
  {% assign content = post.content %}
    <article>
      {% include article.html %}
    </article>
  {% endfor %}
  <div class="pagination">
    {% if paginator.next_page %}
      <a class="prev" href="{{paginator.next_page_path}}">&larr; Older</a>
    {% endif %}
    <a href="/blog/archives">Blog Archives</a>
    {% if paginator.previous_page %}
    <a class="next" href="{{paginator.previous_page_path}}">Newer &rarr;</a>
    {% endif %}
  </div>
</div>
<aside class="sidebar">
  {% if site.blog_index_asides.size %}
    {% include_array blog_index_asides %}
  {% else %}
    {% include_array default_asides %}
  {% endif %}
</aside>

```

