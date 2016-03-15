#微信js-sdk开发环境快速搭建

> 前往<a href="http://weixin.cniotroot.cn">微信js-sdk开发者服务平台<a/>注册后，添加公众号信息，并配置好域名和ip，把域名添加到你的公众号后台的安全域名。

## 获得你的微信js-sdk配置接口,例如：
```js
http://weixin.cniotroot.cn/api/jssdk/********NzQ2LjA
```

## 开发你的H5界面，并使用接口快速获取js-sdk环境配置,eg:
```HTML
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>sample</title>
</head>
<body>
  
</body>
<script src="//cdn.bootcss.com/jquery/1.11.3/jquery.min.js"></script>
<script src="http://res.wx.qq.com/open/js/jweixin-1.0.0.js"></script>
<script>
$.ajax({
    type:'GET',
	//window.location.href是动态获取当前页面的url，不能写死，因为分享的时候微信会给你拼接东西
    url:'http://weixin.cniotroot.cn/api/jssdk/********NzQ2LjA'+'?url='+window.location.href,
    error:function(){
        console.log('出错');
        alert('请求出错');
    },
    success: function (data) {
        console.log(data);
        startConfig(data);
    }
});

//开始配置微信js-sdk
var startConfig = function(data){
	/*
   * 注意：
   * 1. 所有的JS接口只能在公众号绑定的域名下调用，公众号开发者需要先登录微信公众平台进入“公众号设置”的“功能设置”里填写“JS接口安全域名”。
   * 2. 如果发现在 Android 不能分享自定义内容，请到官网下载最新的包覆盖安装，Android 自定义分享接口需升级至 6.0.2.58 版本及以上。
   * 3. 常见问题及完整 JS-SDK 文档地址：http://mp.weixin.qq.com/wiki/7/aaa137b55fb2e0456bf8dd9148dd613f.html
   *
   * 开发中遇到问题详见文档“附录5-常见错误及解决办法”解决，如仍未能解决可通过以下渠道反馈：
   * 邮箱地址：weixin-open@qq.com
   * 邮件主题：【微信JS-SDK反馈】具体问题
   * 邮件内容说明：用简明的语言描述问题所在，并交代清楚遇到该问题的场景，可附上截屏图片，微信团队会尽快处理你的反馈。
   */
  wx.config({
    debug: true,
    appId: '填写你的appid',
    timestamp: data.timestamp,
    nonceStr: data.nonceStr,
    signature: data.signature,
    jsApiList: [
      // 所有要调用的 API 都要加到这个列表中
	  'checkJsApi',
        'onMenuShareTimeline',
        'onMenuShareAppMessage',
        'onMenuShareQQ',
        'onMenuShareWeibo',
        'onMenuShareQZone',
        'hideMenuItems',
        'showMenuItems',
        'hideAllNonBaseMenuItem',
        'showAllNonBaseMenuItem',
        'translateVoice',
        'startRecord',
        'stopRecord',
        'onVoiceRecordEnd',
        'playVoice',
        'onVoicePlayEnd',
        'pauseVoice',
        'stopVoice',
        'uploadVoice',
        'downloadVoice',
        'chooseImage',
        'previewImage',
        'uploadImage',
        'downloadImage',
        'getNetworkType',
        'openLocation',
        'getLocation',
        'hideOptionMenu',
        'showOptionMenu',
        'closeWindow',
        'scanQRCode',
        'chooseWXPay',
        'openProductSpecificView',
        'addCard',
        'chooseCard',
        'openCard'
    ]
  });
};

  
  wx.ready(function () {
    // 在这里调用 API
	
  });
</script>
</html>
```