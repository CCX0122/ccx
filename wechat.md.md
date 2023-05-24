


<br/>

# <center>唯众系统api文档
<br/>
<br/>
<br/>


**<center>  （版本 v1.0）**
<br/>
<br/>
<br/>
<br/>


**<center>  2023年5月**
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>


## <center> 目录<center/>
<br>
 说明：该文档为第三方应用接入唯众系统的接口说明文档初稿，后续可能会根据实际开发情况进行调整


 ## 1. 三方接入流程
 
1. 应用服务商向唯众申请接入请求
2. 唯众系统 配置信息（包含不限于APPKEY、APPSECRET）、api文档、开发测试环境信息等
3. 应用服务商根据文档进行开发和调试
4. 应用服务器开发测试完成申请对接正式环境 
## 2.唯众系统服务端API
### 2.1获取授权
**    通过此接口获取授权的 access_token，调用服务端 API 获取应用资源时需要通过 access_token 来鉴权调用者身份进行授权，7200秒内有效，过期后重新获取 **

调用地址：jswz/apiservice/getaccesstoken?appkey=appkey&appsecert=appsecert
请求方式：GET
返回类型：JSON
### 请求参数

|名称|类型|必填|示例值|描述|
|---|---|---|---|---|
|appkey|String|是| HSDFSDAF233432 |唯众系统分配的appKey|
|appsecret|String|是| 39RSDLFJAFDFSDF |唯众系统分配的appSecret|

### 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|code|Integer|0|返回码|
|msg|String|success|成功|
|data|JSON|-|accessToken信息,见下方JSON1|

#### JSOIN1字段信息
|名称|类型|示例值|描述|
|---|---|---|---|
|accessToken|String|fghjkrtyuifgbn5678|生成的授权码|
|expires|Integer|7200|accessToken过期时间，单位秒，7200秒以内有效，过期重新获取|


> 返回示例

```json
{
  "code": 0,
  "msg": "success",
  "data": 
    {
      "accessToken": "fghjkrtyuifgbn5678",
      "expires": 7200
    }
}
```



### 2.2 获取订单数据

**    经销商在唯众平台的订货数据默认查询全部代理商的数据，可根据上传参数进行条件筛选查询 **

调用地址：jswz/apiservice/getorders
请求方式：POST			 
Content-Type：application/json
返回类型：JSON
### Header参数

|名称|类型|必填|示例值|描述|
|---|---|---|---|---|
|accessToken|String|是| fghjkrtyuifgbn5678 |授权信息|

### Body参数

|名称|类型|必填|示例值|描述|
|---|---|---|---|---|
|rows|Integer|是| 100|数据条数默认100 最大200|
|customerId|Integer|否| 1|代理商编码，查询某个代理商的数据|
|startDate|String|否| 2023-01-01|开始时间|
|startDate|String|否| 2023-01-01|结束时间|

### 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|code|Integer|0|返回码|
|msg|String|success|成功|
|data|JsonData|-|数据详见下方JsonData|

###JsonData
|名称|类型|示例值|描述|
|---|---|---|---|
|hasNewData|boolean|YES|订单日期|
|orderDate|Date|2023-05-01 10:00:00|订单日期|
|detailList|OrderDetail|-|细单数据详见下方OrderDetail|
#### OrderData
|名称|类型|示例值|描述|
|---|---|---|---|
|orderDate|Date|2023-05-01 10:00:00|订单日期|
|orderNo|String|SA203457256|唯众系统订单号|
|orderType|Integer|1|订单类型|
|customerId|Integer|2222|代理商编码|
|receivePerson|String|张三|收货人|
|address|String|北京市朝阳区XXX|收货地址|
|phone|String|13112341234|电话|
|detailList|OrderDetail|-|细单数据详见下方OrderDetail|
#### OrderDetail
|名称|类型|示例值|描述|
|---|---|---|---|
|productModel|String|1-14-1W|产品规格型号|
|quantity|Integer|14|数量|
|taxPrice|Integer|1|订单类型|

