# 退款接口

	提交退款请求数据, 仅支持当天的发生的交易退款

## URL
   {BASE_URL}/maxfunpay/services/tp/trade_refund

## Method
   POST

## Headers
```
   Content-type=application/json
```

## Request
```
{
	"mch_key":"378284f3-31d4-4d75-8c3a-0c540ee6",
	"nonce_str":"abc",
	"tp_trade_no":"1494313896345122",
	"sign":"c2f2898a4b1f306b4422584f5e535646"
}

sign签名生成方式:
nonce_str=&tp_trade_no&mch_key=
通过传递的参数按首字母排序拼接，最后拼上mch_key生成一个字符串，对此字符串进行MD5加密得到
例子：
对此字符串进行MD5加密
nonce_str=abc&tp_trade_no=1494313896345122&mch_key=378284f3-31d4-4d75-8c3a-0c540ee6
得到，c2f2898a4b1f306b4422584f5e535646，sign不区分大小写

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
    "ret": 0,
    "msg": null
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
			<td>ret</th>
			<td>数字</th>
			<td>为0即退款成功，其他值为失败，详细错误情况msg字段</th>
		</tr>
		<tr>
			<td>msg</th>
			<td>字符串</th>
			<td>返回信息，例如错误信息</th>
		</tr>
    </thead>
<table>

## ret返回值说明

<table data-tablesaw-sortable>
    <thead>
        <tr>
            <th data-tablesaw-sortable-col data-tablesaw-sortable-default-col>ret返回值</th>
            <th data-tablesaw-sortable-col>描述</th>
        </tr>
		<tr>
			<td>0</th>
			<td>退款成功</th>
		</tr>
		<tr>
			<td>201</th>
			<td>参数错误，详细看返回的msg内容</th>
		</tr>
		<tr>
			<td>202</th>
			<td>sign校验失败</th>
		</tr>
		<tr>
			<td>203</th>
			<td>mch_key非法</th>
		</tr>
		<tr>
			<td>204</th>
			<td>商户未配置，请联系商务</th>
		</tr>
		<tr>
			<td>205</th>
			<td>该商户未开通支付，请稍后再试</th>
		</tr>
		<tr>
			<td>207</th>
			<td>订单不存在</th>
		</tr>
		<tr>
			<td>208</th>
			<td>订单未付款</th>
		</tr>
		<tr>
			<td>209</th>
			<td>订单已退款</th>
		</tr>
		<tr>
			<td>210</th>
			<td>退款仅支持当天发生的交易</th>
		</tr>
    </thead>
<table>