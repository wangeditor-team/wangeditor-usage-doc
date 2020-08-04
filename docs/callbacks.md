# onchange

## 配置 onchange 回调函数

配置 `onchange` 函数之后，用户操作（鼠标点击、键盘打字等）导致的内容变化之后，会自动触发 `onchange` 函数执行。

如果需要修改 `onchange` 触发的延迟时间（ `onchange` 会在用户无任何操作的 xxx 毫秒之后被触发），可通过 `onchangeTimeout` 配置。

```js
const E = window.wangEditor
const editor = new E('#div1')

// 配置 onchange 回调函数
editor.config.onchange = function (newHtml) {
    console.log('change 之后最新的 html', newHtml)
}
// 配置触发 onchange 的时间频率，默认为 200ms
editor.config.onchangeTimeout = 500 // 修改为 500ms

editor.create()
```

## 有些情况无法触发 onchange 事件

如用户自己用 js 修改了 DOM 节点的内容，没有通过编辑器修改内容，则不会触发编辑器的 `onchange` 。

此时可以主动执行 `editor.change()` 来触发 `onchange` 回调函数。

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

# 插入网络图片的回调事件

```js
const E = window.wangEditor
const editor = new E('#div1')

// 插入网络图片的回调
editor.config.linkImgCallback = function (src) {
    console.log('图片 src ', src)
}

editor.create()
```

# 删除图片的回调事件

待补充
