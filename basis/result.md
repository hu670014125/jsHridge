# setResult(Object object)
> 可设置当当前页面关闭后要带上一个页面的数据，`setResult`的优先级低于`navigateBack`中的data，也就是说如果通过`setResult`设置返回数据时，再通过`navigateBack`
  关闭当前页面时传递数据到上一个页面时之前`setResult`设置的数据将会被覆盖。通过`setResult`设置数据后会在：点击设备返回键（android）、点击导航栏返回键、侧滑关闭、`navigateBack`（不设置data字段），时传入上一个页面。

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
        <th>object</th>
        <th></th>
        <th>是</th>
        <th style="text-align:left">
            要返回上个页面的数据
        </th>
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

> 示例代码
```js
     jsBridge.setResult({
            data: {
                name: "李四1",
                age: "32-1",
                sex: "男-1",
                msg: "setResult中的参数-1",
            },
            success: function (res) {
                console.log("----success:", res);

            }, fail: function (res) {
                console.log("----fail:", res);
            }, complete: function (res) {
                console.log("----complete:", res);
            }
        });

     // 上一个页面接收数据
     window.onNativeLoad = function (params) {
        console.log("-------->onNativeLoad接收参数：",params);
      };
```
