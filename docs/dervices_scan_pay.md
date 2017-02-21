# 刷卡支付

	提交刷卡支付请求数据

## URL
   测试环境地址:https://demo.maxfun.co/maxfunpay/services/devices_scan_pay

## Method
   POST

## Headers
```
   Content-type=application/json
```

## Request
```
{
	"devices_key":"3363c762-f7dc-11e6-bf52-00163e003235",
	"auth_code":"123",
	"total_fee":1,
	"nonce_str":"abc",
	"sign":"5d2a83bdc2740b558e600abe0a53c88b"
}

sign签名生成方式:
auth_code=&nonce_str&total_fee&devices_key=
通过传递的参数按首字母排序拼接，最后拼上access_token生成一个字符串，对此字符串进行MD5加密得到
例子：
对此字符串进行MD5加密
auth_code=123&nonce_str=abc&total_fee=1&devices_key=3363c762-f7dc-11e6-bf52-00163e003235
得到，5d2a83bdc2740b558e600abe0a53c88b， sign不区分大小写

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
            <td>devices_key</th>
            <td>字符型</th>
            <td>设备标识符</th>
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
    "status": 0,
    "msg": "支付成功"
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
			<td>status</th>
			<td>数字</th>
			<td>为0即支付成功，详细看ret返回码说明</th>
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
    </thead>
<table>
