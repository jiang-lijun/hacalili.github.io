---
title: HTML+CSS案例展示(CSS3D效果旋转相册)
date: 
author: hacalili
categories: 前端作品及案例展示
tags:
  - HTML
  - CSS
  - JS
---

>  参考来源：
>
> [黑马程序员pink老师前端入门教程，零基础必看的h5(html5)+css3+移动端前端视频教程_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV14J4114768?p=390&spm_id_from=pageDriver)

# 效果展示：

![img](https://img-blog.csdnimg.cn/44981bc1e2994ec5831ac02c1f83e9be.gif)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

<!-- more -->

# 总结：

1. **transform****：translate(x,y) rotate(180deg) scale() ...** 顺序对最后的效果有影响，需要根据需求安排位移和其他属性的顺序；
2. 实现暂停动画效果：**animation-play-state:paused;** 经常和鼠标经过等其他配合使用；
3. 实现动画走回来，而不是跳回来：**animation-direction:alternate;** ；
4. 实现动画结束后，停在结束位置：**animation-fill-mode:forwards;** ；
5. 实现打字机动画效果：**steps()** 指定时间函数的间隔步长，用来分几步完成动画，有了 **steps()** 就不要写 **ease** 或 **linear** ；
6. 实现大数据热点图时，不要用 **scale** ，会把阴影放大；
7. 3D透视 **perspective** 和 3D呈现 **transform-style:preserve-3d;** 需要写在被观察盒子的父级盒子里面；

## 网页GitHub地址如下：（若加载较慢建议刷新后耐心等待一会~）

[css3dphoto](https://jiang-lijun.github.io/css3dphoto/)

# 网页代码如下：

HTML+CSS：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>css3dphoto</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        body {
            perspective: 1500px;
        }
        section {
            position: relative;
            margin: 500px auto;
            width: 300px;
            height: 206px;
            transform-style: preserve-3d;
            animation: rotatephoto  10s linear;
            background: url(img1.jpg) no-repeat;
        }
        section:hover {
            animation-play-state: paused;
        }
        @keyframes rotatephoto {
            0% {
                transform: rotateY(0);
            }
            100% {
                transform: rotateY(360deg);
            }
        }
        section div {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url(img.jpg) no-repeat;
        }
        section div:nth-child(1) {
            transform: translateZ(300px);
        }
        section div:nth-child(2) {
            transform: rotateY(60deg) translateZ(300px);
        }
        section div:nth-child(3) {
            transform: rotateY(120deg) translateZ(300px);
        }
        section div:nth-child(4) {
            transform: rotateY(180deg) translateZ(300px);
        }
        section div:nth-child(5) {
            transform: rotateY(240deg) translateZ(300px);
        }
        section div:nth-child(6) {
            transform: rotateY(300deg) translateZ(300px);
        }
    </style>
</head>
<body>
    <section>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
        <div></div>
    </section>
</body>
</html>
```

