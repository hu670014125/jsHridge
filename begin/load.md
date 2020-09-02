# window.onNativeLoad(Object object)
 > H5页面开始加载时主动回调，相当于android Activity生命周期中的onLoad函数，但是不等价，<br>
   用于监听H5页面的生命周期 `在html的onLoad 之前执行。`

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
    window.onNativeLoad = function (params) {
        console.log("-------->onNativeLoad接收参数：",params);
    };
```
