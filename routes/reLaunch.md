# jsBridge.reLaunch(Object object)

 关闭所有H5页面，打开一个H5的页面。<br>
 如：`A->B->C->D`,此时页面堆栈为：`[A、B、C、D]`，当使用jsBridge.reLaunch打开新页面`F`时页面堆栈变为：`[F]`

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
        <th style="width: 100px;text-align:left">url</th>
        <th style="width: 100px;">string</th>
        <th style="width: 100px;"></th>
        <th style="width: 100px;">是</th>
        <th style="text-align:left">要显示的H5 URL地址。参数与路径之间使用 ? 分隔，参数键与参数值用 = 相连，不同参数用 & 分隔；如
            'path?key=value&key2=value2'
        </th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">title</th>
        <th>string</th>
        <th></th>
        <th>是</th>
        <th style="text-align:left">原生界面要显示标题</th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">tag</th>
        <th>string</th>
        <th>当前界面首次加载的URL</th>
        <th>否</th>
        <th style="text-align:left">设置当前页面的标签。通过navigateBack返回到指定界面</th>
    </tr>
    <tr style="width: 100px;text-align:left">
        <th>menus</th>
        <th>list&lt;Menu></th>
        <th>[]</th>
        <th>否</th>
        <th style="text-align:left">原生界面顶部导航栏右侧菜单列表。菜单支持多个，如果菜单列表<=3个时全部显示（排成一排）。如果>3个时，从第三个菜单开始溢出显示（即下拉列的方式显示）</th>
    </tr>
    <tr>
        <th style="width: 100px;text-align:left">navigationStyle</th>
        <th>string</th>
        <th>default</th>
        <th>否</th>
        <th style="text-align:left">
            设置原生界面标题导航栏的样式，default(默认，带系统标题栏)、custom(自定义，不带系统标题栏)。如果navigationStyle="custom"时title、menus 等字段无效
        </th>
    </tr >
    <tr>
        <th style="width: 100px;text-align:left">navigationBarTextStyle</th>
        <th>string</th>
        <th>black</th>
        <th>否</th>
        <th style="text-align:left">
            设置标题导航栏的字体样式，只支持black（黑色）、white（白色）
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
    jsBridge.reLaunch({
        title: "黑色主题",
        url: "https://m.baidu.com",
        tag: 'home',
        menus: [
            {text: "添加", icon: "add", ifRoom: true},
            {text: "搜索", icon: "search"}
        ],
        navigationBarTextStyle: "black",
        navigationBarColor: "#FFFFFF",
        success: function (res) {
            console.log(res)
        },
        fail: function (res) {
            console.log(res)
        }
        , complete: function (res) {
            console.log(res)
        }
    });
```
