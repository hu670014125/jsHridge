# onNativePause
>当前H5页面切换到后台运行或者页面不可见时主动回调，相当于android Activity生命周期中的onPause函数，用户监听页面的生命周期。
如当前A页面打开B页面或者切换到后台（Android 点击home键，IOS切换到后台运行）时，会回调该函数。


> 示例代码
```js
    window.onNativePause = function () {
         console.log("-------->onNativePause暂停");
       
     };
```
