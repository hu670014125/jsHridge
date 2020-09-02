# jsBridge.uploadFile(Object object)
  > 将本地资源上传到服务器。客户端发起一个 HTTPS POST 请求，其中 content-type 为 multipart/form-data。
  
  > 参数 Object object

<table>
    <thead>
    <tr>
        <th>属性</th>
        <th>类型</th>
        <th>默认值</th>
        <th>必填</th>
        <th>说明</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <th style="width: 100px;text-align:left">url</th>
        <th>string</th>
        <th></th>
        <th>是</th>
        <th style="text-align:left">
            开发者服务器地址
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">filePath</th>
        <th>string</th>
        <th></th>
        <th>是</th>
        <th style="text-align:left">
            要上传文件资源的路径 (本地路径)
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">name</th>
        <th>string</th>
        <th></th>
        <th>是</th>
        <th style="text-align:left">
            上传到开发服务器的文件扩展名
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">header</th>
        <th>Object</th>
        <th></th>
        <th>否</th>
        <th style="text-align:left">
            HTTP 请求 Header，Header 中不能设置 Referer
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">formData</th>
        <th>Object</th>
        <th></th>
        <th>否</th>
        <th style="text-align:left">
            HTTP 请求中其他额外的 form data
        </th>
    </tr> 
    <tr>
        <th style="width: 100px;text-align:left">allowUploadHEIC</th>
        <th>boolean</th>
        <th></th>
        <th>否</th>
        <th style="text-align:left">
            上传的图片是heic是否上传原文件，默认不允许，会转换成jpg图片上传（只IOS有效）
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">success</th>
        <th>function</th>
        <th></th>
        <th>否</th>
        <th style="text-align:left">
            接口调用成功的回调函数
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">fail</th>
        <th>function</th>
        <th></th>
        <th>否</th>
        <th style="text-align:left">
            接口调用失败的回调函数
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">complete</th>
        <th>function</th>
        <th></th>
        <th>否</th>
        <th style="text-align:left">
            接口调用结束的回调函数（调用成功、失败都会执行）
        </th>
    </tr>
    </tbody>
</table>


> 参数 object.success 回调函数 Object res 参数

<table>
    <thead>
    <tr>
        <th>属性</th>
        <th>类型</th>
        <th>说明</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <th style="width: 200px">msg</th>
        <th style="width: 200px;">string</th>
        <th style="width: 300px;">
            接口调用说明
        </th>
    </tr>
    <tr>
        <th style="width: 200px">data</th>
        <th style="width: 200px;">string</th>
        <th style="width: 300px;">
            开发者服务器返回的数据
        </th>
    </tr>
    <tr>
        <th style="width: 200px">statusCode</th>
        <th style="width: 200px;">number</th>
        <th style="width: 300px;">
            开发者服务器返回的 HTTP 状态码
        </th>
    </tr>
    </tbody>
</table>


> 实例代码
```js
jsBridge.chooseImage({
  success (res) {
    const tempFilePaths = res.tempFiles
    jsBridge.uploadFile({
      url: 'https://example.caih.com/upload', //仅为示例，非真实的接口地址
      filePath: tempFilePaths[0],
      name: 'png',
      formData: {
        'user': 'test'
      },
      success (res){
        const data = res.data
        //do something
      }
    })
  }
})
```
