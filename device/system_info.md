# jsBridge.getSystemInfo(Object object)
> 获取系统信息

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
        <th style="width: 200px">pixelRatio</th>
        <th style="width: 200px;">number</th>
        <th style="width: 300px;">
            设备像素比
        </th>
    </tr>
    <tr>
        <th style="width: 200px">screenWidth</th>
        <th style="width: 200px;">number</th>
        <th style="width: 300px;">
            屏幕宽度，单位px
        </th>
    </tr>
        <tr>
        <th style="width: 200px">screenHeight</th>
        <th style="width: 200px;">number</th>
        <th style="width: 300px;">
            屏幕高度，单位px
        </th>
    </tr>        
        <tr>
        <th style="width: 200px">statusBarHeight</th>
        <th style="width: 200px;">number</th>
        <th style="width: 300px;">
            状态栏高度，单位px
        </th>
    </tr>        
    <tr>
        <th style="width: 200px">toolbarHeight</th>
        <th style="width: 200px;">number</th>
        <th style="width: 300px;">
            导航栏高度，单位px
        </th>
    </tr>
    </tbody>
</table>

> 实例代码
```js
      jsBridge.getSystemInfo({
            success: function (res) {
                console.log(res);
                console.log('-------->获取系统信息成功');
                var toolbarHeight = res.toolbarHeight/res.pixelRatio;
                var statusBarHeight = res.statusBarHeight/res.pixelRatio;
                 $("#status-bar").height(toolbarHeight+statusBarHeight-22);

            },
            fail: function (res) {
                console.log(res);
                console.log('-------->获取系统信息失败');
            },
            complete:function(res) {
                console.log(res);
                console.log('-------->获取系统信息完成');
            }
        });
```
