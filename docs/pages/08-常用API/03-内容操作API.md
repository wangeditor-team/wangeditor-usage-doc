# 内容操作 API

常规的内容操作参考 [内容处理](/pages/02-内容处理/)

在光标位置插入文字 `editor.cmd.do('insertHTML', '<p>...</p>')`

可通过 `editor.cmd.do(name, value)` 来执行 `document.execCommand(name, false, value)` 的操作（`document.execCommand` 是富文本编辑器的基础 API ，文档参考 [这里](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/execCommand)）
