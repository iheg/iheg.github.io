---
layout: post
title:  "CSS3 媒体查询"
date:   2016-04-20 22:44:51 +0800
category: CSS
---

# 媒体类型
**指定媒体：**

1. link 标记

```html
 <link rel="stylesheet" href="style.css" media="screen, print"/>
```
2. @import 指令

```css
@import url(style.css) screen, print;
```

3. @media 指令

```css
@media screen, print {
    body {
        font-family: arial;
    }
}
```

## 媒体分组
1. all 
	所有媒体类型，默认选项
2. braille (布莱叶盲文)	
3. embossed (浮雕)与盲文类型相似，用于盲文打印机的输出
4. handheld (手持)实际上 WebKit(Mobie Safari 和 Android)以及 Firefox Mobie 会完全忽略 handheld 媒体类型
5. print 印刷媒体输出
6. projection (演示) 用于放映设备的输出，通常用于投影仪
7. screen (屏幕) 最常用的类型
8. speech (语音) 
9. tty (电传)
10. tv (电视)


# 媒体查询
媒体查询由两部分组成：一个媒体类型，零个或多个用来检查媒体特性的查询。当媒体类型符合当前设备的，并且查询结果都为真的时间，媒体查询即被应用。
例如：

```html
<link rel="stylesheet" href="style.css" media="screen and (min-width: 800px) and (max-width: 1500px)" />
```

上例使用了 `and` 子句。 还可以使用了 `not` 来否定整个媒体查询。例如：

```
<link rel="stylesheet" href="style.css" media="not screen and (min-width: 800px) and (max-width: 1500px)" />
```

不支持媒体查询的浏览器或设备被认为是 `not all`,即不会应用链接样式表或查询中的关键内容。
关键词 `only` 可以确保仅对 CSS3 支持的浏览器应用样式。

媒体查询也可以通过其他两种方式在 CSS 文件中使用，与单独使用媒体类型时的写法完全相同:

```css
@import url(style.css) screen and (min-width: 800px) and (max-width: 1500px);

@media screen and (min-width: 800px) and (max-width: 1500px) {
    body {
        font-family: arial;
    }
}	
```

需要注意的是： **即使链接的文件不被应用，浏览器也会下载**

## 视口
视口是设备可用的渲染区域大小，不包括任何浏览器的边框。

```html
<meta name="viewport" content="width=device-width" />
```
`name="viewport` 标识了该 `meta` 标签的用途。`content` 属性包括了我们想要传递的属性和值，以键=值的方式出现，使用逗号隔开任意多个键值组合。可能用到的两个重要常量是:

* `device-width` 设备的实际像素宽度(横向放置时)
* `device-height` 设备的实际像素高度(横向放置时)

还有六个可用的重要属性：

1. `width` 视口横向放置时的初始像素宽度。
2. `height` 视口横向放置时的初始像素高度。
3. `initial-scale` 缩放指在计算视口尺寸时要乘以的倍数。默认情况下通常会自动设置一个值，用以将当前整个 Web 页面匹配到可视区域中。
4. `minimum-scale` 设置用户可以缩放的最小值
5. `maximum-scale` 设置用户可以缩放的最大值
6. `user-scalable` 设置在视口中是否允许用户进行缩放，yes 或 no。默认是 yes

# 媒体特性

1. `width` 应用于视口的宽度，而不仅仅是可显示的屏幕空间宽度
2. `height` 视口的高度，用法与 `width` 相同
3. `device-width` (设备宽度)
4. `device-height` (设备高度)
5. `orientation` (方向) 可选值： `landscape`(横放) 和 `portrait`(竖放)
6. `aspect-ratio` (宽高比) 视口宽度和高度的比值，中间用斜杠隔开
	
	```css
	@media screen and (aspect-ratio: 4/3) {
		...
	}
	```
	
7. `device-aspect-ratio` (设备宽高比) 可显示区域宽度和高度的比值
8. `color` 设备表示每种色彩成分所用的字位数量
9. `color-index` (颜色索引)
10. `monochrome` (单色)
11. `resolution` (分辨率)
12. `scan` (扫描) 电视机专属
13. `grid` (栅格) 设备基于栅格还是位图
14. `transform-2d` (二维变换) 在二维尺度上是否可以使用 CSS 变换。可以, 值为 1, 不可以, 值为 0
15. `transform-3d` (三维变换)
16. `transition` (过渡)
17. `animation` (动画)