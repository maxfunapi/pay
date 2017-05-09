## 一满乐支付API文档

---
  * 测试环境： http://qa.maxfun.co
  * 正式环境： https://tp.maxfun.co
  
---   
  
---

### 接入流程说明：
  下面流程描述了在网页中接入微信支付的场景（如微信点餐，微信商城等场景）。 请参考下面的步骤进行进行对接： 
  1. 在一满乐创建商户,每个商户会对应一个mch_key;
  2. 从接入方的付款界面点击“微信支付”，跳转到我们指定的URL，在该界面会直接激活微信输密码的控件，用户输入密码，交易完成。支付界面URL详情请参考[发起JSSDK支付];
  3. 支付成功后，我们会回调接入方指定的回调url来更新支付状态（回调URL在创建商户时指定);
  
---

### 数据接入接口说明

  * [发起JSSDK支付](https://github.com/maxfunapi/pay/blob/master/docs/js_pay.md)
  * [JSSDK支付结果异步通知](https://github.com/maxfunapi/pay/blob/master/docs/async_notify.md)
  * [交易查询](https://github.com/maxfunapi/pay/blob/master/docs/trade_query.md)
  * [刷卡支付](https://github.com/maxfunapi/pay/blob/master/docs/scan_pay.md)
  * [退款接口](https://github.com/maxfunapi/pay/blob/master/docs/trade_refund.md)
---


