


<br/>

# <center>唯众系统api文档
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>


**<center>  （Beta2.0版）**
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>

**<center>  2023年6月16日**
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/><br/>
<br/>
<br/>
<br/>
<br/>



## 目录
[TOC]



<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/><br/>
<br/>






 ## 1. 三方接入流程
 
1. 应用服务商向唯众申请接入请求
2. 唯众系统提供配置信息（包含不限于APPKEY、APPSECRET）、api文档、开发测试环境信息等
3. 应用服务商根据文档进行开发和调试
4. 应用服务器开发测试完成申请对接正式环境 
## 2.唯众系统服务端API
### 2.1获取授权和鉴权信息
#### 2.1.1 获取AES秘钥
说明： 通过此接口获取加密秘钥，服务端返回的数据data为密文，需解密后进行，请求此接口就会更新aes 秘钥，此秘钥会在月底最后一天晚上12点前进行强制更换

调用地址：/apiservice/getAes
请求方式：POST
Content-Type：application/json
返回类型：JSON
 Body参数

|名称|类型|必填|示例值|描述|
|---|---|---|---|---|
|appKey|String|是| HSDFSDAF233432 |唯众系统分配的appKey|
|appSecret|String|是| 39RSDLFJAFDFSDF |唯众系统分配的appSecret|

 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|code|Integer|0|返回码|
|msg|String|success|成功|
|data|AesEntity|-|返回的数据是密文需要使用aes解密,下面的是解密后的数据格式,aes信息,见下方AesEntity|

 AesEntity字段信息
|名称|类型|示例值|描述|
|---|---|---|---|
|aesKey|String|fghjkrtyuifgbn5678|生成的AesKey|

> 返回示例

```json
{
  "code": 0,
  "msg": "success",
  "data": 
    {
      "aesKey": "fghjkrtyuifgbn5678"
    }
}
```
#### 2.1.2 获取RSA秘钥
说明： 通过此接口获取加密秘钥，服务端返回的数据data为密文，需解密后进行，请求此接口就会更新rsa 秘钥，此秘钥会在月底最后一天晚上12点前进行强制更换

调用地址：/apiservice/getRsa
请求方式：POST
Content-Type：application/json
返回类型：JSON
 Body参数

|名称|类型|必填|示例值|描述|
|---|---|---|---|---|
|appKey|String|是| HSDFSDAF233432 |唯众系统分配的appKey|
|appSecret|String|是| 39RSDLFJAFDFSDF |唯众系统分配的appSecret|

 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|code|Integer|0|返回码|
|msg|String|success|成功|
|data|RsaEntity|-|返回的数据是密文需要使用aes解密,下面的是解密后的数据格式,rsa信息,见下方RsaEntity|

 RsaEntity字段信息
|名称|类型|示例值|描述|
|---|---|---|---|
|rsaPrivate|String|MIICdwIBADANBgkqhkiG9w0BAQEFAASCAmEwggJdAgEAAoGBALCIydYi717O+CgMlngBL14QLnDhpoW4hZQANnEEzfk0d+dKeHY6DrmZKBWceca5OL85w3XUUuAMhAspK89rE6XX9n63rvmsgQTSV7oYEHJDO6fOcLeeCZPH9hLaZsLg1yjp4lQ3g5wNsz56Rwl37cKFlL6c0W5stMMRhP/JRYevAgMBAAECgYAV/r0TIqArcmMl7keTJSanNCHtK5hJYe+2vH4L/9q/+YMU/MjchihOhKAjbS8ZDPvei45ocG9w/e43y8XrHn7AflxiRXp02UPq48QxBq1xIG/2LG4HbuyfTZvSy8yv42bz6a88ciQs3iVsGwM4YFk22dmDEemDQwcM8T9ap7FY4QJBAOnVu15TqPWfLblCy8iXlq/K1bnpdFHSgRix3vkMqo3+fAhvtozExjhVeB1fC7mpzBRle16R+YKgZqmIiIZglGECQQDBRJf2h6bQaNmpvBJiZMiEn9giaSNyNhgN3YedtjcboDebO0bLyTpeDKUp7yyUgKca+PbrpmTEYqV6HRsSLJYPAkEAzfu0ERS7OptdCNx5bRtz5ylTenDXQZigliNh2pu4xlqN4lSeR4SzZD6OD7mBN60GlFUNBzKpy9MGfINEWLNNIQJAdlA/lzRD8qG9XiM8Pe/ksQwJjEdA49Ipt5M+SlYaNldGs0j+dhKiIKEtGxbH+8Emi2SOBITAe1jIZJEc2WtiEQJBAL7vjZy3A9v8Y83ReqBBZDlH7bdsALwd+ky7yuOUgbOtMt4lPUnLXl7AM8VhFyFXNvh4/bUh77o3osmQjhTKXv0=|生成的Rsa私钥|

