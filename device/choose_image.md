# jsBridge.chooseImage(Object object)
  > 从本地相册选择图片或使用相机拍照。
  
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
        <th style="width: 100px;text-align:left">count</th>
        <th>number</th>
        <th>9</th>
        <th>否</th>
        <th style="text-align:left">
            最多可以选择的图片张数
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">sizeType</th>
        <th>Array.&lt string></th>
        <th>['original', 'compressed']</th>
        <th>否</th>
        <th style="text-align:left">
            所选的图片的尺寸
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">sourceType</th>
        <th style="width: 150px">Array.&lt string></th>
        <th>['album', 'camera']</th>
        <th>否</th>
        <th style="text-align:left">
            选择图片的来源
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

> object.sizeType 的合法值

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
        <th style="width: 200px">original</th>
        <th style="width: 200px;">string</th>
        <th style="width: 300px;">
            原图
        </th>
    </tr>
    <tr>
        <th style="width: 200px">compressed</th>
        <th style="width: 200px;">string</th>
        <th style="width: 300px;">
            压缩图
        </th>
    </tr>
    </tbody>
</table>

> object.sourceType 的合法值

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
        <th style="width: 200px">album</th>
        <th style="width: 200px;">string</th>
        <th style="width: 300px;">
            从相册选图
        </th>
    </tr>
    <tr>
        <th style="width: 200px">camera</th>
        <th style="width: 200px;">string</th>
        <th style="width: 300px;">
            使用相机
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
            <th style="width: 200px">tempFiles</th>
            <th style="width: 200px;">Array.&ltObject></th>
            <th style="width: 300px;">
                图片的本地临时文件列表
            </th>
        </tr>
    </tbody>
</table>

> res.tempFiles 的结构

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
        <th style="width: 200px">path</th>
        <th style="width: 200px;">string</th>
        <th style="width: 300px;">
            本地临时文件路径 (本地路径)
        </th>
    </tr>
    <tr>
            <th style="width: 200px">size</th>
            <th style="width: 200px;">number</th>
            <th style="width: 300px;">
                本地临时文件大小，单位 B
            </th>
        </tr>
    </tbody>
</table>

> 示例代码
```js

  jsBridge.chooseImage({
    count: 1,
    sizeType: ['original', 'compressed'],
    sourceType: ['album', 'camera'],
    success:function (res) {
      // tempFilePath可以作为img标签的src属性显示图片
      const tempFilePath = res.tempFiles[0].path;
    }
  })

```
