# 关闭粘贴样式的过滤

从其他地方（如网页、word 等）复制文本到编辑器中，编辑器会默认**过滤掉复制文本的样式**，这样可以让编辑器内容更加简洁。因为复制过来的文本样式，可能会比较混乱，且不可控。

可通过设置 `editor.config.pasteFilterStyle = false` 来**关闭样式过滤**。

# 忽略粘贴内容中的图片

从其他页面（如网页、word 等）复制过来的内容，除了包含文字还可能包含图片，这些图片一般都是外域的（可能会有防盗链处理，导致图片不显示）。

可以通过配置 `editor.config.pasteIgnoreImg = true` 来**忽略粘贴的图片**。如果复制的内容有图又文，则只粘贴文字，不粘贴图片。

# 自定义处理粘贴的文本内容

使用者可通过 `editor.config.pasteTextHandle` 对粘贴的文本内容进行自定义的过滤、处理等操作，然后返回处理之后的文本内容。编辑器最终会粘贴用户处理之后并且返回的的内容。

```js
const E = window.wangEditor
const editor = new E('#div1')

// 配置粘贴文本的内容处理
editor.config.pasteTextHandle = function (pasteStr) {
    // 对粘贴的文本进行处理，然后返回处理后的结果
    return pasteStr + '巴拉巴拉'
}

editor.create()
```
