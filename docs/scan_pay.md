# 刷卡支付

	提交刷卡支付请求数据

## URL
   {BASE_URL}/maxfunpay/services/tp/scan_pay

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
	"tp_trade_no":"12601486038696068670",
	"auth_code":"130149729103798799",
	"total_fee":1,
	"nonce_str":"azfkglz",
	"sign":"259140fd9e2bbf84959d0ca01cbda417"
}

sign签名生成方式:
auth_code=&nonce_str=&total_fee&tp_trade_no&mch_key=
通过传递的参数按首字母排序拼接，最后拼上mch_key生成一个字符串，对此字符串进行MD5加密得到
例子：
对此字符串进行MD5加密
auth_code=130149729103798799&nonce_str=azfkglz&total_fee=1&tp_trade_no=12601486038696068670&mch_key=378284f3-31d4-4d75-8c3a-0c540ee67034
得到，259140fd9e2bbf84959d0ca01cbda417，sign不区分大小写

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
            <td>auth_code</th>
            <td>字符型</th>
            <td>用户付款码</th>
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
    "msg": "支付成功",
    "identifier": "o9dNzw96W2W6ni3f3ZdQ2_EGsBPM",
    "total_fee": 1,
    "payment_type": 1,
	"out_trade_no":"1271TP1486985534418791"
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
			<td>为0即支付成功，详细看ret返回码说明</th>
		</tr>
		<tr>
			<td>msg</th>
			<td>字符串</th>
			<td>返回信息，例如错误信息</th>
		</tr>
		<tr>
			<td>identifier</th>
			<td>字符串</th>
			<td>用户标识符, ret等于0才有返回</th>
		</tr>
		<tr>
		<tr>
			<td>total_fee</th>
			<td>整形</th>
			<td>支付金额,单位:分</th>
		</tr>
		<tr>
			<td>payment_type</td>
			<td>数字</td>
			<td>1微信 2支付宝 4京东支付 5QQ支付</td>
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

## ret返回值说明

<table data-tablesaw-sortable>
    <thead>
        <tr>
            <th data-tablesaw-sortable-col data-tablesaw-sortable-default-col>ret返回值</th>
            <th data-tablesaw-sortable-col>描述</th>
        </tr>
		<tr>
			<td>0</th>
			<td>支付成功</th>
		</tr>
		<tr>
			<td>101</th>
			<td>网络延迟，请以顾客支付状态为准！(该状态有可能是支付成功，需要跟用户核实)</th>
		</tr> 
		<tr>
			<td>102</th>
			<td>系统繁忙，稍后再试。</th>
		</tr>
		<tr>
			<td>103</th>
			<td>支付失败，详细看返回的msg内容</th>
		</tr>
		<tr>
			<td>108</th>
			<td>支付超时，该单已撤销，请重新扫描支付</th>
		</tr> 
		<tr>
			<td>109</th>
			<td>支付金额必须小于等于5000000</th>
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
			<td>206</th>
			<td>该订单已完成</th>
		</tr>
    </thead>
<table>
