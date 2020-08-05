# 下载

npm 安装 `npm i wangeditor --save`

CDN 链接 `https://unpkg.com/wangeditor/dist/wangEditor.min.js`

# 基本使用

## 使用 js 外链引入

```html
<div id="div1">
    <p>欢迎使用 <b>wangEditor</b> 富文本编辑器</p>
</div>

<script type="text/javascript" src="//unpkg.com/wangeditor/dist/wangEditor.min.js"></script>
<script type="text/javascript">
    const E = window.wangEditor
    const editor = new E('#div1')
    // 或者 const editor = new E( document.getElementById('div1') )
    editor.create()
</script>
```

## 使用 npm 安装

```js
import E from 'wangeditor'
const editor = new E('#div1')
// 或者 const editor = new E( document.getElementById('div1') )
editor.create()
```

## 修改编辑区域高度

编辑区域高度默认是 300px ，可自行修改。

```js
editor.$textContainerElem.css('height', '600px')
```

# 菜单和编辑器区域分离

如果你想要像 知乎专栏、简书、石墨、网易云笔记 这些编辑页面一样，将编辑区域和菜单分离，也可以实现。

这样，菜单和编辑器区域就是使用者可自己控制的元素，可自定义样式。例如：将菜单fixed、编辑器区域高度自动增加等。

![](../_images/separate.png)

```html
<head>
    <style>
        .toolbar {
            border: 1px solid #ccc;
        }
        .text {
            border: 1px solid #ccc;
            min-height: 400px;
        }
    </style>
</head>
<body>
    <p>
        container 和 toolbar 分开
    </p>
    <div>
        <div id="toolbar-container" class="toolbar"></div>
        <p>------ 我是分割线 ------</p>
        <div id="text-container" class="text"></div>
    </div>

    <script src="//unpkg.com/wangeditor/dist/wangEditor.min.js"></script>
    <script>
        const E = window.wangEditor
        const editor = new E('#toolbar-container', '#text-container') // 传入两个元素
        editor.create()
    </script>
</body>
```

从上面代码可以看出，菜单和编辑区域其实就是两个单独的 `<div>`，位置、尺寸都可以随便定义。

# 使用 textarea

wangEditor 从 `v3` 版本开始不支持 `textarea` ，但是可以通过 `onchange` 来实现 `textarea` 中提交富文本内容。

```html
<div id="div1">
    <p>欢迎使用 <b>wangEditor</b> 富文本编辑器</p>
</div>
<textarea id="text1" style="width:100%; height:200px;"></textarea>

<script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
<script type="text/javascript" src="//unpkg.com/wangeditor/dist/wangEditor.min.js"></script>
<script type="text/javascript">
    const E = window.wangEditor
    const editor = new E('#div1')
    const $text1 = $('#text1')
    editor.config.onchange = function (html) {
        // 第二步，监控变化，同步更新到 textarea
        $text1.val(html)
    }
    editor.create()

    // 第一步，初始化 textarea 的值
    $text1.val(editor.txt.html())
</script>
```

# 一个页面创建多个编辑器

wangEditor 支持一个页面创建多个编辑器。

```html
<head>
    <style type="text/css">
        .toolbar {
            background-color: #f1f1f1;
            border: 1px solid #ccc;
        }
        .text {
            border: 1px solid #ccc;
            height: 200px;
        }
    </style>
</head>
<body>
    <div id="div1" class="toolbar">
    </div>
    <div style="padding: 5px 0; color: #ccc">中间隔离带</div>
    <div id="div2" class="text">
        <p>第一个 demo（菜单和编辑器区域分开）</p>
    </div>

    <div id="div3">
        <p>第二个 demo（常规）</p>
    </div>

    <!-- 引用js -->
    <script type="text/javascript" src="//unpkg.com/wangeditor/dist/wangEditor.min.js"></script>
    <script type="text/javascript">
        const E = window.wangEditor

        const editor1 = new E('#div1', '#div2')
        editor1.create()

        const editor2 = new E('#div3')
        editor2.create()
    </script>
</body>
```