> 返回示例
```json
{  
	"code":0,  
	"msg":"success",  
	"data":[  
		{  
			"orderDate":"2023-05-14 10:00:00",  
			"orderNo":"SA2023405685",  
			"orderType":1,  
			"customerId":1,  
			"receivePerson":"张三",  
			"address":"北京市朝阳区XXX",  
			"phone":"13112341234",  
			"detailList":[  
				{  
					"productModel":"1-14-1W",  
					"quantity":12,  
					"taxPrice":7777.89  
				},  
				{  
					"productModel":"1-14-1B",  
					"quantity":10,  
					"taxPrice":4763.22  
				}  
						]  
		},  
		{  
			"orderDate":"2023-03-12 13:22:01",  
			"orderNo":"SA202333385",  
			"orderType":2,  
			"customerId":5,  
			"receivePerson":"李四",  
			"address":"北京市海淀XXX",  
			"phone":"13156788765",  
			"detailList":[  
				{  
					"productModel":"1-14-1W",  
					"quantity":2,  
					"taxPrice":4834.89  
				},  
				{  
					"productModel":"1-14-1B",  
					"quantity":5,  
					"taxPrice":1234.66  
				}  
						]  
		}  
			]  
}
```

### 2.2 获取出库数据

**    唯众平台出库至经销商的数据，可根据上传参数进行条件筛选查询 **

调用地址：jswz/apiservice/getorders
请求方式：POST			 
Content-Type：application/json
返回类型：JSON
### Header参数

|名称|类型|必填|示例值|描述|
|---|---|---|---|---|
|accessToken|String|是| fghjkrtyuifgbn5678 |授权信息|

### Body参数

|名称|类型|必填|示例值|描述|
|---|---|---|---|---|
|page|Integer|是| 1|页码|
|rows|Integer|是| 20|每页条数，默认20，最大100|
|customerId|Integer|否| 1|代理商编码，查询某个代理商的数据|
|startDate|String|否| 2023-01-01|开始时间|
|startDate|String|否| 2023-01-01|结束时间|


### 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|code|Integer|0|返回码|
|msg|String|success|成功|
|data|ShipmentData|-|总单数据与细单数据详见下方ShipmentData|
#### OrderData
|名称|类型|示例值|描述|
|---|---|---|---|
|orderDate|Date|2023-05-01 10:00:00|订单日期|
|orderNo|String|SA203457256|唯众系统订单号|
|orderType|Integer|1|订单类型|
|customerId|Integer|2222|代理商编码|
|receivePerson|String|张三|收货人|
|address|String|北京市朝阳区XXX|收货地址|
|phone|String|13112341234|电话|
|detailList|OrderDetail|-|细单数据详见下方OrderDetail|
#### OrderDetail
|名称|类型|示例值|描述|
|---|---|---|---|
|productModel|String|1-14-1W|产品规格型号|
|quantity|Integer|14|数量|
|taxPrice|Integer|1|订单类型|

> 返回示例
```json
{  
	"code":0,  
	"msg":"success",  
	"data":[  
		{  
			"orderDate":"2023-05-14 10:00:00",  
			"orderNo":"SA2023405685",  
			"orderType":1,  
			"customerId":1,  
			"receivePerson":"张三",  
			"address":"北京市朝阳区XXX",  
			"phone":"13112341234",  
			"detailList":[  
				{  
					"productModel":"1-14-1W",  
					"quantity":12,  
					"taxPrice":7777.89  
				},  
				{  
					"productModel":"1-14-1B",  
					"quantity":10,  
					"taxPrice":4763.22  
				}  
						]  
		},  
		{  
			"orderDate":"2023-03-12 13:22:01",  
			"orderNo":"SA202333385",  
			"orderType":2,  
			"customerId":5,  
			"receivePerson":"李四",  
			"address":"北京市海淀XXX",  
			"phone":"13156788765",  
			"detailList":[  
				{  
					"productModel":"1-14-1W",  
					"quantity":2,  
					"taxPrice":4834.89  
				},  
				{  
					"productModel":"1-14-1B",  
					"quantity":5,  
					"taxPrice":1234.66  
				}  
						]  
		}  
			]  
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1MzE1NDMxOTcsOTk2Nzk1ODkzLDE2NT
U2NTg5MzMsMTUxNzIwODMyMywtMTA5MDU5MDY3LC0xNTQzMTk5
NjIwLC0xOTc4MTYwNjk5LC0xNzA2NTI3OTgzLDE3NjMzMDA4NT
IsMTU4MDE4MDk5Miw4MzMwNzQ1NzgsLTM1MjcyNjU0MiwxNzYw
ODM2MDk1LDE4OTEwNjg1NzIsLTEwNzY4NzIzMDksMTc5ODU2Mz
IyNSwtNjQ0NjY1NjAsMTI4MDkwNjUzNl19
-->