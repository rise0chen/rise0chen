---
title: php实时输出
date: 2016-05-11
categories: [✬后端, PHP]
---

php 默认情况下会等到脚本执行完成后再输出,可以通过以下两种方法实现实时输出。

<!--more-->

## 方案一、修改 php.ini

```apacheconf
output_buffering=Off
implicit_flush=On
```

## 方案二、增加代码

```php
ob_end_clean();
ob_implicit_flush(1);
```
