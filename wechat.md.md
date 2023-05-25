


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


## <center> 目录
[TOC]

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

调用地址：jswz/apiservice/getAccessToken?appkey=appkey&appsecert=appsecert
请求方式：GET
返回类型：JSON
### Query参数

|名称|类型|必填|示例值|描述|
|---|---|---|---|---|
|appkey|String|是| HSDFSDAF233432 |唯众系统分配的appKey|
|appsecret|String|是| 39RSDLFJAFDFSDF |唯众系统分配的appSecret|

### 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|code|Integer|0|返回码|
|msg|String|success|成功|
|data|AccessToken|-|accessToken信息,见下方JSON1|

#### AccessToken字段信息
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

调用地址：jswz/apiservice/getOrders
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

### JsonData
|名称|类型|示例值|描述|
|---|---|---|---|
|hasNewData|boolean|true|当前查询条件下查询到的数据是未全部传输，如果是yes则表示数据量太多数据未全部传输，此时再次以当前查询条件进行查询会返上次未返回的数据，以此类推重复调用此接口获取新数据。如果值为false则此查询条件下的数据已经全部返回|
|orderData|OrderData|-|细单数据详见下方OrderDetail|
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
    "data":{
        "hasNewData":true,
        "orderData":[
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
}
```

### 2.3 获取出库数据

**    唯众平台出库至经销商的数据，可根据上传参数进行条件查询 **

调用地址：jswz/apiservice/getShipments
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
|rows|Integer|是| 200|默认200|
|customerId|Integer|否| 1|代理商编码，查询某个代理商的数据|
|startDate|String|否| 2023-01-01|开始时间|
|startDate|String|否| 2023-01-01|结束时间|


### 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|code|Integer|0|返回码|
|msg|String|success|成功|
|data|JsonData|-|数据详见下方JsonData|

### JsonData
|名称|类型|示例值|描述|
|---|---|---|---|
|hasNewData|boolean|true|当前查询条件下查询到的数据是未全部传输，如果是yes则表示数据量太多数据未全部传输，此时再次以当前查询条件进行查询会返上次未返回的数据，以此类推重复调用此接口获取新数据。如果值为false则此查询条件下的数据已经全部返回|
|shipmentData|ShipmentData|-|细单数据详见下方ShipmentData|
#### ShipmentData
|名称|类型|示例值|描述|
|---|---|---|---|
|shipmentDate|Date|2023-05-01 10:00:00|发货日期|
|shipmentNo|String|SA203457256|发货单号|
|orderNo|String|SA203457256|关联订单号|
|shipmentType|Integer|1|发货类型编码|
|customerId|Integer|2222|代理商编码|
|receivePerson|String|张三|收货人|
|address|String|北京市朝阳区XXX|收货地址|
|phone|String|13112341234|电话|
|detailList|ShipmentDetail|-|细单数据详见下方ShipmentDetail|
#### ShipmentDetail
|名称|类型|示例值|描述|
|---|---|---|---|
|productModel|String|1-14-1W|产品规格型号|
|validDate|Date|2030-01-01|有效期|
|lot|String|DEF3425|批号|
|sn|String|34567|序列号|
|quantity|Integer|14|数量|
|taxPrice|Bigdecimal|345.87|发票单价|

> 返回示例
```json
{
    "code":0,
    "msg":"success",
    "data":{
        "hasNewData":true,
        "shipmentData":[
            {
                "shipmentDate":"2023-05-14 10:00:00",
                "shipmentNo":"34232",
                "orderNo":"SA2023405685",
                "shipmentType":1,
                "customerId":1,
                "receivePerson":"张三",
                "address":"北京市朝阳区XXX",
                "phone":"13112341234",
                "detailList":[
                    {
                        "productModel":"1-14-1W",
                        "validDate":"2029-09-09",
                        "lot":"1-14-1W",
                        "sn":"FE2452D",
                        "quantity":10,
                        "taxPrice":7777.89
                    },
                    {
                        "productModel":"1-14-1B",
                        "validDate":"2029-09-09",
                        "lot":"SSS",
                        "sn":"FE2452D",
                        "quantity":10,
                        "taxPrice":4763.22
                    }
                ]
            },
            {
                "shipmentDate":"2023-05-20 10:00:00",
                "shipmentNo":"366662",
                "orderNo":"SA202366665",
                "shipmentType":1,
                "customerId":1,
                "receivePerson":"李四",
                "address":"北京市朝阳区XXX",
                "phone":"13134566543",
                "detailList":[
                    {
                        "productModel":"1-14-1W",
                        "validDate":"2029-09-09",
                        "lot":"1-14-1W",
                        "sn":"FE2452D",
                        "quantity":10,
                        "taxPrice":7777.89
                    },
                    {
                        "productModel":"1-14-1B",
                        "validDate":"2029-09-09",
                        "lot":"SSS",
                        "sn":"FE2452D",
                        "quantity":10,
                        "taxPrice":4763.22
                    }
                ]
            }
        ]
    }
}
```
### 2.4 获取植入数据

**    经销商在唯众系统上报的植入数据，可根据上传参数进行条件查询 **

调用地址：jswz/apiservice/getimplants
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
|rows|Integer|是| 200|默认200|
|customerId|Integer|否| 1|代理商编码，查询某个代理商的数据|
|startDate|String|否| 2023-01-01|开始时间|
|startDate|String|否| 2023-01-01|结束时间|


### 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|code|Integer|0|返回码|
|msg|String|success|成功|
|data|JsonData|-|数据详见下方JsonData|

### JsonData
|名称|类型|示例值|描述|
|---|---|---|---|
|hasNewData|boolean|true|当前查询条件下查询到的数据是未全部传输，如果是yes则表示数据量太多数据未全部传输，此时再次以当前查询条件进行查询会返上次未返回的数据，以此类推重复调用此接口获取新数据。如果值为false则此查询条件下的数据已经全部返回|
|implantData|ImplantData|-|细单数据详见下方ImplantData|
#### ImplantData
|名称|类型|示例值|描述|
|---|---|---|---|
|customerId|Integer|234|经销商代码|
|hospitalId|Integer|3456|医院编码|
|invoiceUnit|String|嘉事唯众|开票单位名称|
|receiveName|String|张三|发票购货方名称|
|invoiceNo|String|2222|发票号码|
|invoiceDate|Date|2020-10-01|发票日期|
|invoiceType|String|医院发票|发票类型*|
|invoiceCode|String|45678|发票代码|
|invoiceCheckCode|String|123456|发票校验码后六位|
|invoiceAmount|Bigdecimal|4567.67|发票金额|
|reportDate|Date|2022-10-11|上报日期|
|detailList|ImplantDetail|-|细单数据详见下方ImplantDetail|
#### ImplantDetail
|名称|类型|示例值|描述|
|---|---|---|---|
|productModel|String|1-14-1W|产品规格型号|
|validDate|Date|2030-01-01|有效期|
|lot|String|DEF3425|批号|
|sn|String|34567|序列号|
|quantity|Integer|14|数量|
|taxPrice|Bigdecimal|345.74|发票单价|
|hospitalPrice|Bigdecimal|345.74|医院单价|

> 返回示例
```json
{
    "code":0,
    "msg":"success",
    "data":{
        "hasNewData":true,
        "implantData":[
            {
                "customerId":2324,
                "hospitalId":4563,
                "invoiceUnit":"开票单位名称A",
                "receiveName":"发票购货方名称B",
                "invoiceNo":"666453",
                "invoiceDate":"2023-05-01",
                "invoiceType":"医院发票",
                "invoiceCode":"45678",
                "invoiceCheckCode":"123456",
                "invoiceAmount":"6574.57",
                "reportDate":"2022-10-23",
                "detailList":[
                    {
                        "productModel":"1-14-1W",
                        "validDate":"2029-09-09",
                        "lot":"1-14-1W",
                        "sn":"FE2452D",
                        "quantity":10,
                        "taxPrice":7777.89,
                        "hospitalPrice":7777.89
                    },
                    {
                        "productModel":"1-14-1B",
                        "validDate":"2029-09-09",
                        "lot":"SSS",
                        "sn":"FE2452D",
                        "quantity":10,
                        "taxPrice":4763.22,
                        "hospitalPrice":4377.89
                    }
                ]
            },
            {
                "customerId":432,
                "hospitalId":564,
                "invoiceUnit":"开票单位名称C",
                "receiveName":"发票购货方名称D",
                "invoiceNo":"3421",
                "invoiceDate":"2023-04-01",
                "invoiceType":"医院发票",
                "invoiceCode":"2312",
                "invoiceCheckCode":"543423",
                "invoiceAmount":"6574.57",
                "reportDate":"2022-10-23",
                "detailList":[
                    {
                        "productModel":"1-14-1W",
                        "validDate":"2029-09-09",
                        "lot":"1-14-1W",
                        "sn":"FE2452D",
                        "quantity":10,
                        "taxPrice":7777.89,
                        "hospitalPrice":7777.89
                    },
                    {
                        "productModel":"1-14-1B",
                        "validDate":"2029-09-09",
                        "lot":"SSS",
                        "sn":"FE2452D",
                        "quantity":10,
                        "taxPrice":4763.22,
                        "hospitalPrice":4377.89
                    }
                ]
            }
        ]
    }
}
```
### 2.5 获取退货数据

**    以任何原因由代理商退货到唯众的产品，可根据上传参数进行条件查询 **

调用地址：jswz/apiservice/getReturnData
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
|rows|Integer|是| 200|默认200|
|customerId|Integer|否| 1|代理商编码，查询某个代理商的数据|
|startDate|String|否| 2023-01-01|开始时间|
|startDate|String|否| 2023-01-01|结束时间|


### 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|code|Integer|0|返回码|
|msg|String|success|成功|
|data|JsonData|-|数据详见下方JsonData|

### JsonData
|名称|类型|示例值|描述|
|---|---|---|---|
|hasNewData|boolean|true|当前查询条件下查询到的数据是未全部传输，如果是yes则表示数据量太多数据未全部传输，此时再次以当前查询条件进行查询会返上次未返回的数据，以此类推重复调用此接口获取新数据。如果值为false则此查询条件下的数据已经全部返回|
|returnData|ReturnData|-|细单数据详见下方ReturnData|
#### ReturnData
|名称|类型|示例值|描述|
|---|---|---|---|
|returnDate|Date|2020-10-10|退货日期|
|customerId|Integer|3456|代理商编码|
|returnTypeId|Integer|123|退货类型编码|
|detailList|ReturnDetail|-|细单数据详见下方ReturnDetail|
#### ReturnDetail
|名称|类型|示例值|描述|
|---|---|---|---|
|productModel|String|1-14-1W|产品型号|
|validDate|Date|2030-01-01|有效期|
|lot|String|DEF3425|批号|
|sn|String|34567|序列号|
|quantity|Integer|14|数量|


> 返回示例
```json
{
    "code":0,
    "msg":"success",
    "data":{
        "hasNewData":true,
        "returnData":[
            {
                "returnDate":"2023-05-01",
                "customerId":2324,
                "returnTypeId":4563,
                "detailList":[
                    {
                        "productModel":"1-14-1W",
                        "validDate":"2029-09-09",
                        "lot":"1-14-1W",
                        "sn":"FE2452D",
                        "quantity":10
                    },
                    {
                        "productModel":"1-14-1B",
                        "validDate":"2029-09-09",
                        "lot":"SSS",
                        "sn":"FE2452D",
                        "quantity":10
                    }
                ]
            },
            {
                "returnDate":"2023-05-01",
                "customerId":2324,
                "returnTypeId":4563,
                "detailList":[
                    {
                        "productModel":"1-14-1W",
                        "validDate":"2029-09-09",
                        "lot":"1-14-1W",
                        "sn":"FE2452D",
                        "quantity":10
                    },
                    {
                        "productModel":"1-14-1B",
                        "validDate":"2029-09-09",
                        "lot":"SSS",
                        "sn":"FE2452D",
                        "quantity":10
                    }
                ]
            }
        ]
    }
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY5MjY0NTM1LDg5ODYxNDE4MywxMzE3Nj
I4NTc3LC05MDkyOTc3MTMsLTE1NTU0Mzk2NDYsLTEwNjUwNTk5
NSwxNTQ2NTA1Njc4LDE4MzM5MTM5ODgsLTc1NzQ5MTAzNiwtMT
gwNDYzNjc0MiwxNDI4MDYzNTM0LDM1NzQyMTUyOSwtMTc1ODU4
NzQzOSw4MDE3NzM3MjUsLTIxNDEzMDM3NTksOTk2Nzk1ODkzLD
E2NTU2NTg5MzMsMTUxNzIwODMyMywtMTA5MDU5MDY3LC0xNTQz
MTk5NjIwXX0=
-->