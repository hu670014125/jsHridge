# window.onNativeResult(Object object)
 > 当上个页面关闭并返回当前页面时主动回调该函数，相当于android Activity生命周期中的onResult函数，用于获从上一个页面传递过来的数据。
>` 上一个页面是否主动传递数据该函数都回调，如果上个页面传递不主动传递数据，默认为JavaScript 的空对象，即：{}`
 
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
            上个页面传递参数
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