> 返回示例

```json
{
  "code": 0,
  "msg": "success",
  "data": 
    {
      "rsaPrivate": "MIICdwIBADANBgkqhkiG9w0BAQEFAASCAmEwg"
    }
}
```
### 2.2 获取订单数据

*  说明： 获取经销商在唯众平台的增量订货数据，默认查询全部代理商的数据。如要查询某个代理商的数据请根据上传参数进行查询

调用地址：/apiservice/getOrders
请求方式：POST			 
Content-Type：application/json
返回类型：JSON

Body参数

|名称|类型|必填|示例值|描述|
|---|---|---|---|---|
|isNewData|Integer|是| 0|是否为增量数据 0-全量数据  1-增量数据|
|page|Integer|否| 1|页码，1开始 如果isNewData==0 此项必填|
|rows|Integer|否| 500|每页条数，最大值1000 如果isNewData==0 此项必填|
|startDate|String|否| 2023-01-01|开始时间|
|endDate|String|否| 2023-01-01|结束时间|
|sign|String|是| dsfsdjfdfadf|验签字段，按照一点的组合顺序进行MD5加密|

 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|code|Integer|0|返回码|
|msg|String|success|成功|
|data|JsonData|-|数据详见下方JsonData|

 JsonData
|名称|类型|示例值|描述|
|---|---|---|---|
|orderData|OrderData|-|细单数据详见下方OrderDetail|
|total|Long|4500|数据总数|
 OrderData
|名称|类型|示例值|描述|
|---|---|---|---|
|orderDate|Date|2023-05-01 10:00:00|订单日期|
|lastModifyTime|Timestamp|1685513394|数据最后更新时间|
|orderNo|String|SA203457256|唯众系统订单号|
|orderType|Integer|1|订单类型详见订单类型字典|
|orderStatus|Integer|1|订单状态详见订单状态字典|
|customerId|Integer|2222|代理商编码|
|receivePerson|String|张三|收货人|
|address|String|北京市朝阳区XXX|收货地址|
|phone|String|13112341234|电话|
|memo|String|备注信息|备注|
|detailList|OrderDetail|-|细单数据详见下方OrderDetail|
 OrderDetail
|名称|类型|示例值|描述|
|---|---|---|---|
|orderDetailNo|String|SA2023405685001|唯众系统订单细单号|
|productModel|String|1-14-1W|产品规格型号|
|quantity|Integer|14|数量|
|sendQuantity|Integer|10|已发数量|
|notYetSendQuantity|Integer|4|未发数量|
|taxPrice|Bigdecimal|1|含税单价|

