


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
**    通过此接口获取授权的 access_token，调用服务端 API 获取应用资源时需要通过 access_token 来鉴权调用者身份进行授权 **

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
|data|Object|---|---|
|---|---|---|---|
|---|---|---|---|
|---|---|---|---|

> 返回示例

```json
{
  "code": 0,
  "msg": "success",
  "data": 
    {
      "access_token": "fghjkrtyuifgbn5678",
      "expires": 7200
    }
}
```



### 2.2 POST 订单数据

**    经销商在唯众平台的订货数据 **

调用地址：jswz/apiservice/getorders
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
|data|Object|---|---|
|---|---|---|---|
|---|---|---|---|
|---|---|---|---|

> 返回示例

```json
{
  "code": 0,
  "msg": "success",
  "data": 
    {
      "access_token": "fghjkrtyuifgbn5678",
      "expires": 7200
    }
}
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU2OTQwNjU5MSwtMzUyNzI2NTQyLDE3Nj
A4MzYwOTUsMTg5MTA2ODU3MiwtMTA3Njg3MjMwOSwxNzk4NTYz
MjI1LC02NDQ2NjU2MCwxMjgwOTA2NTM2XX0=
-->