# editor 属性

编辑器唯一的 id `editor.id`

编辑器的所有配置 `editor.config`

编辑区域 DOM 节点 `editor.$textElem.elems[0]` ，元素 id `editor.textElemId`

菜单栏 DOM 节点 `editor.$toolbarElem.elems[0]` ，元素 id `editor.toolbarElemId`

# 选区范围 API

选中的文字 `editor.selection.getSelectionText()`

选区所在的 DOM 节点 `editor.selection.getSelectionContainerElem().elems[0]`

选区开始的 DOM 节点 `editor.selection.getSelectionStartElem().elems[0]`

选区结束的 DOM 节点 `editor.selection.getSelectionEndElem().elems[0]`

折叠选区 `editor.selection.collapseRange()`

判断选区是否为“空”（即没有选中任何文字）`editor.selection.isSelectionEmpty()`

# 内容操作 API

常规的内容操作参考 [内容处理](/content.html)

在光标位置插入文字 `editor.cmd.do('insertHTML', '<p>...</p>')`

可通过 `editor.cmd.do(name, value)` 来执行 `document.execCommand(name, false, value)` 的操作（`document.execCommand` 是富文本编辑器的基础 API ，文档参考 [这里](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/execCommand)）

# 禁用编辑器

```js
// 禁用编辑功能
editor.$textElem.attr('contenteditable', false)

// 开启编辑功能
editor.$textElem.attr('contenteditable', true)
```

# 销毁编辑器

待编写
