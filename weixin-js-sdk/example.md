#΢��js-sdk�����������ٴ

> ǰ��<a href="http://weixin.cniotroot.cn">΢��js-sdk�����߷���ƽ̨<a/>ע�����ӹ��ں���Ϣ�������ú�������ip����������ӵ���Ĺ��ںź�̨�İ�ȫ������

## ������΢��js-sdk���ýӿ�,���磺
```js
http://weixin.cniotroot.cn/api/jssdk/********NzQ2LjA
```

## �������H5���棬��ʹ�ýӿڿ��ٻ�ȡjs-sdk��������,eg:
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
	//window.location.href�Ƕ�̬��ȡ��ǰҳ���url������д������Ϊ�����ʱ��΢�Ż����ƴ�Ӷ���
    url:'http://weixin.cniotroot.cn/api/jssdk/********NzQ2LjA'+'?url='+window.location.href,
    error:function(){
        console.log('����');
        alert('�������');
    },
    success: function (data) {
        console.log(data);
        startConfig(data);
    }
});

//��ʼ����΢��js-sdk
var startConfig = function(data){
	/*
   * ע�⣺
   * 1. ���е�JS�ӿ�ֻ���ڹ��ںŰ󶨵������µ��ã����ںſ�������Ҫ�ȵ�¼΢�Ź���ƽ̨���롰���ں����á��ġ��������á�����д��JS�ӿڰ�ȫ��������
   * 2. ��������� Android ���ܷ����Զ������ݣ��뵽�����������µİ����ǰ�װ��Android �Զ������ӿ��������� 6.0.2.58 �汾�����ϡ�
   * 3. �������⼰���� JS-SDK �ĵ���ַ��http://mp.weixin.qq.com/wiki/7/aaa137b55fb2e0456bf8dd9148dd613f.html
   *
   * ������������������ĵ�����¼5-�������󼰽���취�����������δ�ܽ����ͨ����������������
   * �����ַ��weixin-open@qq.com
   * �ʼ����⣺��΢��JS-SDK��������������
   * �ʼ�����˵�����ü��������������������ڣ��������������������ĳ������ɸ��Ͻ���ͼƬ��΢���Ŷӻᾡ�촦����ķ�����
   */
  wx.config({
    debug: true,
    appId: '��д���appid',
    timestamp: data.timestamp,
    nonceStr: data.nonceStr,
    signature: data.signature,
    jsApiList: [
      // ����Ҫ���õ� API ��Ҫ�ӵ�����б���
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
    // ��������� API
	
  });
</script>
</html>
```