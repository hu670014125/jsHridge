# onNativeStop
>当前H5页面即将被关闭时主动回调，相当于android Activity生命周期中的onStop函数，用户监听页面的生命周期。
如通过navigateBack关闭当前界面、物理返回键（Android）、导航栏返回上一页时会回调该函数。


> 示例代码
```js
   window.onNativeStop = function () {
        console.log("-------->onNativeStop停止");
       
    };
```
