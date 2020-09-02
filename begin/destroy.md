# window.onNativeDestroy
>当前H5页面即将销毁时主动回调，相当于android Activity生命周期中的onDestroy函数，用户监听页面的生命周期。
当关闭原始页面后原生页面内存即将释放时回调。


> 示例代码
```js
   window.onNativeDestroy = function () {
        console.log("-------->onNativeDestroy页面销毁");
       
    };
```
