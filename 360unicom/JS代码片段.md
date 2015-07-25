### 以下是常用的代码收集，没有任何技术含量，只是填坑的积累。转载请注明出处，谢谢。

#### 1. js
- 返回指定范围的随机数(m-n之间)的公式
```javascript
Math.random()*(n-m)+m
```

#### 2. [微信 weixin](http://loo2k.com/blog/detecting-wechat-client/)

- UserAgent 判断微信客户端
```javascript
// Mozilla/5.0 (iPhone; CPU iPhone OS 8_3 like Mac OS X) AppleWebKit/600.1.4 (KHTML, like Gecko) Mobile/12F70 MicroMessenger/6.1.5 NetType/WIFI
function isWechat() {  
    var ua = navigator.userAgent.toLowerCase();
    return /micromessenger/i.test(ua) || /windows phone/i.test(ua);
}
```

- JS接口安全域名不填写，分享onMenuShareAppMessage直接会取默认值。
```javascript
// 分享onMenuShareAppMessage直接会取默认值
```

- 关闭当前页面
```javascript
WeixinJSBridge.call('closeWindow');
```

- [支付接口方法调用必须在addevent里边调用](http://www.cnblogs.com/true_to_me/p/3565039.html)
```javascript
document.addEventListener('WeixinJSBridgeReady', function onBridgeReady(){
    that.initOrder();
}, false);
```

- 支付接口方法调用必须在
```javascript
WeixinJSBridge.invoke('getBrandWCPayRequest', d, function(res){
    if(res.err_msg == "get_brand_wcpay_request:ok"){
        // alert("支付成功");
        // union.release(d.orderId);
        resetUrl();
        paySuccess('home', d.orderId);
    } else {
        cancelOrder(d.orderId);
        // alert(res.err_msg);
    }
    loading.hide();
});
```