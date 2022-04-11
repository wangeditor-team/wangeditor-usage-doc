# placeholder

可以修改 placeholder 的提示文字。

```js
const editor = new E('#div1')

editor.config.placeholder = '自定义 placeholder 提示文字'
// editor.config.placeholder = '' // 不想使用 placeholder ，赋值为空字符串即可

editor.create()
```

注意：在使用国际化时，如果 placeholder 中含有 `.`，请在模板中配置，具体参考[这里](../12-多语言/README.md)。