# 交易查询

	交易查询

## URL
   {BASE_URL}/maxfunpay/services/tp/trade_query

## Method
   POST

## Headers
```
   Content-type=application/json
```

## Request
```
{
	"mch_key":"378284f3-31d4-4d75-8c3a-0c540ee67034",
	"tp_trade_no":"1484657785743165",
	"nonce_str":"azfkglz",
	"sign":"06acad6e57d3091b61df59df76b39f5d"
}

sign签名生成方式:
nonce_str=&tp_trade_no&mch_key=
通过传递的参数按首字母排序拼接，最后拼上mch_key生成一个字符串，对此字符串进行MD5加密得到
例子：
对此字符串进行MD5加密
nonce_str=azfkglz&tp_trade_no=1484657785743165&mch_key=378284f3-31d4-4d75-8c3a-0c540ee67034
得到，06acad6e57d3091b61df59df76b39f5d，sign不区分大小写

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
            <td>商户订单号</th>
            <td>是</th>
        </tr>
		<tr>
            <td>nonce_str</th>
            <td>字符型</th>
            <td>随机字符串(建议每次请求都是随机生成的)</th>
            <td>是</th>
        </tr>
        <tr>
            <td>sign</th>
            <td>字符型</th>
            <td>数据签名</th>
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
    "identifier": null,
    "mch_key": "378284f3-31d4-4d75-8c3a-0c540ee67034",
    "tp_trade_no": "1484657785743165",
    "pay_status": 0,
    "payment_type": 1,
    "total_fee": 0.01,
    "out_trade_no": "1271TP1487057748363124"
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
			<td>pay_status</th>
			<td>数字</th>
			<td>付款状态: 0-未付款 1-已支付 3-取消支付订单 4-已退款</th>
		</tr>
		<tr>
			<td>identifier</th>
			<td>字符串</th>
			<td>用户标识符</th>
		</tr>
		<tr>
			<td>mch_key</th>
			<td>字符串</th>
			<td>商户标识符</th>
		</tr>
		<tr>
			<td>total_fee</th>
			<td>数字(Double)</th>
			<td>交易金额</th>
		</tr>
		<tr>
			<td>payment_type</td>
			<td>数字</td>
			<td>支付方式: 1-微信 2-支付宝 4-京东支付 5-QQ支付</td>
		</tr>
		<tr>
			<td>tp_trade_no</td>
			<td>字符串</td>
			<td>商户订单号</td>
		</tr>
		<tr>
			<td>out_trade_no</td>
			<td>字符串</td>
			<td>交易单号</td>
		</tr>
    </thead>
<table>
