# window.onNativeBridgeReady(Object object)
 > H5和本地通信建立完成后主动回调,H5要调用的所有的本地方法需要在onNativeBridgeReady之后调<br>
用才生效，onNativeBridgeReady执行完成后会在Window对象中注入jsBridge对象，H5调用本地原<br>
生的所有方法都是通过该对象调用。`在html的onLoad 之前执行。`

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
        <th style="width: 200px">jsBridge</th>
        <th style="width: 200px;">Object</th>
        <th style="width: 300px;">
            调用原生本地的对象
        </th>
    </tr>
    </tbody>
</table>

> 示例代码
```js
    window.onNativeBridgeReady = function (jsBridge) {
        console.log("--------->onNativeBridgeReady通信建立");
        jsBridge.setTitle({text:'H5'});
        
    };
```
