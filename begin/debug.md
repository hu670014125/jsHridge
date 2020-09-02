
# 开启调试模式
 > 开启调试模式，只能开启当前的页面，不能全局开启。开启调试模式后在右下角显示`vconsole(微信提供)`。
   <br>在HTML的head中添加`<meta name="debug" content="true"/> `来开启。

> 示例代码
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="debug" content="true"/>
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0"/>
    <title>xxxx</title>
  </head>
  <body>
     <div >
     xxxx
     </div>
  </body>
</html>

```
