# 配置 z-index

编辑器 `z-index` 默认为 `10000`，可以自行调整。

<span style="color: red;">注意：</span>`z-index`值需要`>=0`

```js
const editor = new E('#div1')

editor.config.zIndex = 500

editor.create()
```
