# jsBridge.removeMenu(Object object)
> 删除当前页面原生导航栏右侧`指定的`菜单，当自定义页面时该方法无效，因为自定义页面时原生导航栏不显示。

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
        <th style="width: 100px;text-align:left">menu</th>
        <th>Menu</th>
        <th> </th>
        <th>是</th>
        <th style="text-align:left">
            正在显示的菜单列表项
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

> 参数 Menu object
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
        <th style="width: 200px">text</th>
        <th style="width: 200px;">string</th>
        <th style="width: 300px;">
            菜单名称
        </th>
    </tr>
     <tr>
            <th style="width: 200px">icon</th>
            <th style="width: 200px;">string</th>
            <th style="width: 300px;">
                菜单显示内置图标，不支持自定义，目前仅支持：add、search、sacn、more，如果其他以外的值这显示text中的文本
            </th>
        </tr>
        <tr>
                    <th style="width: 200px">ifRoom</th>
                    <th style="width: 200px;">boolean</th>
                    <th style="width: 300px;">
                        如果设置为true时自动排在菜单栏前面
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

     jsBridge.removeMenu({
                menu: {
                    text: "添加",
                    icon: "add",
                    ifRoom:true
                },
                success: function (res) {
    
                    console.log("----success", res);
    
                }, fail: function (res) {
                    console.log("----fail", res);
                }, complete: function (res) {
                    console.log("----complete", res);
                }
            });
```
