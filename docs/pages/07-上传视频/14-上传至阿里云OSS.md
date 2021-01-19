# 上传至阿里云OSS

首先，[安装 OSS 相关工具](https://help.aliyun.com/document_detail/64041.html?spm=a2c4g.11186623.6.1463.7729677aEdDm5v)，然后编写代码：

```js
// 具体值需要去阿里云控制台获取
let client = new OSS({
  // // region以杭州为例（oss-cn-hangzhou），其他region按实际情况填写。
  // region: '<Your region>',
  // // 阿里云主账号AccessKey拥有所有API的访问权限，风险很高。强烈建议您创建并使用RAM账号进行API访问或日常运维，请登录RAM控制台创建RAM账号。
  // accessKeyId: '<Your AccessKeyId>',
  // accessKeySecret: '<Your AccessKeySecret>',
  // bucket: 'Your bucket name',
});

editor.config.customUploadVideo = function (resultFiles, insertVideoFn) {
    // resultFiles 是 input 中选中的文件列表
    // insertVideoFn 是获取视频 url 后，插入到编辑器的方法
    client.put('myVideo', resultFiles[0])
      .then(function (res) {
        // 上传视频，返回结果，将视频插入到编辑器中
        insertVideoFn(res.url)
      }).catch(function (err) {
        console.log(err)
      })
}
```

更多配置请参考 [阿里云官方文档](https://help.aliyun.com/document_detail/64047.html?spm=a2c4g.11186623.6.1466.605572148P3NOZ)