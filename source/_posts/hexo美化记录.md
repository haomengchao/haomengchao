title: hexo美化记录
author: Mengchao Hao
tags:
  - 学习
  - hexo
categories:
  - 学习
date: 2021-10-04 14:23:00
---
#### 增加文章结尾自定义文字
在 `hexo/themes/next/layout/_marco` 下新建文件`passage-end-tag.swig` 并在其中保存以下内容
```
<div>
    {% if not is_index %}
        <div style="text-align:center;color: #ccc;font-size:14px;">{{theme.passage_end_tag.content}}</div>
    {% endif %}
</div>
``` 
修改`hexo/themes/next/layout/_marco/post.swig`， 在`POST BODY`代码块后，`POST FOOTER`代码块前加入
```
    {% if not is_index and theme.passage_end_tag.enabled %}
      {% include 'passage-end-tag.swig' %}
    {% endif %}
```
最后修改主题配置文件`themes/next/_config.yml`新加以下内容, `content`是你自定义的结尾文字
```
# 文章末尾添加“本文结束”标记
passage_end_tag:
  enabled: true
  content: 你的自定义结尾文字
```
#### 启用canvas-nest

最新版的Next已经不再集成nest，但是我尝试使用最新的启用nest的指导方法并没有成功启用nest，最后还是用了老方法将nest源文件加在Next的lib中。
在Next文件夹中将源文件拷贝下来：
```
git clone https://github.com/theme-next/theme-next-canvas-nest source/lib/canvas-nest
```
并在主题配置文件`themes/next/_config.yml`中增加
```
#canvas nest 
canvas_nest:
  enable: true    #开启canvas
  onmobile: true # 是否在移动站开启canvas
  color: '34,34,34' # 颜色值
  opacity: 0.5 # 数值 0~1 ，线条透明度
  zIndex: -1 # 背景叠层大小，-1代表放在文章的后面
  count: 200 # 线条数量
```
#### 增加音乐播放器

使用hexo-aplayer为博客增加背景音乐，具体方式参考
>[Hexo+Next 搭建个人博客 （添加网页音乐播放器）](https://leezhiy.github.io/2020/04/11/2020-04-11-Hexo-Next%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2-%EF%BC%88%E6%B7%BB%E5%8A%A0%E7%BD%91%E9%A1%B5%E9%9F%B3%E4%B9%90%E6%92%AD%E6%94%BE%E5%99%A8%EF%BC%89/)

采用文中第二种方法。注意作者所说的`hexo/scripts/plugins.js`并不存在，需要自己新建。