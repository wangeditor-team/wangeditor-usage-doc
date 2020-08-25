# 自定义 alert

上传图片的错误提示默认使用 alert 弹出，你也可以自定义用户体验更好的提示方式。

```js
editor.config.customAlert = function (s) {
    console.log('customAlert: ' + s)
}
```
