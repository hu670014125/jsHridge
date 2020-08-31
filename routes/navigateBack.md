# jsBridge.navigateBack(Object object)
关闭当前H5页面，返回上一页面或多级或者指定界面页面。
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
        <th style="width: 100px;text-align:left">data</th>
        <th style="width: 100px;">object</th>
        <th style="width: 100px;"></th>
        <th style="width: 100px;">否</th>
        <th style="text-align:left">
        要传递到上一个页面的数据，要比setResult函数优先级高
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">tag</th>
        <th>string</th>
        <th></th>
        <th>否</th>
        <th style="text-align:left">返回tag对应的原生页面，优先级高于delta</th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">delta</th>
        <th>int</th>
        <th></th>
        <th>否</th>
        <th style="text-align:left">关闭当前H5页面，返回一级页面或多级原生页面，如果delta大于当前页面堆栈则返回原生H5页面首次</th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">success</th>
        <th>function</th>
        <th> </th>
        <th>否</th>
        <th style="text-align:left">
            接口调用成功的回调函数
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">fail</th>
        <th>function</th>
        <th> </th>
        <th>否</th>
        <th style="text-align:left">
            接口调用失败的回调函数
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">complete</th>
        <th>function</th>
        <th> </th>
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
    </tbody>
</table>

> 示例代码
```js
        jsBridge.navigateBack({
            delta: 1,
            data: user,
            success: function (res) {

            }, fail: function (res) {

            }, complete: function (res) {
            }
        });
```
