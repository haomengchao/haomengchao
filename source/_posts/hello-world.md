title: 搭建hexo参考的资料
tags:
  - 学习
  - hexo
categories:
  - 学习
date: 2021-10-03 19:59:00
---
终于是有了自己的个人博客，本来以为这件事是需要前后端从头到尾自己写，没想到现在有这么多成熟的博客框架，浏览了一圈后选定使用hexo，主要是因为和github配合部署的方案比较成熟，说白了因为对懒人好。
整个过程中参考了以下一些资料，感谢各位大佬提供的经验！


### 视频参考

主要参考了这位up主的教程： [【2021最新版】保姆级Hexo+github搭建个人博客](https://www.bilibili.com/video/BV1mU4y1j72n?p=1) 可谓是真的保姆级了


### 文字参考

[Hexo博客系列（一）：使用Hexo配合Github进行静态博客搭建](https://yehansharp.github.io/2019/12/28/Hexo%E5%8D%9A%E5%AE%A2%E7%B3%BB%E5%88%97%EF%BC%88%E4%B8%80%EF%BC%89%EF%BC%9A%E4%BD%BF%E7%94%A8Hexo%E9%85%8D%E5%90%88Github%E8%BF%9B%E8%A1%8C%E9%9D%99%E6%80%81%E5%8D%9A%E5%AE%A2%E6%90%AD%E5%BB%BA)

[Next主题for hexo](https://github.com/theme-next/hexo-theme-next)

[hexo 管理工具](https://github.com/jaredly/hexo-admin)

### Debug 记录
在部署到github的时候，有一次更换主题后css就加载不出来了，重新clean deploy了好几次都没解决，参考大量资料有说是github deploy branch的问题，有说是config.yml里root和url的问题，经过我一系列操作后终于解决了：

1. 首先github.io目前只支持在主分支上部署，指定分支部署已经不支持了，所以hexo的部署分支一定是master（现在应该叫main了），你的code放到另一个分支上。
2. config.yml里的url和root填的不对应该会导致css文件拿不到，url如果你用github的话，就填成`https://username.github.io/`, root就填 `/ `就行。
3. 还是不行的话就清除浏览器cookie。

我是通过以上三种操作解决了样式无法加载的问题。