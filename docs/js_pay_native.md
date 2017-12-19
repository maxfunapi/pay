# 原生微信/支付宝js支付

	原生微信/支付宝js支付

## URL
   {BASE_URL}/maxfunpay/services/tp/jssdk_pay

## Method
   POST

## Headers
```
   Content-type=application/json
```

## Request
```
{
  "mch_key": "c6003437-2a68-43f4-88df-d6e33579f85d",
  "tp_trade_no": "TP151367904179222",
  "total_fee": 1,
  "nonce_str": "ramdom_str",
  "payment_type": 1,
  "openid": "o9dNzw96W2W6ni3f3ZdQ2_EGsBPM"
}

```
<table data-tablesaw-sortable>
    <thead>
        <tr>
            <th data-tablesaw-sortable-col data-tablesaw-sortable-default-col>字段名称</th>
            <th data-tablesaw-sortable-col>类型</th>
            <th data-tablesaw-sortable-col>描述</th>
            <th data-tablesaw-sortable-col>是否必填</th>
        </tr>
		<tr>
            <td>mch_key</th>
            <td>字符型</th>
            <td>商户标识符</th>
            <td>是</th>
        </tr>
		<tr>
            <td>tp_trade_no</th>
            <td>字符型</th>
            <td>商户订单号，32个字符内、可包含字母，确保在商户系统唯一</th>
            <td>是</th>
        </tr>
		<tr>
            <td>total_fee</th>
            <td>整型</th>
            <td>支付金额,单位:分</th>
            <td>是</th>
        </tr>
		<tr>
            <td>nonce_str</th>
            <td>字符型</th>
            <td>随机字符串(建议每次请求都是随机生成的)</th>
            <td>是</th>
        </tr>
        <tr>
            <td>openid</th>
            <td>字符型</th>
            <td>微信openid或支付宝buyerid</th>
            <td>是</th>
        </tr>
		<tr>
            <td>payment_type</th>
            <td>整型</th>
            <td>支付类型 1微信 2支付宝</th>
            <td>是</th>
        </tr>
    </thead>
<table>


## Response
```
{
    "status": {
        "code": "200",
        "message": "success"
    },
    "result": {
        "payment_amount": 0.01,
        "order_info": {
            "appId": "wx8632a91376b81e24",
            "timeStamp": "1513679691874",
            "nonceStr": "1513679691874",
            "signType": "MD5",
            "paySign": "4E1337FB0C297A36E2071E9F94C8276F",
            "package": "prepay_id=wx201712191834514bbc1e8d4e0582825063",
            "callback_url": null
        },
        "alipay_order_info": null,
        "pay_status_info": null,
        "transaction_order_id": 4553,
        "deposit_amount": 0,
        "deposit_balance": 0,
        "coupon_amount": 0,
        "original_amount": 0,
        "transaction_order_no": null,
        "create_date": null
    }
}
```
<table data-tablesaw-sortable>
    <thead>
        <tr>
            <th data-tablesaw-sortable-col data-tablesaw-sortable-default-col>字段名称</th>
            <th data-tablesaw-sortable-col>类型</th>
            <th data-tablesaw-sortable-col>描述</th>
        </tr>
		<tr>
			<td>payment_amount</th>
			<td>数字</th>
			<td>支付金额</th>
		</tr>
		<tr>
			<td>order_info</th>
			<td></th>
			<td>微信原生支付参数</th>
		</tr>
		<tr>
			<td>alipay_order_info</th>
			<td></th>
			<td>支付宝原生支付参数</th>
		</tr>
    </thead>
<table>
