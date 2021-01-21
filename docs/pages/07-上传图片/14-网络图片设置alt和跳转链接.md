# 网络图片设置alt和跳转链接
在wangEditor中，插入网络图片功能可以分别设置添加alt属性和跳转链接选项，默认情况下这两个选项是开启的，如果不需要这两个选项，可以参考如下代码：
```js
// 配置alt选项
editor.config.showLinkImgAlt = false
// 配置超链接
editor.config.showLinkImgHref = false
```
配置后的效果如下：
![](../../images/img-alt-href.png)