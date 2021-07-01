# onchange

## 配置 onchange 回调函数

配置 `onchange` 函数之后，用户操作（鼠标点击、键盘打字等）导致的内容变化之后，会自动触发 `onchange` 函数执行。

如果需要修改 `onchange` 触发的延迟时间（ `onchange` 会在用户无任何操作的 xxx 毫秒之后被触发），可通过 `onchangeTimeout` 配置。更多信息请见 [配置历史记录](../02-内容处理/07-配置历史记录.html)

```js
const E = window.wangEditor;
const editor = new E("#div1");

// 配置 onchange 回调函数
editor.config.onchange = function (newHtml) {
  console.log("change 之后最新的 html", newHtml);
};
// 配置触发 onchange 的时间频率，默认为 200ms
editor.config.onchangeTimeout = 500; // 修改为 500ms

editor.create();
```

# onSelectionChange

## 配置 onSelectionChange 回调函数

v4.7.5+

配置 `onSelectionChange` 函数之后，用户选区操作（鼠标选中文字，ctrl+a 全选等）会自动触发`onSelectionChange` 函数执行。

其中回调参数有 3 个是`text`,`html`,`selection`,分别为`当前选择文本`,`当前选中的html`,`原生selection对象`

```js
const E = window.wangEditor;
const editor = new E("#div1");
// 配置 onSelectionChange 回调函数
editor.config.onSelectionChange = function (newSelection) {
  console.log("onSelectionChange", newSelection);
  /**
    {
       text:'wangeditor', // 当前选择文本
       html: '<p>wangeditor</p>', // 当前选中的html
       selection: selection, // 原生selection对象
    }
   */
};
editor.create();
```
