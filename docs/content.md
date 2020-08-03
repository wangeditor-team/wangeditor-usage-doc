# 设置内容

以下方式中，如果条件允许，尽量使用第一种方式，效率最高。

## html 初始化内容

直接将内容写到要创建编辑器的 `<div>` 标签中。

```html
<div id="div1">
    <p>初始化的内容</p>
    <p>初始化的内容</p>
</div>

<script type="text/javascript" src="//unpkg.com/wangeditor/dist/wangEditor.min.js"></script>
<script type="text/javascript">
    const E = window.wangEditor
    const editor = new E('#div1')
    editor.create()
</script>
```

## js 设置内容

创建编辑器之后，使用 `editor.txt.html(...)` 设置编辑器内容。

```html
<div id="div1">
</div>

<script type="text/javascript" src="//unpkg.com/wangeditor/dist/wangEditor.min.js"></script>
<script type="text/javascript">
    const E = window.wangEditor
    const editor = new E('#div1')
    editor.create()
    editor.txt.html('<p>用 JS 设置的内容</p>') // 重新设置编辑器内容
</script>
```

## 追加内容

创建编辑器之后，可使用 `editor.txt.append('<p>追加的内容</p>')` 继续追加内容。

# 获取内容

## 获取 html

使用 `editor.txt.html()` 获取 html 。

需要注意的是：**从编辑器中获取的 html 代码是不包含任何样式的纯 html**，如果显示的时候需要对其中的 `<table>` `<code>` `<blockquote>` 等标签进行自定义样式（这样既可实现**多皮肤**功能），下面提供了编辑器中使用的样式供参考。

```less
/* table 样式 */
table {
  border-top: 1px solid #ccc;
  border-left: 1px solid #ccc;
}
table td,
table th {
  border-bottom: 1px solid #ccc;
  border-right: 1px solid #ccc;
  padding: 3px 5px;
}
table th {
  border-bottom: 2px solid #ccc;
  text-align: center;
}

/* blockquote 样式 */
blockquote {
  display: block;
  border-left: 8px solid #d0e5f2;
  padding: 5px 10px;
  margin: 10px 0;
  line-height: 1.4;
  font-size: 100%;
  background-color: #f1f1f1;
}

/* code 样式 */
code {
  display: inline-block;
  *display: inline;
  *zoom: 1;
  background-color: #f1f1f1;
  border-radius: 3px;
  padding: 3px 5px;
  margin: 0 3px;
}
pre code {
  display: block;
}

/* ul ol 样式 */
ul, ol {
  margin: 10px 0 10px 20px;
}
```

## 获取 text

使用 `editor.txt.text()` 获取 text 文本。

## 获取 JSON

使用 `editor.txt.getJSON()` 获取 JSON 格式的内容。格式如

```json
[
    {
        "tag": "p",
        "attrs": [],
        "children": [
            "欢迎使用 ",
            {
                "tag": "b",
                "attrs": [],
                "children": [ "wangEditor" ]
            },
            " 富文本编辑器"
        ]
    },
    {
        "tag": "img",
        "attrs": [
            { "name": "src", "value": "xxx.png" },
            { "name": "style", "value": "max-width:100%;" }
        ],
        "children": []
    },
]
```

# 清空内容

可使用 `editor.txt.clear()` 清空编辑器内容。
