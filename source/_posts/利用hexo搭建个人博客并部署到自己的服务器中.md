---
title: 利用hexo搭建个人博客并部署到自己的服务器中
date: 2021-08-10 18:29:14
tags: 
  - Linux
  - Hexo
categories:
  - 教程
  - Hexo
description: 安装hexo
---

这是一篇测试笔记

![图片](https://zdkj-oss-bucket.oss-cn-hangzhou.aliyuncs.com/car-rental-user/common/pic/avatar.jpg)

{% note default simple %}
default 提示块标籤
{% endnote %}

<div class="gallery-group-main">
{% galleryGroup '壁纸' '收藏的一些壁纸' '/Gallery/wallpaper' https://i.loli.net/2019/11/10/T7Mu8Aod3egmC4Q.png %}
{% galleryGroup '漫威' '关于漫威的图片' '/Gallery/marvel' https://i.loli.net/2019/12/25/8t97aVlp4hgyBGu.jpg %}
{% galleryGroup 'OH MY GIRL' '关于OH MY GIRL的图片' '/Gallery/ohmygirl' https://i.loli.net/2019/12/25/hOqbQ3BIwa6KWpo.jpg %}
</div>

{% gallery %}
![](https://i.loli.net/2019/12/25/Fze9jchtnyJXMHN.jpg)
![](https://i.loli.net/2019/12/25/ryLVePaqkYm4TEK.jpg)
![](https://i.loli.net/2019/12/25/gEy5Zc1Ai6VuO4N.jpg)
![](https://i.loli.net/2019/12/25/d6QHbytlSYO4FBG.jpg)
![](https://i.loli.net/2019/12/25/6nepIJ1xTgufatZ.jpg)
![](https://i.loli.net/2019/12/25/E7Jvr4eIPwUNmzq.jpg)
![](https://i.loli.net/2019/12/25/mh19anwBSWIkGlH.jpg)
![](https://i.loli.net/2019/12/25/2tu9JC8ewpBFagv.jpg)
{% endgallery %}

**代码：**
```
// 获取信息
async vehicleVehiclePreview() {
  const [err, res] = await vehicleVehiclePreviewvehicleVehiclePreviewvehicleVehiclePreviewvehicleVehiclePreviewvehicleVehiclePreview(this.vehicleId, this.orderId)
  if (err) return
  this.carNumber = res.data.carNumber
  this.goodsList = res.data.goodsList
  this.mileage = res.data.mileage
  this.oil = res.data.oil
  this.remarksList = res.data.remarksList
},
// 预览图片
previewPics(urls, index = 0) {
  previewImgs(urls, index)
},
```
