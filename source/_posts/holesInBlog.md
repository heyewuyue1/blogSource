---
title: 搭建博客遇到的坑
date: 2021-10-10 16:34:51
tags:
 - 搭建博客
---

# 部署博客时没有样式

- 如下设置`_config.yml`:
```yml
url: https://heyewuyue1.github.io
	...
deploy:
  type: git
  repo: https://github.com/heyewuyue1/heyewuyue1.github.io

```

# Series点进去没有反应

- 直接把`themes/vexo/layout/series.ejs`删除就可以了。也不知道series是干嘛的，删了之后点series就是一个空白的md页面。至少不会卡死了，就这样吧。

# 博客里面插入不了图片

- ~~尚未解决~~。
- 用[图床](http://sm.ms)解决了。官方文档一点都不好使，感觉几年没更新了。

# 博客的多行公式不能用\\\\换行

- 后来发现原来在渲染的时候“\\\\”会被渲染成“\\”。所以要实现多行公式的换行要在源文件里输入四个“\\”也就是“\\\\\\\\”。这样渲染完才是两个“\\”。（包括我打这段话的时候每个“\\”，都要输入双倍的“\\”）

# 博客的评论不好使

- vexo主题自带的评论系统因为种种原因要不就是不好使，要不就是根本用不了。我现在采用的是valine评论系统，直接采用暴力的方法把valine的html和js源码复制在每篇md下方即可。
```html
<br><br><br><br><br>
<script src="//unpkg.com/valine/dist/Valine.min.js"></script>
<div id="vcomments"></div>
<script>
    new Valine({
        el: '#vcomments',
        appId: 'appId',
        appKey: 'appKey'
    })
</script>
```

<br><br><br><br><br>
<script src="//unpkg.com/valine/dist/Valine.min.js"></script>
<div id="vcomments"></div>
<script>
    new Valine({
        el: '#vcomments',
        appId: 'pYVxUdjGaaE4WkIo9yulsMpw-gzGzoHsz',
        appKey: 'k5IXm5eqTCqoajlqYcc8F39c'
    })
</script>