# 准备

```js
// 引入 wangEditor
import E from 'wangeditor' // npm 安装
// const E = window.wangEditor // CDN 引入的方式

// 获取必要的变量，这些在下文中都会用到
const { $ } = E
const { BtnMenu, DropListMenu, PanelMenu, DropList, Panel, Tooltip } = E.menuConstructors
```

# 快速注册一个菜单

【注意】以 Button 菜单为例演示，下文会提到其他类型的菜单，注册步骤都是一样的。

## 菜单 class

```js
// 第一，菜单 class ，Button 菜单继承 BtnMenu class
class AlertMenu extends BtnMenu {
    constructor(editor) {
        const $elem = E.$(
            `<div class="w-e-menu">
                <button>alert</button>
            </div>`
        )
        super($elem, editor)
    }
    // 菜单点击事件
    clickHandler() {
        // 做任何你想做的事情
        // 可参考【常用 API】文档，来操作编辑器

        alert('hello world')
    }
    // 菜单是否被激活（如果不需要，这个函数可以空着）
    // 1. 激活是什么？光标放在一段加粗、下划线的文本时，菜单栏里的 B 和 U 被激活，如下图
    // 2. 什么时候执行这个函数？每次编辑器区域的选区变化（如鼠标操作、键盘操作等），都会触发各个菜单的 tryChangeActive 函数，重新计算菜单的激活状态
    tryChangeActive() {
        // 激活菜单
        // 1. 菜单 DOM 节点会增加一个 .w-e-active 的 css class
        // 2. this.this.isActive === true
        this.active()

        // // 取消激活菜单
        // // 1. 菜单 DOM 节点会删掉 .w-e-active
        // // 2. this.this.isActive === false
        // this.unActive()
    }
}
```

![](../_images/menu-active.png)

## 注册菜单

```js
const editor = new E('#div1')

// 注册菜单
const menuKey = 'alertMenuKey' // 菜单 key ，各个菜单不能重复
editor.menus.extend('alertMenuKey', AlertMenu)

// 将菜单加入到 editor.config.menus 中
// 也可以通过配置 menus 调整菜单的顺序，参考【配置菜单】部分的文档
editor.config.menus = editor.config.menus.concat(menuKey)

// 注册完菜单，再创建编辑器，顺序很重要！！！
editor.create()
```

![](../_images/custom-menu.png)

# Button 菜单

上文【注册菜单】部分已介绍。

# DropList 菜单

DropList 菜单，鼠标 hover 菜单时，显示下拉列表，如下图。

![](../_images/droplist.png)

开发一个 DropList 菜单的 class 代码如下。**另，注册菜单，和上文过程一样，不再赘述。**

```js
// 标题菜单的 class ，可作为 DropList 菜单的参考代码
class Head extends DropListMenu {
    constructor(editor) {
        // 菜单栏中，标题菜单的 DOM 元素
        // 注意，这里的 $ 不是 jQuery ，是 E.$ （wangEditor 自带的 DOM 操作工具，类似于 jQuery）
        const $elem = $('<div class="w-e-menu"><i class="w-e-icon-header"></i></div>')

        // droplist 配置
        const dropListConf = {
            width: 100,
            title: '设置标题',
            type: 'list',
            list: [
                { $elem: $('<h1>H1</h1>'), value: '<h1>' },
                { $elem: $('<h2>H2</h2>'), value: '<h2>' },
                { $elem: $('<h3>H3</h3>'), value: '<h3>' },
                { $elem: $('<h4>H4</h4>'), value: '<h4>' },
                { $elem: $('<h5>H5</h5>'), value: '<h5>' },
                { $elem: $('<p>正文</p>'), value: '<p>' },
            ],
            // droplist 每个 item 的点击事件
            clickHandler: (value) => {
                // value 参数即 dropListConf.list 中配置的 value
                this.command(value)
            },
        }

        super($elem, editor, dropListConf)
    }

    command(value) {
        // 设置标题
        this.editor.cmd.do('formatBlock', value)
    }

    // 菜单是否需要激活
    tryChangeActive() {
        const reg = /^h/i
        const cmdValue = this.editor.cmd.queryCommandValue('formatBlock')
        if (reg.test(cmdValue)) {
            // 选区处于标题内，激活菜单
            this.active()
        } else {
            // 否则，取消激活
            this.unActive()
        }
    }
}
```

