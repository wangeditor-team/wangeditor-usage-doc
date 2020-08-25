# onfocus 和 onblur

编辑区域 focus（聚焦）和 blur（失焦）时触发的回调函数。

```js
const E = window.wangEditor
const editor = new E('#div1')

editor.config.onblur = function (newHtml) {
    console.log('onblur', newHtml) // 获取最新的 html 内容
}
editor.config.onfocus = function (newHtml) {
    console.log('onfocus', newHtml) // 获取最新的 html 内容
}

editor.create()
```
