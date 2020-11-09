# 获取/设置 JSON

## 获取 JSON

使用 `editor.txt.getJSON()` 获取 JSON 格式的内容，格式如下。

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
        "tag": "p",
        "attrs": [],
        "children": [
            {
                "tag": "img",
                "attrs": [
                    { "name": "src", "value": "xxx.png" },
                    { "name": "style", "value": "max-width:100%;" }
                ]
            }
        ]
    }
]
```

## 设置 JSON

使用 `editor.txt.setJSON({...})` ，传入上述的 JSON 格式，可设置内容。

注意，`setJSON` 从 `v4.3.0` 版本开始支持。
