# 框架分析对比

> 框架支持情况

|  框架   | Android、IOS统一  | 生命周期  | 函数回调  |原生导航栏  |自定义界面|
|  ----  | :----:  |:----:  |:----:  |:----:  |:----:  |
| 航交所  | × |× |× |× |√ |
| Bridge | √ |√ |√ |√ |√ |

> 框架支持调试和自适应

|  框架   | debug  | H5自适应 | 
|  ----  | :----:  |:----:  |
| 航交所  | × |× |
| Bridge | √ |√ |

> 框架技术栈

|  框架   | Android | IOS  | H5本地通信(10平均值)  |是否丢包  |支持系统版本|
|  ----  | :----:  |:----:  |:----:  |:----:  |:----:  |
| 航交所  |X5WebView |WKWebView |4ms |IOS高并发丢包 |Android2.3、IOS 10 |
| Bridge |WebView |WKWebView |2.7ms |不丢包 |Android5.0、IOS 9 |

> 本地通信耗时计算规则：使用Android项目，使用同一台设备，H5调用10本地，求平均值。

> 航交所Android提供的原生方法

|  序号   | 名称 | 参数  |说明  |
|  ----  | :----  |:----:  |:----:|
| 1  |closeActivity | |关闭界面 |
| 2 |getLocalUserJson | |获取用户JSON |
| 3 |openNewWebPage | String url, String title, boolean hasTopTitle|打开新界面 |
| 4 |openNewWebPage |String url, String title, boolean hasTopTitle, String rightButton |打开新界面 |
| 5 |appRefreshLogin | |刷新登录 |
| 6 |startQrScan | |打开扫一扫 |
| 7 |openShipPage | |打开船舶地图信息页面 |
| 8 |saveWebImage | String url, String fileName|保存网络图片|
| 9 |setBlockBackPress |boolean isBlock  |未知 |
| 10 |doWebGoBack ||返回上一页（web）  |
| 11 |shareFile |String url, String fileName |分享|
| 12 |openFile | String url, String fileName|打开文件 |
| 13 |openWithOtherApp |String url, String fileName |Intent 打开文件 |
| 14 |loadFileByType | String url, String fileName, int type|未知 |
| 15 |showTitleBar | String title, String rightButton|未知 |
| 16 |showTitleBar | String title, String rightButton, String shareUrl |未知 |
| 17 |changeShareUrl |String newUrl |未知 |
| 18 |setTitleBarShow |boolean show |未知 |
| 19 |resetTitleBar |String title |未知 |
| 20 |getUuid | |获取Uuid |

> 航交所IOS提供的原生方法

|  序号   | 名称 | 参数  |说明  |
|  ----  | :----  |:----:  |:----:|
| 1  |closeActivity | |关闭界面 |
| 2 |getLocalUserJson | |获取用户JSON |
| 3 |openNewWebPage | String url, String title, boolean hasTopTitle|打开新界面 |
| 4 |appRefreshLogin | |刷新登录 |
| 5 |`saveWebImage` | String url, String fileName|保存网络图片|
| 6 |`shareFile` |String url, String fileName |分享|
| 7 |`openFile` | String url, String fileName|打开文件 |
| 8 |`openWithOtherApp` |String url, String fileName |Intent 打开文件 |