> 返回示例
```json
{
    "code":0,
    "msg":"success",
    "data":{
	    "total":4500,
        "orderData":[
            {
                "orderDate":"2023-05-14 10:00:00",
                "lastModifyTime": 1685513394,
                "orderNo":"SA2023405685",
                "orderType":1,
                "orderStatus":1,
                "customerId":1,
                "receivePerson":"张三",
                "address":"北京市朝阳区XXX",
                "memo":"备注信息",
                "phone":"13112341234",
                "detailList":[
                    {
	                    "orderDetailNo":"SA2023405685001",
                        "productModel":"1-14-1W",
                        "quantity":12,
                        "sendQuantity":10,
                        "notYetSendQuantity":2,
                        "taxPrice":7777.89
                    },
                    {
                        "orderDetailNo":"SA2023405685002",
                        "productModel":"1-14-1B",
                        "quantity":10,
                        "sendQuantity":8,
                        "notYetSendQuantity":2,
                        "taxPrice":4763.22
                    }
                ]
            },
            {
                "orderDate":"2023-03-12 13:22:01",
                "lastModifyTime": 1685513394,
                "orderNo":"SA202333385",
                "orderType":2,
                "orderStatus":1,
                "customerId":5,
                "receivePerson":"李四",
                "address":"北京市海淀XXX",
                "memo":"备注信息",
                "phone":"13156788765",
                "detailList":[
                    {
	                    "orderDetailNo":"SA202333385003",
                        "productModel":"1-14-1W",
                        "quantity":2,
                        "sendQuantity":1,
                        "notYetSendQuantity":1,
                        "taxPrice":4834.89
                    },
                    {
                        "orderDetailNo":"SA202333385004",
                        "productModel":"1-14-1B",
                        "quantity":5,
                        "sendQuantity":5,
                        "notYetSendQuantity":0,
                        "taxPrice":1234.66
                    }
                ]
            }
        ]
    }
}
```

### 2.3 获取出库数据

* 说明：唯众平台出库至经销商的数据，可根据上传参数进行条件查询 ，建议正式上线前全量同步一次数据，此后至少每天同步一次增量数据，以免长时间未同步，导致数据过多，导致传输时间变长而失败！

调用地址：/apiservice/getShipments
请求方式：POST			 
Content-Type：application/json
返回类型：JSON

 Body参数

|名称|类型|必填|示例值|描述|
|---|---|---|---|---|
|isNewData|Integer|是| 0|是否为增量数据 0-全量数据  1-增量数据|
|page|Integer|否| 1|页码，如果isNewData=0此项必填。如果isNewData=1 此参数不生效|
|rows|Integer|否| 500|每页条数，最大值1000 如果isNewData=0 此项必填。如果isNewData=1 此参数不生效|
|startDate|String|否| 2023-01-01|开始时间，如果isNewData==1 此参数不生效|
|endDate|String|否| 2023-01-01|结束时间，如果isNewData==1 此参数不生效|


 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|code|Integer|0|返回码|
|msg|String|success|成功|
|data|JsonData|-|返回的数据是密文需要使用aes解密,下面的是解密后的数据格式,数据详见下方JsonData|

 JsonData
|名称|类型|示例值|描述|
|---|---|---|---|
|shipmentData|ShipmentData|-|细单数据详见下方ShipmentData|
|total|Long|4500|数据总数|
 ShipmentData
|名称|类型|示例值|描述|
|---|---|---|---|
|shipmentDate|String|2023-05-01 10:00:00|发货日期|
|shipmentNo|String|1341715|唯众系统发货单号|
|orderNo|String|SA203457256|唯众系统关联订单号|
|shipmentType|Integer|1|发货类型编码,详见发货类型字典|
|orderType|Integer|1|订单类型编码,详见订单类型字典|
|customerId|String|2222|代理商编码|
|receivePerson|String|张三|收货人|
|address|String|北京市朝阳区XXX|收货地址|
|phone|String|13112341234|电话|
|lastModifyTime|Long|1685513394|数据最后更新时间|
|id|Integer|168|数据唯一值|
|detailList|ShipmentDetail|-|细单数据详见下方ShipmentDetail|
 ShipmentDetail
