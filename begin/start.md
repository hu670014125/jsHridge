# onNativeStart(Object object)
>H5页面进入运行阶段时主动回调，相当于android Activity生命周期中的onStart函数，用户监听页面的生命周期。

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
        <th style="width: 200px">params</th>
        <th style="width: 200px;">Object</th>
        <th style="width: 300px;">
            通过url传递过来的参数
        </th>
    </tr>
    </tbody>
</table>

> 示例代码
```js
    window.onNativeStart = function (params) {
            console.log("-------->onNativeStart正在运行",params);
    };
```
