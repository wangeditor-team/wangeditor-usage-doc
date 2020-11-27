# 自定义 alert

编辑器 customAlert 是对全局的alert做了统一处理，默认为 window.alert。

如觉得浏览器自带的alert体验不佳，可自定义 alert，以便于达到与自身项目统一的alert效果。

```js
import { message } from 'antd';

const editor = new E('#div1')
// 以 Ant Design 为例
editor.config.customAlert = function (s, t) {
  switch (t) {
    case 'success':
      message.success(s)
      break
    case 'info':
      message.info(s)
      break
    case 'warning':
      message.warning(s)
      break
    case 'error':
      message.error(s)
      break
    default:
      message.info(s)
      break
  }
}

editor.create()
```