> 航交所实例代码

 ```js

/**
 * Created by COMIT-ZQ on 2016/12/1.
 */
var initJsBridge=function(){
    //alert("qrcode_android");
    $("#qrcode_buttons").click(function(){
        var loginInfo=waterApp.getLoginInfo();
        var callbackp={"key":""};
        if(loginInfo!=null){
            var department=loginInfo.login_department;
            var loginUser=loginInfo.login_code;
            var entId=loginInfo.login_department;
            var planId=0;
            if($("#planId").val()!=undefined){
                planId=$("#planId").val();
            }
            var callbackValue="&department="+department;
            callbackValue+="&loginUser="+loginUser;
            callbackValue+="&entId="+entId;
            callbackValue+="&planId="+planId;
            callbackp={"key":callbackValue};
        }else{
            var callbackValue="&department=0";
            callbackValue+="&loginUser=0";
            callbackValue+="&entId=0";
            callbackValue+="&planId=0";
            callbackp={"key":callbackValue};
        }
        if(window.jsBridge && window.jsBridge.mpTestObjcCallBack){
            var sss=JSON.stringify(callbackp);
            window.jsBridge.mpTestObjcCallBack(sss);
            console.debug("二维码扫描：mpTestObjcCallBack");
        }
    });
    //行业互动
    $(".chat_buttons").click(function(){
        //alert("chat_buttons_click");
        var loginType=waterApp.checkLoginType();
        var loginInfo=waterApp.getLoginInfoOnly();
        if(loginInfo==null){
            return;
        }
        var hxLoginName="";
        if(loginType=="1"){
            hxLoginName+="water_gl_"+loginInfo.login_code;
        }else if(loginType=="2"){
            hxLoginName+="water_ent_"+loginInfo.login_code;
        }else{
            return;
        }

        var nativeObject={};
        nativeObject.action="chat";
        nativeObject.username=hxLoginName.toLowerCase();
        nativeObject.password="123456";
        nativeObject.create_group=loginInfo.create_group;
        var callbackp=JSON.stringify(nativeObject);
        //alert("chat_buttons"+callbackp);
        if(window.jsBridge && window.jsBridge.chat){
            window.jsBridge.chat(callbackp);
            clearNoRead();
        }
    });
    //$("#share_buttons").click(function(){
    //    var url=$(this).data("url");
    //    var title=$(this).data("title");
    //    var description=$(this).data("description");
    //    youmengShare(title,description,url);
    //});

    $("header").delegate("#share_buttons", "click", function () {
        var url=$(this).data("url");
        var title=$(this).data("title");
        var description=$(this).data("description");
        //alert("share_buttons_click="+url+title+description);
        youmengShare(title,description,url,"share");
    });
    $("header").delegate("#share_text_buttons", "click", function () {
        //var url=$(this).data("url");
        var title=$(this).data("title");
        var description=$(this).data("description");
        //alert("share_buttons_click="+url+title+description);
        youmengShare(title,description,"","shareText");
    });
    $("header").delegate("#share_file_buttons", "click", function () {
        var url=$(this).data("url");
        var title=$(this).data("title");
        var description=$(this).data("description");
        //alert("share_buttons_click="+url+title+description);
        youmengShare(title,description,url,"shareFile");
    });

    $("header").delegate("#open_web_page", "click", function () {
        var url=$(this).data("url");
        var title=$(this).data("title");
        var cacscreen=$(this).data("cacscreen");
        if(cacscreen==null){
            cacscreen=false;
        }
        var canzoom=$(this).data("canzoom");
        if(canzoom==null){
            canzoom=false;
        }
        console.debug(url);
        console.debug(encodeURI(url));
        if(window.jsBridge && window.jsBridge.openWebPage){
            window.jsBridge.openWebPage(encodeURI(url),title,cacscreen,canzoom);
        }
    });
    $("#open_ship_location_page").click(function () {
        var mmsi=$(this).data("mmsi");
        console.debug("open_ship_location_page click"+mmsi);
        if(window.jsBridge && window.jsBridge.openShipPage){
            console.debug("open_ship_location_page call"+mmsi);
            window.jsBridge.openShipPage(mmsi);
        }
    });
    
    $("#saoyisao").click(function(){
    	if(window.jsBridge && window.jsBridge.startQrScan){
            window.local.startQrScan();
            console.debug("打开扫描：startQrScan");
        }
    });
    
    $("#openNewWebPage").click(function(){
    	if(window.jsBridge && window.jsBridge.openNewWebPage){
            //window.local.startQrScan();
    		var newUrl=$(this).data("newUrl");
    		var title=$(this).data("title");
    		var hasTopTitle=$(this).data("hasTopTitle");
    		//alert(newUrl);alert(title);alert(hasTopTitle);
    		window.jsBridge.openNewWebPage(newUrl,title,hasTopTitle);
            console.debug("新打开窗口");
        }
    });
    //打开地图
    /*var openMap = function(msi){

    	if(window.jsBridge && window.jsBridge.openShipPage){
            window.local.openShipPage(msi);
            console.debug("打开地图：openShipPage");
        }
    }*/

    $("#login_buttons").click(function(){
        hxLogin();
        $("#noread_buttons").click();
    });
    $("#logout_buttons").click(function(){
        hxLogout();
    });
    $("#noread_buttons").click(function(){
        if(window.jsBridge && window.jsBridge.unreadMessage){
            window.jsBridge.unreadMessage();
        }
    });

    $("#login_page_button").click(function(e){
        e.preventDefault();
        if(window.jsBridge && window.jsBridge.restartLoginPage){
            window.jsBridge.restartLoginPage();
            console.debug("打开登录页面：restartLoginPage");
        }
    });

    //刷新登录状态
    $("#refresh_login_button").click(function(e){
        e.preventDefault();
        if(window.jsBridge && window.jsBridge.appRefreshLogin){
            window.jsBridge.appRefreshLogin();
            console.debug("刷新登录状态：appRefreshLogin");
        }
    });

    //退出activity
    $("#quit_button").click(function(){
        if(window.jsBridge && window.jsBridge.closeActivity){
            window.jsBridge.closeActivity();
            console.debug("关闭页面：closeActivity");
        }
    });
    
  //退出activity
   /* $("#saoyisao").click(function(){
        if(window.jsBridge && window.jsBridge.closeActivity){
            window.jsBridge.closeActivity();
            console.debug("关闭页面：closeActivity");
        }
    });*/
    /**
     * 获取用户信息
     */
    //alert("getAppUser_buttons_init");
    $("#getAppUser_buttons").click(function(){
        //alert("getAppUser_buttons_1");
        if(window.local && window.local.getLocalUserJson){
            //alert("getAppUser_buttons_2");
            window.local.getLocalUserJson();
            //alert("getAppUser_buttons_3");
        }
    });
    $("#updateAppUser_buttons").click(function(){
        if(window.local && window.local.refreshLocalUserJson){
            window.local.refreshLocalUserJson();
            console.debug("更新用户信息：refreshLocalUserJson");
        }
    });
    /**
     * 获取定位信息
     * */
    $("#location_button").click(function(){
        if(window.local && window.local.getCurrentLocation){
            window.local.getCurrentLocation();
            console.debug("获取位置信息：getCurrentLocation");
        }
    });

    if(window.local && window.local.getLocalUserJson){
        window.local.getLocalUserJson();
        console.debug("获取用户信息：getLocalUserJson");
    }
    
    
    $("#scanButton").click(function(){
        //alert("getAppUser_buttons_1");
        if(window.local && window.local.getLocalUserJson){
            //alert("getAppUser_buttons_2");
            window.local.startQrScan();
            //alert("getAppUser_buttons_3");
        }
    });
    
   /* $("#scanButton").click(function(){
        //alert("getAppUser_buttons_1");
        if(window.local && window.local.getLocalUserJson){
            //alert("getAppUser_buttons_2");
            
            //alert("getAppUser_buttons_3");
        }
    });*/

    //try{
    //    if(initPage){
    //        var loginKey = localStorage.getItem("loginKey");
    //        if(loginKey==null){
    //            window.setTimeout(function(){
    //                initPage();
    //            },1000);
    //        }else{
    //            initPage();
    //        }
    //    }
    //}catch(ex){
    //
    //}

    $("#save_web_image_button").click(function(e){
        e.preventDefault();
        if(window.jsBridge && window.jsBridge.saveWebImage){
            let url = $(this).data("url");
            let fileName = $(this).data("fileName");
            window.jsBridge.saveWebImage(url, fileName);
            console.debug("保存图片：saveWebImage");
        }
    });

    $("#open_file_button").click(function(){
    	if(window.jsBridge && window.jsBridge.openFile){
    		let url = $(this).data("url");
    		let fileName = $(this).data("fileName");
    		window.jsBridge.openFile(url, fileName);
        }
    });

    $("#share_file_button").click(function(){
    	if(window.jsBridge && window.jsBridge.shareFile){
    		let url = $(this).data("url");
    		let fileName = $(this).data("fileName");
    		window.jsBridge.shareFile(url, fileName);
        }
    });

    //用其它应用打开文件
    $("#open_with_other_app_button").click(function(){
    	if(window.jsBridge && window.jsBridge.openWithOtherApp){
    		let url = $(this).data("url");
    		let fileName = $(this).data("fileName");
    		window.jsBridge.openWithOtherApp(url, fileName);
        }
    });

    //不同方式加载文件
    //type 1:app内打开，2:弹出分享，3:弹出第三方打开，4:弹出第三方打开图片
    $("#load_file_by_type_button").click(function(){
    	if(window.jsBridge && window.jsBridge.loadFileByType){
    		let url = $(this).data("url");
            let fileName = $(this).data("fileName");
            let type = $(this).data("type");
    		window.jsBridge.loadFileByType(url, fileName, type);
        }
    });

    //处理输入框被软键盘遮挡的问题
    window.addEventListener("resize", function() {
        if(document.activeElement.tagName=="INPUT" || document.activeElement.tagName=="TEXTAREA") {
           window.setTimeout(function() {
              document.activeElement.scrollIntoViewIfNeeded();
           },0);
        }
    });
};

/**
 * 设置用户信息回调方法
 * @param userJsonStr
 */
var getParamFromLocal=function(userJson){
    console.debug("获取用户信息返回:getParamFromLocal:");
    //localStorage.setItem("loginKey",jsonStr);
    waterApp.setLoginInfo(userJson);
    try{
        if(initPage){
            initPage();
        }
    }catch (ex){

    }
};
/**
 * 获取定位信息回调方法
 * */
var getCurrentLocationCallBack=function(locationJson){
    try{
        if(locationJson.address){
            //如果获取不到位置信息，则取上一次成功获取的位置
            var jsonStr=JSON.stringify(locationJson);
            localStorage.setItem("locationKey",jsonStr);
        }
        console.debug("获取定位信息返回:getCurrentLocation:");
        if(pageLocationCallBack){
            //如果页面有获取位置的回调，则把位置对象伟过去处理
            pageLocationCallBack(waterApp.getCurrentLocation());
            console.debug("获取定位信息返回成功:getCurrentLocation:");
        }
        //alert(jsonStr);
    }catch (ex){
        //alert("获取定位失败:"+ex.toString());
    }
};

/**
 * 环信登录
 */
var hxLogin=function(){
    var loginType=waterApp.checkLoginType();
    var loginInfo=waterApp.getLoginInfoOnly();
    if(loginInfo==null){
        return;
    }
    var hxLoginName="";
    if(loginType=="1"){
        hxLoginName+="water_gl_"+loginInfo.login_code;
    }else if(loginType=="2"){
        hxLoginName+="water_ent_"+loginInfo.login_code;
    }else{
        return;
    }

    var nativeObject={};
    nativeObject.action="login";
    nativeObject.username=hxLoginName.toLowerCase();
    nativeObject.password="123456";
    nativeObject.create_group=loginInfo.create_group;
    var callbackp=JSON.stringify(nativeObject);
    //alert("hxLogin"+callbackp);
    if(window.jsBridge && window.jsBridge.login){
        window.jsBridge.login(callbackp);
    }
};
/**
 * 环信帐号退出
 */
var hxLogout=function(){
    var loginType=waterApp.checkLoginType();
    if(loginType=="1" || loginType=="2"){
        if(window.jsBridge && window.jsBridge.logout){
            window.jsBridge.logout();
        }
    }
};

/**
 * 分享
 * @param title
 * @param description
 * @param url
 */
var youmengShare=function(title,description,url,type){
    if($.trim(type) == ''){
        console.error("分享类型type不能为空");
        return;
    }
    var nativeObject={};
    if(type=="share"){
        nativeObject.action="share";
    }else if(type=="shareText"){
        nativeObject.action="shareText";
    }else if(type=="shareFile"){
        nativeObject.action="shareFile";
    }else{
        console.error("分享类型type="+type);
        return;
    }

    nativeObject.url=url;
    nativeObject.title=title;
    nativeObject.description=description;
    var callbackp=JSON.stringify(nativeObject);

    if(type=="share"){
        if(window.jsBridge && window.jsBridge.share){
            window.jsBridge.share(callbackp);
            console.debug("友盟分享：share");
        }
    }else if(type=="shareText"){
        if(window.jsBridge && window.jsBridge.shareText){
            window.jsBridge.shareText(callbackp);
            console.debug("友盟分享：shareText");
        }
    }else if(type=="shareFile"){
        if(window.jsBridge && window.jsBridge.shareFile){
            window.jsBridge.shareFile(callbackp);
            console.debug("友盟分享：shareFile");
        }
    }

};
/**
 * 新消息提醒
 * @param text
 */
var hasNewMessageCallBack=function(text){
    //alert("收到新消息:"+text);
    if(text!="0"){
        $('.chat_red_point').css("left",$('.chat_red_point').parent().width()+$('.chat_red_point').parent().position().left-5)
        $(".chat_red_point").html(text).fadeIn();
    }

};
/**
 * 未读消息回调
 * @param numCount
 */
var unreadMessageCallBack=function(numCount){
    //alert("未读消息:"+numCount);
    if(numCount!="0"){
        $('.chat_red_point').css("left",$('.chat_red_point').parent().width()+$('.chat_red_point').parent().position().left-5)
        $(".chat_red_point").html(numCount).fadeIn();
    }
};

/**
 * 主动获取未读消息
 */
var getUnreadMessage=function(){
    var loginType=waterApp.checkLoginType();
    if(loginType=="1" || loginType=="2"){
        if(window.jsBridge && window.jsBridge.unreadMessage){
            window.jsBridge.unreadMessage();
        }
    }

};

/**
 * 友盟页面统计
 * @param pageType
 */
umengLog=function(pageType){
    if(window.jsBridge && window.jsBridge.beginTrackCallBack && window.jsBridge.endTrackCallBack){
        window.jsBridge.beginTrackCallBack(pageType);
        window.jsBridge.endTrackCallBack(pageType);
    }
};

initJsBridge();

```
