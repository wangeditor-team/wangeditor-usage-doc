# 获取 JSON

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
