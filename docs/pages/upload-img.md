# 上传图片到服务器

【注意】如果上传图片遇到问题，请打开浏览器开发者工具，查看 `console.error` 输出的错误信息。

## 配置 server 接口

```js
const E = window.wangEditor
const editor = new E('#div1')

// 配置 server 接口地址
editor.config.uploadImgServer = '/upload-img'

editor.create()
```

配置完成之后，编辑器的图片菜单，会显示上传图片的 tab 和图标，如下图。

![](../_images/upload-img.png)

## server 接口返回格式，重要！！！

接口要返回 `application/json` 格式，格式要求如下：

```js
{
    // errno 即错误代码，0 表示没有错误。
    //       如果有错误，errno != 0，可通过下文中的监听函数 fail 拿到该错误码进行自定义处理
    "errno": 0,

    // data 是一个数组，返回图片的线上地址
    "data": [
        "图片1地址",
        "图片2地址",
        "……"
    ]
}
```

只要按照上述格式返回，编辑器即可正确的插入图片，或者抛出错误。

## 限制图片大小

默认限制图片大小是 5M ，可以自己修改。

```js
editor.config.uploadImgMaxSize = 2 * 1024 * 1024 // 2M
```

## 限制一次最多能传几张图片

默认为 100 张，需要限制可自己配置。

```js
editor.config.uploadImgMaxLength = 5 // 一次最多上传 5 个图片
```

## 自定义上传参数

上传图片时可自定义传递一些参数，例如传递验证的 `token` 等。参数会被添加到 `formData` 中，一起上传到服务端。

```js
editor.config.uploadImgParams = {
    token: 'xxxxx',
    x: 100
}
```

如果需要将**参数拼接到 url 中**，可再加上如下配置。

```js
editor.customConfig.uploadImgParamsWithUrl = true
```

## 自定义 fileName

上传图片时，可自定义 filename ，即在使用 `formData.append(name, file)` 添加图片文件时，自定义第一个参数。

```js
editor.config.uploadFileName = 'your-custom-fileName'
```

## 自定义 header

上传图片时添加 http 请求的 header 。

```js
editor.config.uploadImgHeaders = {
    Accept: 'text/x-json',
    a: 100,
}
```

## withCredentials（跨域传递 cookie）

跨域上传中如果需要传递 cookie 需设置 `withCredentials` 。

```js
editor.config.withCredentials = true
```

## 自定义 timeout 时间

timeout 即上传接口等待的最大时间，默认是 10 秒钟，可以自己修改。

```js
editor.config.uploadImgTimeout = 5 * 1000
```

## 回调函数

可使用回调函数，对上传图片的不同阶段，做相应处理。代码示例如下。

```js
editor.config.uploadImgHooks = {
    // 上传图片之前
    before(xhr) {
        console.log(xhr)

        // 可阻止图片上传
        return {
            prevent: true,
            msg: '需要提示给用户的错误信息'
        }
    }
    // 图片上传并返回了结果，图片插入已成功
    success(xhr) {
        console.log('success', xhr)
    }
    // 图片上传并返回了结果，但图片插入时出错了
    fail(xhr, editor, resData) {
        console.log('fail', resData)
    }
    // 上传图片出错，一般为 http 请求的错误
    error(xhr, editor, resData) {
        console.log('error', xhr, resData)
    }
    // 上传图片超时
    timeout(xhr) {
        console.log('timeout')
    }
    // 图片上传并返回了结果，想要自己把图片插入到编辑器中
    // 例如服务器端返回的不是 { errno: 0, data: [...] } 这种格式，可使用 customInsert
    customInsert(insertImgFn, result) {
        // result 即服务端返回的接口
        console.log('customInsert', result)

        // insertImgFn 可把图片插入到编辑器，传入图片 src ，执行函数即可
        insertImgFn(result.data[0])
    }
}
```

## 自定义 alert

上传图片的错误提示默认使用 alert 弹出，你也可以自定义用户体验更好的提示方式。

```js
editor.config.customAlert = function (s) {
    console.log('customAlert: ' + s)
}
```

## 自己写上传图片

如果想完全自己实现图片上传的过程，如上传图片到某个云服务器，可以使用如下代码。

```js
editor.config.customUploadImg = function (resultFiles, insertImgFn) {
    // resultFiles 是 input 中选中的文件列表
    // insertImgFn 是获取图片 url 后，插入到编辑器的方法

    // 上传图片，返回结果，将图片插入到编辑器中
    insertImgFn(imgUrl)
}
```

# base64 保存图片

设置 `editor.config.uploadImgShowBase64 = true` 可使用 base64 格式保存图片。即，可选择本地图片，编辑器用 base64 格式显示图片。

【注意】`uploadImgShowBase64`（base64 格式）和 `uploadImgServer`（上传图片到服务器）**两者不能同时使用**！！！

![](../_images/base64.png)

# 隐藏插入网络图片的功能

设置 `editor.config.showLinkImg = false` 即可隐藏插入网络图片的功能，即只保留上传本地图片。
