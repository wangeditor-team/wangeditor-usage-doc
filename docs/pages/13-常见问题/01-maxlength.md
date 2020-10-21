# max-length

**wangEditor 暂时无法实现 `max-length` 功能。**

目前业界没有一个富文本 `max-length` 的统一做法，从产品到技术层面都没有。

`max-length` 一般用于限制纯文本，用于 `<input>` `<textarea>` 。
而富文本编辑器不只能输入纯文本，还有其他很多复杂的格式，例如图片、代码块、表格。
这些非文本内容，在 `editor.txt.html()` 返回结果中要占据大量的空间。

如果你非得需要一个富文本的 `max-length` ，那目前只能是通过 `onchange` 随时检查 `editor.txt.text()` ，然后判断长度，再对富文本做禁用处理。
不过，这其中可能会发生一些预期之外的问题，到时只能随机应变。

如果你有更好的建议，可以随时给我们提交 [issue](https://github.com/wangeditor-team/wangEditor/issues) 。