# Panel 菜单

Panel 菜单，点击菜单时，弹出 panel ，如下图。

![](../_images/panel.png)

开发一个 Panel 菜单，可直接参考[视频菜单的源码](https://github.com/wangeditor-team/we-next/tree/master/src/menus/video)，比较好理解。看源码过程中需注意：

- 忽略 typescript 的类型
- 忽略 `index.ts` 中的 `MenuActive`
- 忽略 `create-panel-conf.ts` 中的 `getRandom` 方法，自己定义字符串即可
- 总之，看主流程，不要被一些不重要的事情所影响

另，注册菜单，和上文过程一样，不再赘述。

# 更多可参考的源码

更多菜单的代码，可直接参考 wangEditor [菜单部分的源码](https://github.com/wangeditor-team/we-next/tree/master/src/menus) 。

再有问题也可[加入 QQ 群](/#交流)交流。

# 自定义 tooltip

在编辑区域可以通过 tooltip 来实现更复杂的操作，例如下图的链接，可以通过 tooltip 来查看链接、删除链接。

![](../_images/tooltip.png)

要自定义 tooltip ，可以参考[链接的 tooltip 源码](https://github.com/wangeditor-team/we-next/tree/master/src/menus/link/bind-event)。代码写完之后，将 `index.ts` 中的 `bindEvent` 函数执行即可，但要在 `editor.create()` 之前执行。

看源码，实现 tooltip 需要用到 `editor.txt.eventHooks` ，请继续往下看。

# 编辑区域的各种事件回调（钩子）

## 是什么

想要监听编辑区域的各种事件回调，如鼠标点击、keyup、粘贴、点击图片、点击链接、滚动等，不用自己写。编辑器内都有定义，并开放使用。

```js
// eventHooks 举例
{
    dropEvents: Function[]
    clickEvents: Function[]
    keyupEvents: Function[]
    tabUpEvents: Function[] // tab 键（keyCode === ）Up 时
    tabDownEvents: Function[] // tab 键（keyCode === 9）Down 时
    enterUpEvents: Function[] // enter 键（keyCode === 13）up 时
    deleteUpEvents: Function[] // 删除键（keyCode === 8）up 时
    deleteDownEvents: Function[] // 删除键（keyCode === 8）down 时
    pasteEvents: Function[] // 粘贴事件
    linkClickEvents: Function[] // 点击链接事件
    textScrollEvents: Function[] // 编辑区域滑动事件
    toolbarClickEvents: Function[] // 菜单栏被点击
    imgClickEvents: Function[] // 图片被点击事件
    // 等等……
}
```

所有 eventHooks 及其内部实现，可以参考[源码](https://github.com/wangeditor-team/we-next/blob/master/src/text/index.ts#L13)。

## 如何使用

使用 eventHooks 非常简单，例如[链接的 tooltip 源码](https://github.com/wangeditor-team/we-next/blob/master/src/menus/link/bind-event/tooltip-event.ts)中就有使用。定义一个函数，push 到相应的 eventHooks 就可以了。

```js
// function showLinkTooltip() { /* 显示 tooltip */ }
// function hideLinkTooltip() { /* 隐藏 tooltip */ }

// 点击链接元素是，显示 tooltip
editor.txt.eventHooks.linkClickEvents.push(showLinkTooltip)

// 点击其他地方，有键盘操作，或者滚动时，隐藏 tooltip
editor.txt.eventHooks.clickEvents.push(hideLinkTooltip)
editor.txt.eventHooks.keyupEvents.push(hideLinkTooltip)
editor.txt.eventHooks.toolbarClickEvents.push(hideLinkTooltip)
editor.txt.eventHooks.textScrollEvents.push(hideLinkTooltip)
```
