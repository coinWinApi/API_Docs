# B端商户下单API文档
目前开放了B端商户下单api，，我们将提供B端商户accessKey，需要使用我们提供的accessKey，具体接口与回调流程请阅读以下文本。
# 接口说明
- 签名说明：这里的签名采用sha256对请求接口的url与参数带上key与时间戳(毫秒级-长度是13位的)进行加密得到密文，然后在请求中将密文赋给sign参数加进请求头里。 例如：get请求api/Pay 参数有symbol、openid、remark，则需要对 api/Pay?accessKey=****&symbolId=1001&orderBuyType=2&value=100&payId=1&timestamp=1567412503000 进行sha256加密（注意参数的排序是按照键进行升序排序的）然后在请求头里带上sign参数，值就是得到的密文
- 只要请求正常，接口统一返回200状态码，返回的Json格式为
~~~~
{
  "success": true,
  "data": "string"
}
~~~~

### 接口列表

|接口方法|类型|说明|
| --------   | -----  | ----  |
|tripleotc/ad/OrderVerify|post|B端商户下单|
|tripleotc/ad/OrderVerify|B端商户下单|||

### 请求参数
|参数名称|是否必须|类型|描述|默认值|取值范围|
| --------   | -----  | ----  |
|symbolId|true|int|币种Id|无|1011(usdt)|
|orderBuyType|true|int|按数量|无|1--代表按金额|
|value|true|decimal|数值|无||
|payId|true|int|支付方式|无|1-支付宝，2-微信，3-银联|

### 返回参数
|参数名称|是否必须|类型|描述|默认值|取值范围|
| --------   | -----  | ----  |
|success|true|bool|请求是否成功|true|true、false|
|data|true|json|	若成功则返回地址，否则返回错误信息||||
