# onNativeMenuItemSelected
>当点击原生页面的导航栏按钮时回调该函数。`通过jsBridge.addMenu(Object object)添加导航栏菜单`

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
                菜单图标名称
            </th>
        </tr>
        <tr>
                    <th style="width: 200px">ifRoom</th>
                    <th style="width: 200px;">boolean</th>
                    <th style="width: 300px;">
                        是否自动排列在前面
                    </th>
                </tr>
    </tbody>
</table>

> 示例代码
```js
  window.onNativeMenuItemSelected = function (params) {
        console.log(params);
        alert('你点击了：' + params.text);
    };
```