|名称|类型|示例值|描述|
|---|---|---|---|
|shipmentDetailNo|String|34232001|唯众系统发货细单号|
|orderDetailNo|String|SA2023405685001|唯众系统订单细单号|
|productModel|String|1-14-1W|产品规格型号|
|validDate|String|2030-01-01|有效期|
|lot|String|DEF3425|批号|
|sn|String|34567|序列号|
|quantity|Integer|14|数量|
|taxPrice|Bigdecimal|345.87|含税单价|

> 返回示例
```json
{
    "code":0,
    "msg":"success",
    "data":{
        "total":5000,
        "shipmentData":[
            {
                "shipmentDate":"2023-05-14 10:00:00",
                "shipmentNo":"34232",
                "orderNo":"SA2023405685",
                "shipmentType":1,
                "orderType":1,
                "customerId":"WS-FSD23",
                "receivePerson":"张三",
                "address":"北京市朝阳区XXX",
                "phone":"13112341234",
                "lastModifyTime": 1685513394,
                "detailList":[
                    {
                        "shipmentDetailNo":"34232001",
                        "orderDetailNo":"SA202333385003",
                        "productModel":"1-14-1W",
                        "validDate":"2029-09-09",
                        "lot":"1-14-1W",
                        "sn":"FE2452D",
                        "quantity":10,
                        "taxPrice":7777.89
                    },
                    {
                        "shipmentDetailNo":"34232002",
                        "orderDetailNo":"SA202333385003",
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
                "orderType":1,
                "customerId":"WS-FSD23",
                "receivePerson":"李四",
                "address":"北京市朝阳区XXX",
                "phone":"13134566543",
                "lastModifyTime": 1685513394,
                "detailList":[
                    {
	                    "shipmentDetailNo":"366662001",
	                    "orderDetailNo":"SA202333385003",
                        "productModel":"1-14-1W",
                        "validDate":"2029-09-09",
                        "lot":"1-14-1W",
                        "sn":"FE2452D",
                        "quantity":10,
                        "taxPrice":7777.89
                    },
                    {
	                    "shipmentDetailNo":"366662002",
	                    "orderDetailNo":"SA202333385003",
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

* 说明：经销商在唯众系统上报的植入数据，可根据上传参数进行条件查询 

调用地址：/apiservice/getImplants
请求方式：POST			 
Content-Type：application/json
返回类型：JSON

 Body参数

|名称|类型|必填|示例值|描述|
|---|---|---|---|---|
|isNewData|Integer|是| 0|是否为增量数据 0-全量数据  1-增量数据|
|page|Integer|否| 1|页码，1开始 如果isNewData==0 此项必填|
|rows|Integer|否| 500|每页条数，最大值1000 如果isNewData==0 此项必填|
|customerId|Integer|否| 1|代理商编码，查询某个代理商的数据|
|startDate|String|否| 2023-01-01|开始时间|
|endDate|String|否| 2023-01-01|结束时间|
|sign|String|是| dsfsdjfdfadf|验签字段，按照一点的组合顺序进行MD5加密|


 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|code|Integer|0|返回码|
|msg|String|success|成功|
|data|JsonData|-|数据详见下方JsonData|

 JsonData
|名称|类型|示例值|描述|
|---|---|---|---|
|total|Long|4500|数据总数|
|implantData|ImplantData|-|细单数据详见下方ImplantData|
 ImplantData
|名称|类型|示例值|描述|
|---|---|---|---|
|implantNo|String|IM23804|唯众植入单号|
|customerId|Integer|234|经销商代码|
|hospitalId|Integer|3456|医院编码|
|invoiceUnit|String|嘉事唯众|开票单位名称|
|receiveName|String|张三|发票购货方名称|
|invoiceNo|String|2222|发票号码|
|invoiceDate|Date|2020-10-01|发票日期|
|invoiceType|String|01|发票类型,详见发票类型字典|
|invoiceStatus|Integer|0|发票状态,详见发票状态字典|
|invoiceSource|Integer|0|发票来源,详见发票来源字典|
|invoiceCode|String|45678|发票代码|
|invoiceCheckCode|String|123456|发票校验码后六位|
|invoiceAmount|Bigdecimal|4567.67|发票金额|
|reportDate|Date|2022-10-11|上报日期|
|lastModifyTime|Timestamp|1685513394|数据最后更新时间|
|detailList|ImplantDetail|-|细单数据详见下方ImplantDetail|
 ImplantDetail
|名称|类型|示例值|描述|
|---|---|---|---|
|implantDetailNo|String|IM238423423001|唯众系统植入细单编号|
|productModel|String|1-14-1W|产品规格型号|
|validDate|Date|2030-01-01|有效期|
|lot|String|DEF3425|批号|
|sn|String|34567|序列号|
|quantity|Integer|14|数量|
|taxPrice|Bigdecimal|345.74|发票单价|
|taxRate|String|13|税率|
|hospitalPrice|Bigdecimal|345.74|医院单价|

> 返回示例
```json
{
    "code":0,
    "msg":"success",
    "data":{
        "total":40000,
        "implantData":[
            {
                "implantNo":"IM238423423",
                "customerId":2324,
                "hospitalId":4563,
                "invoiceUnit":"开票单位名称A",
                "receiveName":"发票购货方名称B",
                "invoiceNo":"666453",
                "invoiceDate":"2023-05-01",
                "invoiceType":0,
                "invoiceStatus":0,
                "invoiceSource":0,
                "invoiceCode":"45678",
                "invoiceCheckCode":"123456",
                "invoiceAmount":"6574.57",
                "reportDate":"2022-10-23",
                "lastModifyTime": 1685513394,
                "detailList":[
                    {
	                    "implantDetailNo":"IM238423423001",
                        "productModel":"1-14-1W",
                        "validDate":"2029-09-09",
                        "lot":"1-14-1W",
                        "sn":"FE2452D",
                        "quantity":10,
                        "taxPrice":7777.89,
                        "taxRate":"13",
                        "hospitalPrice":7777.89
                    },
                    {
                        "implantDetailNo":"IM238423423002",
                        "productModel":"1-14-1B",
                        "validDate":"2029-09-09",
                        "lot":"SSS",
                        "sn":"FE2452D",
                        "quantity":10,
                        "taxPrice":4763.22,
                        "taxRate":"13",
                        "hospitalPrice":4377.89
                    }
                ]
            },
            {
                "implantNo":"IM238423478",
                "customerId":432,
                "hospitalId":564,
                "invoiceUnit":"开票单位名称C",
                "receiveName":"发票购货方名称D",
                "invoiceNo":"3421",
                "invoiceDate":"2023-04-01",
                "invoiceType":0,
                "invoiceStatus":0,
                "invoiceSource":0,
                "invoiceCode":"2312",
                "invoiceCheckCode":"543423",
                "invoiceAmount":"6574.57",
                "reportDate":"2022-10-23",
                "lastModifyTime": 1685513394,
                "detailList":[
                    {
                        "implantDetailNo":"IM238423478001",
                        "productModel":"1-14-1W",
                        "validDate":"2029-09-09",
                        "lot":"1-14-1W",
                        "sn":"FE2452D",
                        "quantity":10,
                        "taxPrice":7777.89,
                        "taxRate":"13",
                        "hospitalPrice":7777.89
                    },
                    {
                        "implantDetailNo":"IM238423478002",
                        "productModel":"1-14-1B",
                        "validDate":"2029-09-09",
                        "lot":"SSS",
                        "sn":"FE2452D",
                        "quantity":10,
                        "taxPrice":4763.22,
                        "taxRate":"13",
                        "hospitalPrice":4377.89
                    }
                ]
            }
        ]
    }
}
```
### 2.5 获取退货数据

	说明：以任何原因由代理商退货到唯众的产品，可根据上传参数进行条件查询 

调用地址：/apiservice/getReturnData
请求方式：POST			 
Content-Type：application/json
返回类型：JSON

 Body参数

|名称|类型|必填|示例值|描述|
|---|---|---|---|---|
|isNewData|Integer|是| 0|是否为增量数据 0-全量数据  1-增量数据|
|page|Integer|否| 1|页码，1开始 如果isNewData==0 此项必填|
|rows|Integer|否| 500|每页条数，最大值1000 如果isNewData==0 此项必填|
|customerId|Integer|否| 1|代理商编码，查询某个代理商的数据|
|startDate|String|否| 2023-01-01|开始时间|
|endDate|String|否| 2023-05-01|结束时间|
|sign|String|是| dsfsdjfdfadf|验签字段，按照一点的组合顺序进行MD5加密|


 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|code|Integer|0|返回码|
|msg|String|success|成功|
|data|JsonData|-|数据详见下方JsonData|

 JsonData
|名称|类型|示例值|描述|
|---|---|---|---|
|total|Long|-|数据总数|
|returnData|ReturnData|-|细单数据详见下方ReturnData|
 ReturnData
|名称|类型|示例值|描述|
|---|---|---|---|
|returnNo|String|RT2306020001|唯众退货编号|
|returnDate|Date|2020-10-10|退货日期|
|customerId|Integer|3456|代理商编码|
|returnTypeId|Integer|123|退货类型编码,详见退货类型字典|
|lastModifyTime|Timestamp|1685513394|数据最后更新时间|
|detailList|ReturnDetail|-|细单数据详见下方ReturnDetail|
 ReturnDetail
|名称|类型|示例值|描述|
|---|---|---|---|
|returnDetailNo|String|RT2306020001001|唯众退货细单编号|
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
        "total":4500,
        "returnData":[
            {
                "returnNo":"RT2306020001",
                "returnDate":"2023-05-01",
                "customerId":2324,
                "returnTypeId":4563,
                "lastModifyTime": 1685513394,
                "detailList":[
                    { 
	                    "returnDetailNo":"RT2306020001001",
                        "productModel":"1-14-1W",
                        "validDate":"2029-09-09",
                        "lot":"1-14-1W",
                        "sn":"FE2452D",
                        "quantity":10
                    },
                    {
	                    "returnDetailNo":"RT2306020001002",
                        "productModel":"1-14-1B",
                        "validDate":"2029-09-09",
                        "lot":"SSS",
                        "sn":"FE2452D",
                        "quantity":10
                    }
                ]
            },
            {
                "returnNo":"RT234234239",
                "returnDate":"2023-05-01",
                "customerId":2324,
                "returnTypeId":4563,
                "lastModifyTime": 1685513394,
                "detailList":[
                    {
                        "returnDetailNo":"RT234234239001",
                        "productModel":"1-14-1W",
                        "validDate":"2029-09-09",
                        "lot":"1-14-1W",
                        "sn":"FE2452D",
                        "quantity":10
                    },
                    {
                        "returnDetailNo":"RT234234239002",
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
### 2.6 获取植入上报状态

	说明：经销商植入上报当前状态，可根据上传参数进行条件查询 

调用地址：/apiservice/getImplantStatus
请求方式：POST			 
Content-Type：application/json
返回类型：JSON

 Body参数

|名称|类型|必填|示例值|描述|
|---|---|---|---|---|
|isNewData|Integer|是| 0|是否为增量数据 0-全量数据  1-增量数据|
|page|Integer|否| 1|页码，1开始 如果isNewData==0 此项必填|
|rows|Integer|否| 500|每页条数，最大值1000 如果isNewData==0 此项必填|
|customerId|Integer|否| 1|代理商编码，查询某个代理商的数据|
|startDate|String|否| 2023-01-01|开始时间|
|endDate|String|否| 2023-05-01|结束时间|
|sign|String|是| dsfsdjfdfadf|验签字段，按照一点的组合顺序进行MD5加密|

 返回参数
|名称|类型|示例值|描述|
|---|---|---|---|
|code|Integer|0|返回码|
|msg|String|success|成功|
|data|JsonData|-|数据详见下方JsonData|

 JsonData
|名称|类型|示例值|描述|
|---|---|---|---|
|total|Long|-|数据总数|
|implantStatusData|ImplantStatusData|-|细单数据详见下方ImplantStatusData|
 ImplantStatusData
|名称|类型|示例值|描述|
|---|---|---|---|
|customerId|Integer|3456|代理商编码|
|date|String|2023-01|2023年1月份|
|implantStatus|ReturnDetail|1|详见植入上报状态字典|
|lastModifyTime|Timestamp|1685513394|数据最后更新时间|

> 返回示例
```json
{
    "code":0,
    "msg":"success",
    "data":{
        "total":4500,
        "implantStatusData":[
            {
                "date":"2023-01",
                "customerId":2324,
                "implantStatus":1,
                "lastModifyTime": 1685513394
            },
            {
                "date":"2023-02",
                "customerId":2324,
                "implantStatus":2,
                "lastModifyTime": 1685513394
            }
        ]
    }
}
```
## 3 数据字典
    说明：数据字典部分需要根据实际开发时进行调整
### 3.1 退货类型字典
|code|描述|
|---|---|
|1|退货|
|2|换货|
### 3.2 发票类型字典
|code|描述|
|---|---|
|01|增值税专用发票|
|02|货物运输业增值税专用发票|
|03|机动车销售统一发票|
|04|增值税普通发票|
|08|增值税电子专用发票|
|10|增值税电子普通发票|
|11|增值税普通发票(卷票)|
|14|增值税电子普通发票(通行费)|
|15|二手车销售统一发票|


### 3.3 植入上报状态字典
|code|描述|
|---|---|
|0|无上报|
|1|未上报|
|2|上报中|
|3|上报完成|
### 3.4 发货类型字典
|code|描述|
|---|---|
|1|快递|
|2|自提|
### 3.5 订单类型字典
|code|描述|
|---|---|
|1|正常订单|
|2|IVUS设备借用|
|3|超级智能套包③|
|4|超级智能套包②|
|5|超级智能套包①|
|6|其他|

### 3.6 订单状态字典
|code|描述|
|---|---|
|1|待提交|
|2|审批中|
|3|备货中|
|4|已发货|
|5|已完成|
### 3.7 发票来源字典
|code|描述|
|---|---|
|0|非医院发票|
|1|医院发票|
### 3.8 发票状态字典
|code|描述|
|---|---|
|0|作废|
|1|红冲|
|2|正常通过|
## 4 返回码
|code|说明|
|---|---|
|0|api请求成功|
|500|服务器异常|
|5001|应用配置错误|
|5002|accessToken 校验失败|
|5003|accessToken 已过期|
|5004|请求参数不符合规范|


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ4MTU1NDg1NSwtMjAwMjI1OTgwOSwxNz
g3ODcwNzU2LC0xODQxMzI1OTQ0LC0xODQ0NjI1MDY2LC0xMzM5
ODI4MDI4LC0xMzM5ODI4MDI4LDEyMjA0NzM4MzksLTY0MzQ1Nz
U3MSwxODk4NDk2MTQzLC0xMzE0NzU5MTg1LC0xODg1ODczMjY1
LC04MzExMDQxMzYsLTQ4Nzk3MzQ2MiwtMTUyMTE0NjcsLTEwNT
IxOTc2NzUsMTI4OTU5NTMwMCwtMjEwNTQ4MDU5MCwtMjA5MTE0
NDMyNCwxMTg0NDY0NDRdfQ==
-->