# 自动 focus

编辑器初始化时，默认会自动 focus 到编辑区域。可通过如下操作，取消自动 focus 。

```js
const editor = new E('#div1')

// 取消自动 focus
editor.config.focus = false

editor.create()
```
