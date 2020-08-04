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

需要引入 `highlight.js`

其他描述待补充。
