# B端商户下单API文档

* [返回文档首页](https://github.com/coinWinApi/API_Docs)

目前开放了B端商户下单api，，我们将提供B端商户accessKey与secretKey,accessKey用来授权，secretKey用来签名，切勿暴露accessKey与secretKey，具体接口与回调流程请阅读以下文本。
# 接口说明
- 签名说明：这里的签名采用sha256进行签名。对业务报文体的JSON对象的字符串签名。
- 签名key：secretKey 【secretKey由接口方提供】
- 签名对象：
### 业务报文体的JSON对象的 字符串 


#### 接口列表 (注：Data为业务报文体，json对象，该对象的key切记务必要小写，不然无法验签通过)

|接口地址|请求方式|接口说明|
| --------   | -----  | ----  |
|tripleotc/ad/OrderVerify|post|B端商户下单接口|

### 请求参数
|参数名称|是否必须|类型|描述|默认值|取值范围|
| --------   | -----  | ----  | ----  | ----  | ----  |
|AccessKey|true|string|授权key|无|接口方提供|
|TimeStamp|true|string|（当前时间）毫秒级精度|无|时间戳，例：1567412503000|
|Signature|true|string|签名数据|无||
|Data|true|json|业务报文体|无||
| --------   | -----  | ----  | ----  | ----  | ----  |
|Data业务报文体参数名称|是否必须|类型|描述|默认值|取值范围|
|Data.accesskey|true|string|授权key|无|接口方提供|
|Data.timestamp|true|string|（当前时间）毫秒级精度|无|时间戳|
|Data.symbolid|true|int|币种Id|1011|1011(usdt)|
|Data.orderbuytype|true|int|按金额|1|1--代表按金额|
|Data.value|true|decimal|金额|无||
|Data.payid|true|int|支付方式|无|1-支付宝，2-微信，3-银联|
|Data.ordersourcetype|true|int|订单来源类型|30001|平台订单|
| --------   | -----  | ----  | ----  | ----  | ----  |
### 返回参数

|参数名称|是否必须|类型|描述|默认值|取值范围|
| --------   | -----  | ----  | ----  | ----  | ----  |
|code|true|int|业务码||200：成功、1001：失败|
|success|true|bool|操作是否成功|true：成功 false：失败|true、false|
|message|true|string|文本信息|||
|data|true|json|结果业务体||||
