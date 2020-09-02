# jsBridge.addBackListener(Object object)
> 添加原生返回键监听。
  若开启返回键监听后当前页面的状态栏返回键、侧滑关闭、物理返回键（Android）将失效，不再处理内部的返回事件，`注意:开启系统返回键监听后不能移除`
  其他界面不受到影响。

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

         // 开启系统返回键监听
          jsBridge.addBackListener({
              success: function (res) {
                  console.log("----success:", res);
              }, fail: function (res) {
                  console.log("----fail:", res);
              }, complete: function (res) {
                  console.log("----complete:", res);
              }
          });

     // 点击返回键时回调该函数
        window.onNativeBackListener = function (text) {
            console.log("--------->onNativeBackListener");
            if (confirm("你确定要退出吗？")) {
                jsBridge.navigateBack();
            } else {
                alert("点击了取消");
            }
        }
```
