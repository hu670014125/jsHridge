# jsBridge.imageToBase64(Object object)
  > 将本地临时文件路径 (本地路径)的图片，转换成base64编码。
  
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
           本地临时文件路径 (本地路径)
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">quality</th>
        <th>number</th>
        <th>80</th>
        <th>否</th>
        <th style="text-align:left">
            图片转换的质量，在10-100区间，quality数值越小转换后的base64编码越小
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
                base64编码的图片，不包含头部信息（如：data:img/jpg;base64,）
            </th>
        </tr>
    </tbody>
</table>


> 实例代码
```js
 jsBridge.imageToBase64({
            url: imageUrl,
            quality: 30,
            success: function (res) {
                console.log(res);
            },
            fail: function (res) {
                console.log("----------->图片转失败");
                console.log(res)
            },
            complete: function (res) {
                console.log("----------->图片转完成");
                console.log(res)
            }
        });
```
