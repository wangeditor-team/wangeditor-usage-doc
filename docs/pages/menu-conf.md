# 自定义菜单栏

【注意】v3 版本开始，菜单不支持换行折叠了（因为换行之后菜单栏是在太难看），如果菜单栏宽度不够，建议精简菜单项。

## 配置菜单

编辑器创建之前，可使用 `editor.config.menus` 定义显示哪些菜单和菜单的顺序。

```html
<div id="div1">
    <p>欢迎使用 wangEditor 编辑器</p>
</div>

<script type="text/javascript" src="//unpkg.com/wangeditor/dist/wangEditor.min.js"></script>
<script type="text/javascript">
    const E = window.wangEditor
    const editor = new E('#div1')

    // 配置菜单栏，删减菜单，调整顺序
    editor.config.menus = [
        'bold',
        'head',
        'link',
        'italic',
        'underline'
    ]

    editor.create()
</script>
```

## 所有菜单

默认情况下会显示所有的菜单，配置如下：

```js
// 默认情况下，显示所有菜单
editor.config.menus = [
    // 待补充
]
```

# 配置颜色

编辑器的字体颜色和背景色，可以通过 `editor.config.colors` 自定义配置

```js
const E = window.wangEditor
const editor = new E('#div1')

// 配置颜色（文字颜色、背景色）
editor.config.colors = [
    '#000000',
    '#eeece0',
    '#1c487f',
    '#4d80bf'
]

editor.create()
```

# 配置字体

编辑器的字体，可以通过 `editor.config.fontNames` 配置。

```js
const E = window.wangEditor
const editor = new E('#div1')

// 配置字体
editor.config.fontNames = [
    '黑体',
    '仿宋',
    '楷体',
    '标楷体',
    '华文仿宋',
    '华文楷体',
    '宋体',
    '微软雅黑',
    'Arial',
    'Tahoma',
    'Verdana',
    'Times New Roman',
    'Courier New',
]

editor.create()
```

# 配置字号

待补充。

包括 customFontSize 和 fontSize 的区别

# 插入代码

wangEditoor中的"插入代码"菜单模块, 支持通过引入  **highlight js** 插件实现代码高亮的样式功能.并且提供多种样式支持. 编辑器默认不带有 highlight, 您需要手动安装高亮插件.

highlight js官网: https://highlightjs.org

## 安装 highlight

npm 方式

```javascript
npm install highlight.js -S
```

CDN 引入

```html
<script src="http://cdn.bootcss.com/highlight.js/8.0/highlight.min.js"></script>
```

## 挂载 highlight

**1.获取highlight实例**

```javascript
import hljs from 'highlight.js'
```

(cdn引入,highlight 实例 "hljs"会声明到window下, 直接调用即可)

挂载设置代码如下

```javascript
const E = window.wangEditor
const editor = new E('#div1')

// 挂载highlight插件
editor.highlight = hljs

editor.create()
```

**2.css的引入**

npm方式

```javascript
import 'highlight.js/styles/monokai_sublime.css'
```

CDN引入

```html
<link href="http://cdn.bootcss.com/highlight.js/8.0/styles/monokai_sublime.min.css" rel="stylesheet">
```

完成以上所有步骤之后, 再次使用wangEditor中的  **插入代码** 功能, 就能够有高亮效果了, 如图所示

![highlight-example](../_images/highlight-example.png)

## 显示内容

当您在读取文本数据作展示时, 需要使用highlight重新渲染

**1.首先您需要在文本展示页面安装highlight插件**

(安装方式与富文本页面引入highlight相同,不再赘述)

**2.获取的到highlight的实例后, 使用其全局渲染方法, 对代码文本进行渲染, 即可实现高亮显示.**

```javascript
hljs.initHighlightingOnLoad();
```



更多highlight使用方法, 请参考highlight.js官方手册