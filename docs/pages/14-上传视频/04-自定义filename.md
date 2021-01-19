# 自定义 fileName

上传视频时，可自定义 filename ，即在使用 `formData.append(name, file)` 添加视频文件时，自定义第一个参数。

```js
editor.config.uploadVideoName = 'your-custom-fileName'
```
