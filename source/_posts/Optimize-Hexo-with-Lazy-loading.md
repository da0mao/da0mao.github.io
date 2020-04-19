---
title: Optimize Hexo with lazy loading
author: Jun Hu
date: 2019-08-05 11:01:00
tags:
 - Hexo
---

>Lazy loading is a design pattern commonly used in computer programming to defer initialization of an object until the point at which it is needed. It can contribute to efficiency in the program's operation if properly and appropriately used.

<!-- more -->

Using lazy loading is easy:

1. Install lazyload
```bash
npm install hexo-lazyload-image --save
```

2. Update your _config.yml file as follows:
```yml
lazyload:
  enable: true 
  onlypost: false
  loadingImg: #/images/loading.png
```

Options are very intuitive. 

---

Thanks to [Troy](https://troyyang.com/2017/08/06/hexo-lazyload-image/)! 