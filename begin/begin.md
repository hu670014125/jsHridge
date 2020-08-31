
# onNativeBridgeReady
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

# onNativeLoad
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
        <th style="width: 200px">data</th>
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

# onNativeStart
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
        <th style="width: 200px">data</th>
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

# onNativePause
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
        <th style="width: 200px">data</th>
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

# onNativeStop
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
        <th style="width: 200px">data</th>
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

# onNativeDestroy
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
        <th style="width: 200px">data</th>
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
# onNativeResult
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
        <th style="width: 200px">data</th>
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
# onNativeMenuItemSelected
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
        <th style="width: 200px">data</th>
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

# onNativeBackListener
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
        <th style="width: 200px">data</th>
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
