# XSS 攻击

富文本编辑器是最容易发生 XSS 攻击的工具之一。

XSS 的攻击方式非常多。简单的方式方案（如替换 `< >` 为 `&lt; &gt;`）无法全面解决问题。

因此，我们推荐使用专业的工具 [xss](https://www.npmjs.com/package/xss) 来解决。

```js
const html = editor.txt.html()
const safeHtml = xss(html)
console.log('处理过 xss 攻击的 html', safeHtml)
```
