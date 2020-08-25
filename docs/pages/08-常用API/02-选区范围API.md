# 选区范围 API

选中的文字 `editor.selection.getSelectionText()`

选区所在的 DOM 节点 `editor.selection.getSelectionContainerElem().elems[0]`

选区开始的 DOM 节点 `editor.selection.getSelectionStartElem().elems[0]`

选区结束的 DOM 节点 `editor.selection.getSelectionEndElem().elems[0]`

折叠选区 `editor.selection.collapseRange()`

判断选区是否为“空”（即没有选中任何文字）`editor.selection.isSelectionEmpty()`
