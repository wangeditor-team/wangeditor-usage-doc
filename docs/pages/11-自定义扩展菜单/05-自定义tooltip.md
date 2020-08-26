# 自定义 tooltip

在编辑区域可以通过 tooltip 来实现更复杂的操作，例如下图的链接，可以通过 tooltip 来查看链接、删除链接。

![](../../images/tooltip.png)

要自定义 tooltip ，可以参考[链接的 tooltip 源码](https://github.com/wangeditor-team/we-next/tree/master/src/menus/link/bind-event)。代码写完之后，将 `index.ts` 中的 `bindEvent` 函数执行即可，但要在 `editor.create()` 之前执行。

看源码，实现 tooltip 需要用到 `editor.txt.eventHooks` ，请继续往下看。
