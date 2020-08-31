# onNativeBackListener
> 原生页面点击状态栏的返回键和物理返回键（Android）时回调该函数，默认是不开启回调的，通过` jsBridge.addBackListener()`开启监听系统返回键，
  若开启返回键监听后当前页面的状态栏返回键、侧滑关闭、物理返回键（Android）将失效，不再处理内部的返回事件，`注意:开启系统返回键监听后不能移除`
  其他界面不受到影响。


> 示例代码
```js
    window.onNativeBridgeReady = function (jsBridge) {
        // 开启系统返回键监听
        jsBridge.addBackListener();
    };

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
