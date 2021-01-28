# 上传至阿里云OSS

利用[自己实现上传功能](https://doc.wangeditor.com/pages/07-%E4%B8%8A%E4%BC%A0%E5%9B%BE%E7%89%87/11-%E8%87%AA%E5%B7%B1%E5%AE%9E%E7%8E%B0%E4%B8%8A%E4%BC%A0%E5%8A%9F%E8%83%BD.html)来实现阿里云OSS的上传

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

editor.config.customUploadImg = function (resultFiles, insertImgFn) {
    // resultFiles 是 input 中选中的文件列表
    // insertImgFn 是获取图片 url 后，插入到编辑器的方法
    client.put('myImg', resultFiles[0])
      .then(function (res) {
        // 上传图片，返回结果，将图片插入到编辑器中
        insertImgFn(res.url)
      }).catch(function (err) {
        console.log(err)
      })
}
```

更多配置请参考 [阿里云官方文档](https://help.aliyun.com/document_detail/64047.html?spm=a2c4g.11186623.6.1466.605572148P3NOZ)