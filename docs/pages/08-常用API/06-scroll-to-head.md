# scroll-to-head

滚动到某个标题。如下图，可以获取编辑区域的所有标题，可以通过 API 让编辑器滚动到某个标题。

![](../../images/scroll-to-head.png)

PS：该功能从 `v4.5.0` 开始支持。

## 获取所有标题

通过 `onCatalogChange` 可以实时获取编辑器所有标题，标题变化即可触发该回调函数。

```js
editor.config.onCatalogChange = function (headList) {
    /*
        headList 格式
        [
            { 
                id: "eold9", // 标题 id
                tag: "H1",
                text: "标题文字"
            },
            { ... },
            { ... }
        ]
    */

    // 然后自己渲染标题 UI
}
```

## 滚动某个标题

执行 `editor.scrollToHead(headId)` 即可。
其中 `headId` 即上面获取的 `id` 。

## 回显内容时

通过 `editor.txt.html()` 获取的 html 内容，标题也是带着 id 的，格式如下。

```html
<h1 id="eold9">标题一</h1>
<p>正文</p>
<h2 id="nh339">标题二</h2>
<p>正文</p>
<h3 id="5mgwk">标题三</h3>
<p>正文</p>
```

在现实这些内容时，可以使用这些 id 来做锚点，实现 scroll to head 的功能。
