# 配置alert

编辑器 customAlert 默认为 window.alert，可以自行调整。

```js
const editor = new E('#div1')
// 以 element-ui 为例
editor.config.customAlert = function (s, t) {
  switch (t) {
    case 'success':
      this.$message.success(s)
      break
    case 'info':
      this.$message.info(s)
      break
    case 'warning':
      this.$message.warning(s)
      break
    case 'error':
      this.$message.error(s)
      break
    default:
      this.$message.info(s)
      break
  }
}

editor.create()
```
