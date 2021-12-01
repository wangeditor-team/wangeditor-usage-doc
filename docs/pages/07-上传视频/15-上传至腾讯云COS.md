# 上传至腾讯云COS

首先，在腾讯云控制台[创建存储桶](https://cloud.tencent.com/document/product/436/13309)，配置好[跨域规则](https://cloud.tencent.com/document/product/436/13318)。

结合[自己实现上传功能](https://www.wangeditor.com/doc/pages/07-%E4%B8%8A%E4%BC%A0%E8%A7%86%E9%A2%91/11-%E8%87%AA%E5%AE%9A%E4%B9%89%E4%B8%8A%E4%BC%A0%E5%8A%9F%E8%83%BD.html)和[COS js-sdk](https://cloud.tencent.com/document/product/436/11459)来实现腾讯云COS的上传。

```js
// SecretId和SecretKey需要去腾讯云控制台获取
let cos = new COS({
    SecretId: 'AKID*****************************',
    SecretKey: '********************************'
});

editor.config.customUploadVideo = function (resultFiles, insertVideoFn) {
    const file = resultFiles[0];            
    cos.sliceUploadFile({
        Bucket: '***', // 存储桶名称
        Region: '***', // 存储桶地域
        Key:  file.name, // 文件名称
        Body: resultFiles[0], // 文件
    }, function (err, data) {
        if(err) {
            console.log(err);
            return;
        }
        insertVideoFn('//'+data.Location); // 插入返回的url地址
    });        
};

```

更多腾讯云COS相关信息可参考 [腾讯云对象存储官方文档](https://cloud.tencent.com/document/product/436)