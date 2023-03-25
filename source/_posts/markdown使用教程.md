---
title: markdown使用教程
date: 2023-03-24 21:36:48
tags: 
- markdown
- 标记语言
- 轻量级
categories: 软件工具
top: true
---



# markdown引入图片、音频、视频

## **1、markdown 简介**

- Markdown 是一种轻量级标记语言，它允许人们使用易读易写的纯文本格式编写文档。
- Markdown 编写的文档后缀为 .md, .markdown
- 简单易学容易上手，十分钟左右即可上手
- 有助于作者专心写作（各种在线博客编辑坑太多，文档丢失、广告太多，可移植性差）

  

## **2、插入图片**

我们在写博客的时候总免不了要插入各种图片，下面就是markdown插入图片的语法

```text
![图片描述关键词](图片链接地址)
```

## **3、插入音频**

### **3.1 使用audio 标签**

语法如下：

```text
<audio id="audio" controls="" preload="none">
      <source id="mp3" src="音频地址">
</audio>
```

插入音频后效果如下：

<audio id="audio" controls="" preload="none">
      <source id="mp3" src="音频地址">
</audio>

### **3.2 使用iframe标签**

我们以网易云音乐为例 1.首先在网易云音乐播放界面，点击生成外链播放器

![img](https://pic4.zhimg.com/80/v2-3c2ef02608fc13a41a3c1f1d92480073_1440w.webp)

2.选择自己想要的大小的iframe代码块

![img](https://pic3.zhimg.com/80/v2-243b06dc7502415ad623c0cd43d726be_1440w.webp)

3.复制iframe代码块嵌入到页面中

```text
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=1488737309&auto=1&height=66"></iframe>
```

效果如下：

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=1488737309&auto=1&height=66"></iframe>

## **4、引入视频**

对应语法如下，这两个都可以

```html
<video src="视频链接"></video>
<iframe height=498 width=510 src="视频链接">
```

我们以小破站为例，因为免费。小破站牛逼 1.找到我们想要的视频，然后点击下面的分享按钮

![img](https://pic3.zhimg.com/80/v2-8ffa8949d227124109aa1d7792412a06_1440w.webp)



2.加入一个自适应iframe

<iframe src="//player.bilibili.com/player.html?aid=59317437&bvid=BV1Pt411G7qh&cid=103365806&page=1" scrolling="no" border="20" frameborder="no" framespacing="0"  allowfullscreen="allowfullscreen" height=498 width=100%> </iframe>





```
<iframe width="560" height="315" src="https://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allowfullscreen></iframe>
```

<iframe width="560" height="315" src="https://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allowfullscreen></iframe>



 





```html
<video src="https://raw.githubusercontent.com/xiangchengkang/blogImage/main/img/%E9%97%AA%E7%83%81%E4%B9%8B%E7%8B%90.mp4"></video>
```











