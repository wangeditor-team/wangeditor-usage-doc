# 自定义 fileName

上传图片时，可自定义 filename ，即在使用 `formData.append(name, file)` 添加图片文件时，自定义第一个参数。

```js
editor.config.uploadFileName = 'your-custom-fileName'
```
