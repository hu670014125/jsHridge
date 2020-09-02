# jsBridge.scanCode(Object object)
  > 调起客户端扫码界面进行扫码
  
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
        <th style="width: 100px;text-align:left">onlyFromCamera</th>
        <th>boolean</th>
        <th>false</th>
        <th>否</th>
        <th style="text-align:left">
            是否只能从相机扫码，不允许从相册选择图片
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">scanType</th>
        <th>Array.&ltstring></th>
        <th>['barCode', 'qrCode']</th>
        <th>否</th>
        <th style="text-align:left">
            扫码类型
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

> object.scanType 的合法值

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
        <th style="width: 200px">barCode</th>
        <th style="width: 200px;">string</th>
        <th style="width: 300px;">
            一维码
        </th>
    </tr>
    <tr>
        <th style="width: 200px">qrCode</th>
        <th style="width: 200px;">string</th>
        <th style="width: 300px;">
            二维码
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
        <th style="width: 200px">result</th>
        <th style="width: 200px;">string</th>
        <th style="width: 300px;">
            所扫码的内容
        </th>
    </tr>
    <tr>
        <th style="width: 200px">scanType</th>
        <th style="width: 200px;">string</th>
        <th style="width: 300px;">
           所扫码的类型
        </th>
    </tr>
    </tbody>
</table>

> res.scanType 的合法值

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
         <th style="width: 200px">QR_CODE</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
             二维码
         </th>
     </tr>
     <tr>
         <th style="width: 200px">AZTEC</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            一维码
         </th>
     </tr>     
     <tr>
         <th style="width: 200px">CODABAR</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            一维码
         </th>
     </tr>     
     <tr>
         <th style="width: 200px">CODE_39</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            一维码
         </th>
     </tr>     
     <tr>
         <th style="width: 200px">CODE_93</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            一维码
         </th>
     </tr>     
     <tr>
         <th style="width: 200px">CODE_128</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            一维码
         </th>
     </tr>     
     <tr>
         <th style="width: 200px">DATA_MATRIX</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            二维码
         </th>
     </tr>     
     <tr>
         <th style="width: 200px">EAN_8</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            一维码
         </th>
     </tr>     
     <tr>
         <th style="width: 200px">EAN_13</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            一维码
         </th>
     </tr>     
     <tr>
         <th style="width: 200px">ITF</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            一维码
         </th>
     </tr>     
     <tr>
         <th style="width: 200px">MAXICODE</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            一维码
         </th>
     </tr>     
     <tr>
         <th style="width: 200px">PDF_417</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            二维码
         </th>
     </tr>
     <tr>
         <th style="width: 200px">RSS_14</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            一维码
         </th>
     </tr>
     <tr>
         <th style="width: 200px">RSS_EXPANDED</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            一维码
         </th>
     </tr>
     <tr>
         <th style="width: 200px">UPC_A</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            一维码
         </th>
     </tr>
     <tr>
         <th style="width: 200px">UPC_EAN_EXTENSION</th>
         <th style="width: 200px;">string</th>
         <th style="width: 300px;">
            一维码
         </th>
     </tr>
     </tbody>
 </table>

> 实例代码
```js
// 允许从相机和相册扫码
jsBridge.scanCode({
  success:function(res) {
    console.log(res)
  }
})

// 只允许从相机扫码
jsBridge.scanCode({
  onlyFromCamera: true,
  success:function(res) {
    console.log(res)
  }
})
```
