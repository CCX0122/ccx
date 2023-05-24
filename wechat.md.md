


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

POST /control/order/list

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|page|query|integer| 是 |none|
|rows|query|integer| 是 |none|
|startDate|query|string| 否 |none|
|endDate|query|string| 否 |none|
|customerName|query|string| 否 |none|
|orderStatus|query|integer| 否 |-9:提交失败 -4:已提交 -3:退回修改 -2:中止 -1:作废 1:待提交 2:审批中 3:备货中 4:已发货 5:已完成|
|orderNo|query|string| 否 |订单号|

> 返回示例

> 成功

```json
{
  "code": 0,
  "msg": "success",
  "data": [
    {
      "id": 100284,
      "order_no": "SA2209190049",
      "customer_id": 2610,
      "customer_person_id": 1880,
      "customer_address_id": 6712,
      "producer_id": 1799,
      "quantity": 22,
      "value": 123600,
      "orig_value": 123600,
      "order_type_id": 1,
      "status": 0,
      "erp_status": 0,
      "received_quantity": 0,
      "transit_quantity": 0,
      "transit_company_id": null,
      "transit_type_id": null,
      "date": "2022-09-19 10:22:58",
      "memo": "",
      "doc_memo": "055-127要改进型的经桡的，抽吸导管请发最新批号效期的，谢谢",
      "wz_id": "",
      "created_at": "2022-09-19 10:22:58",
      "updated_at": "2022-09-19 14:31:33",
      "wz_updated": null,
      "yj_status": 5,
      "is_zy": 0,
      "is_yj": 1,
      "is_modified": 0,
      "platform_id": 17,
      "shipment_quantity": 22,
      "coupon_status": 1,
      "coupon_matched": null,
      "paid_time": "2022-09-19 14:11:25",
      "send_status": 0,
      "suite_group_id": null
    },
    {
      "id": 100286,
      "order_no": "SA2209190051",
      "customer_id": 2610,
      "customer_person_id": 1880,
      "customer_address_id": 6712,
      "producer_id": 1799,
      "quantity": 2,
      "value": 0,
      "orig_value": 0,
      "order_type_id": 3,
      "status": 0,
      "erp_status": 0,
      "received_quantity": 0,
      "transit_quantity": 0,
      "transit_company_id": null,
      "transit_type_id": null,
      "date": "2022-09-19 10:23:40",
      "memo": "",
      "doc_memo": null,
      "wz_id": "",
      "created_at": "2022-09-19 10:23:40",
      "updated_at": "2022-09-19 14:31:33",
      "wz_updated": null,
      "yj_status": 5,
      "is_zy": 0,
      "is_yj": 1,
      "is_modified": 0,
      "platform_id": 17,
      "shipment_quantity": 2,
      "coupon_status": 1,
      "coupon_matched": null,
      "paid_time": "2022-09-19 14:11:25",
      "send_status": 0,
      "suite_group_id": null
    }
  ],
  "dictionary": [
    {
      "field": "yj_status",
      "describe": "订单状态",
      "info": [
        {
          "code": -2,
          "name": "作废"
        },
        {
          "code": -3,
          "name": "退回修改"
        },
        {
          "code": 2,
          "name": "审批中"
        },
        {
          "code": 3,
          "name": "备货中"
        },
        {
          "code": 4,
          "name": "已发货"
        },
        {
          "code": 5,
          "name": "已完成"
        }
      ]
    },
    {
      "field": "order_type_id",
      "describe": "类型",
      "info": [
        {
          "code": 32,
          "name": "过期换货补货单"
        },
        {
          "code": 1,
          "name": "正常订单"
        },
        {
          "code": 33,
          "name": "投诉换货补货单"
        },
        {
          "code": 2,
          "name": "寄售订单"
        },
        {
          "code": 3,
          "name": "促销订单"
        },
        {
          "code": 31,
          "name": "赠品订单"
        }
      ]
    },
    {
      "field": "platform_id",
      "describe": "平台名称",
      "info": [
        {
          "code": 17,
          "name": "嘉事唯众"
        }
      ]
    },
    {
      "field": "customer_id",
      "describe": "代理商名称",
      "info": [
        {
          "code": 2610,
          "name": "山东瑞卓医疗科技有限公司"
        }
      ]
    }
  ],
  "total": 441
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|null|true|none||none|
|» dictionary|null|true|none||none|
|» total|integer|true|none||none|

## POST 订单详情

POST /control/order/detail

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|orderNo|query|string| 是 |订单号|

> 返回示例

> 成功

```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "mainData": [
      {
        "title": "订单号",
        "field": "order_no",
        "info": "SA2209190166"
      },
      {
        "title": "客户",
        "field": "customer_name",
        "info": "宜宾维诺方医疗器械有限公司"
      },
      {
        "title": "订单类型",
        "field": "order_type_name",
        "info": "促销订单"
      },
      {
        "title": "厂家",
        "field": "producer_name",
        "info": "威海禾木吉瑞生物科技有限公司"
      },
      {
        "title": "发货单",
        "field": "shipment_no",
        "info": "980023"
      },
      {
        "title": "收货地址",
        "field": "address",
        "info": "四川省宜宾市叙州区安边镇豆坝社区金沙家园20号13795838877宜宾维诺方医疗器械有限公司-7"
      },
      {
        "title": "备注",
        "field": "doc_memo",
        "info": "四川省成都市天府新区华府大道一段688号益州国际"
      }
    ],
    "productList": [
      [
        {
          "title": "产品名称",
          "field": "product_name",
          "info": "神经血管球囊导管"
        },
        {
          "title": "型号",
          "field": "model",
          "info": "NBLN-2.0X09"
        },
        {
          "title": "规格",
          "field": "specification",
          "info": "NBLN-2.0X09"
        },
        {
          "title": "单价",
          "field": "price",
          "info": 0
        },
        {
          "title": "数量",
          "field": "quantity",
          "info": 4
        },
        {
          "title": "已发数量",
          "field": "shipment_quantity",
          "info": 0
        },
        {
          "title": "取消数量",
          "field": "cancel_quantity",
          "info": 0
        },
        {
          "title": "总价",
          "field": "total_price",
          "info": 0
        }
      ],
      [
        {
          "title": "产品名称",
          "field": "product_name",
          "info": "神经血管球囊导管"
        },
        {
          "title": "型号",
          "field": "model",
          "info": "NBLN-2.25X09"
        },
        {
          "title": "规格",
          "field": "specification",
          "info": "NBLN-2.25X09"
        },
        {
          "title": "单价",
          "field": "price",
          "info": 0
        },
        {
          "title": "数量",
          "field": "quantity",
          "info": 1
        },
        {
          "title": "已发数量",
          "field": "shipment_quantity",
          "info": 0
        },
        {
          "title": "取消数量",
          "field": "cancel_quantity",
          "info": 0
        },
        {
          "title": "总价",
          "field": "total_price",
          "info": 0
        }
      ],
      [
        {
          "title": "产品名称",
          "field": "product_name",
          "info": "神经血管球囊导管"
        },
        {
          "title": "型号",
          "field": "model",
          "info": "NBLN-3.0X09"
        },
        {
          "title": "规格",
          "field": "specification",
          "info": "NBLN-3.0X09"
        },
        {
          "title": "单价",
          "field": "price",
          "info": 0
        },
        {
          "title": "数量",
          "field": "quantity",
          "info": 1
        },
        {
          "title": "已发数量",
          "field": "shipment_quantity",
          "info": 0
        },
        {
          "title": "取消数量",
          "field": "cancel_quantity",
          "info": 0
        },
        {
          "title": "总价",
          "field": "total_price",
          "info": 0
        }
      ],
      [
        {
          "title": "产品名称",
          "field": "product_name",
          "info": "神经血管球囊导管"
        },
        {
          "title": "型号",
          "field": "model",
          "info": "NBLN-2.0X12"
        },
        {
          "title": "规格",
          "field": "specification",
          "info": "NBLN-2.0X12"
        },
        {
          "title": "单价",
          "field": "price",
          "info": 0
        },
        {
          "title": "数量",
          "field": "quantity",
          "info": 4
        },
        {
          "title": "已发数量",
          "field": "shipment_quantity",
          "info": 0
        },
        {
          "title": "取消数量",
          "field": "cancel_quantity",
          "info": 0
        },
        {
          "title": "总价",
          "field": "total_price",
          "info": 0
        }
      ],
      [
        {
          "title": "产品名称",
          "field": "product_name",
          "info": "神经血管球囊导管"
        },
        {
          "title": "型号",
          "field": "model",
          "info": "NBLN-2.25X12"
        },
        {
          "title": "规格",
          "field": "specification",
          "info": "NBLN-2.25X12"
        },
        {
          "title": "单价",
          "field": "price",
          "info": 0
        },
        {
          "title": "数量",
          "field": "quantity",
          "info": 1
        },
        {
          "title": "已发数量",
          "field": "shipment_quantity",
          "info": 0
        },
        {
          "title": "取消数量",
          "field": "cancel_quantity",
          "info": 0
        },
        {
          "title": "总价",
          "field": "total_price",
          "info": 0
        }
      ],
      [
        {
          "title": "产品名称",
          "field": "product_name",
          "info": "神经血管球囊导管"
        },
        {
          "title": "型号",
          "field": "model",
          "info": "NBLN-2.5X12"
        },
        {
          "title": "规格",
          "field": "specification",
          "info": "NBLN-2.5X12"
        },
        {
          "title": "单价",
          "field": "price",
          "info": 0
        },
        {
          "title": "数量",
          "field": "quantity",
          "info": 4
        },
        {
          "title": "已发数量",
          "field": "shipment_quantity",
          "info": 0
        },
        {
          "title": "取消数量",
          "field": "cancel_quantity",
          "info": 0
        },
        {
          "title": "总价",
          "field": "total_price",
          "info": 0
        }
      ],
      [
        {
          "title": "产品名称",
          "field": "product_name",
          "info": "神经血管球囊导管"
        },
        {
          "title": "型号",
          "field": "model",
          "info": "NBLN-2.5X15"
        },
        {
          "title": "规格",
          "field": "specification",
          "info": "NBLN-2.5X15"
        },
        {
          "title": "单价",
          "field": "price",
          "info": 0
        },
        {
          "title": "数量",
          "field": "quantity",
          "info": 2
        },
        {
          "title": "已发数量",
          "field": "shipment_quantity",
          "info": 0
        },
        {
          "title": "取消数量",
          "field": "cancel_quantity",
          "info": 0
        },
        {
          "title": "总价",
          "field": "total_price",
          "info": 0
        }
      ]
    ]
  },
  "dictionary": null,
  "total": 1
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|object|true|none||none|
|»» mainData|[object]|true|none||none|
|»»» title|string|true|none||none|
|»»» field|string|true|none||none|
|»»» info|string|true|none||none|
|»» productList|[array]|true|none||none|
|»»» title|string|true|none||none|
|»»» field|string|true|none||none|
|»»» info|string|true|none||none|
|dictionary|null|true|none||none|
|total|integer|true|none||none|

## POST 发货列表

POST /control/shipment/list

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|page|query|integer| 是 |页码1开始|
|rows|query|integer| 是 |每页条数|
|startDate|query|string| 否 |开始日期YYYY-MM-DD|
|endDate|query|string| 否 |结束日期YYYY-MM-DD|
|customerName|query|string| 否 |代理商名称|
|shipmentNo|query|string| 否 |发货单号|
|logisticsNo|query|string| 否 |运单号|
|shipLogNo|query|string| 否 |发货单号或者运单号|

> 返回示例

> 成功

```json
{
  "code": 0,
  "msg": "success",
  "data": [
    {
      "id": 123211,
      "shipment_no": "980032",
      "customer_id": 4988,
      "customer_person_id": null,
      "order_id": 99960,
      "quantity": 1,
      "confirm_quantity": 0,
      "delivery_time": "2022-09-20 11:35:02",
      "confirm_time": "2022-09-20 11:41:49",
      "status": 0,
      "storehouse": 0,
      "delivery_type": 0,
      "logistics_no": null,
      "logistics_type": null,
      "cost_type": 0,
      "type": 1,
      "wz_id": "980032",
      "created_at": "2022-09-20 11:41:49",
      "updated_at": "2022-09-20 11:41:49",
      "receiver_phone": null,
      "sender_phone": null,
      "logistics_status": 0,
      "logistics_trace": null,
      "logistics_errmsg": null,
      "wz_updated": "2022-09-20 11:35:02",
      "is_yj": 1,
      "orig_customer_id": 4988,
      "platform_id": 1840,
      "return_order_id": null,
      "send_status": 0,
      "send_error": null,
      "order_no": "SA2209150086"
    },
    {
      "id": 123198,
      "shipment_no": "980023",
      "customer_id": 5153,
      "customer_person_id": null,
      "order_id": 100401,
      "quantity": 17,
      "confirm_quantity": 0,
      "delivery_time": "2022-09-20 10:48:32",
      "confirm_time": "2022-09-20 10:51:54",
      "status": 0,
      "storehouse": 0,
      "delivery_type": 0,
      "logistics_no": null,
      "logistics_type": null,
      "cost_type": 0,
      "type": 1,
      "wz_id": "980023",
      "created_at": "2022-09-20 10:51:54",
      "updated_at": "2022-09-20 10:51:56",
      "receiver_phone": null,
      "sender_phone": null,
      "logistics_status": 0,
      "logistics_trace": null,
      "logistics_errmsg": null,
      "wz_updated": "2022-09-20 10:48:32",
      "is_yj": 1,
      "orig_customer_id": 5153,
      "platform_id": 1840,
      "return_order_id": null,
      "send_status": 0,
      "send_error": null,
      "order_no": "SA2209190166"
    },
    {
      "id": 123186,
      "shipment_no": "980021",
      "customer_id": 4935,
      "customer_person_id": null,
      "order_id": 100363,
      "quantity": 4,
      "confirm_quantity": 0,
      "delivery_time": "2022-09-20 10:48:27",
      "confirm_time": "2022-09-20 10:51:47",
      "status": 0,
      "storehouse": 0,
      "delivery_type": 0,
      "logistics_no": null,
      "logistics_type": null,
      "cost_type": 0,
      "type": 1,
      "wz_id": "980021",
      "created_at": "2022-09-20 10:51:47",
      "updated_at": "2022-09-20 10:51:47",
      "receiver_phone": null,
      "sender_phone": null,
      "logistics_status": 0,
      "logistics_trace": null,
      "logistics_errmsg": null,
      "wz_updated": "2022-09-20 10:48:27",
      "is_yj": 1,
      "orig_customer_id": 4935,
      "platform_id": 1840,
      "return_order_id": null,
      "send_status": 0,
      "send_error": null,
      "order_no": "SA2209190128"
    },
    {
      "id": 122719,
      "shipment_no": "978869",
      "customer_id": 4988,
      "customer_person_id": null,
      "order_id": 100079,
      "quantity": 2,
      "confirm_quantity": 0,
      "delivery_time": "2022-09-16 15:59:35",
      "confirm_time": "2022-09-16 16:02:08",
      "status": 0,
      "storehouse": 0,
      "delivery_type": 0,
      "logistics_no": null,
      "logistics_type": null,
      "cost_type": 0,
      "type": 1,
      "wz_id": "978869",
      "created_at": "2022-09-16 16:02:08",
      "updated_at": "2022-09-16 16:02:09",
      "receiver_phone": null,
      "sender_phone": null,
      "logistics_status": 0,
      "logistics_trace": null,
      "logistics_errmsg": null,
      "wz_updated": "2022-09-16 15:59:35",
      "is_yj": 1,
      "orig_customer_id": 4988,
      "platform_id": 1840,
      "return_order_id": null,
      "send_status": 0,
      "send_error": null,
      "order_no": "SA2209160042"
    }
  ],
  "dictionary": [
    {
      "field": "platform_id",
      "describe": "平台名称",
      "info": [
        {
          "code": 1840,
          "name": "嘉事吉建"
        }
      ]
    },
    {
      "field": "customer_id",
      "describe": "代理商名称",
      "info": [
        {
          "code": 4935,
          "name": "上海木仪医疗科技有限公司"
        },
        {
          "code": 4988,
          "name": "江苏曼太医疗科技有限公司"
        },
        {
          "code": 5153,
          "name": "宜宾维诺方医疗器械有限公司"
        }
      ]
    },
    {
      "field": "status",
      "describe": "状态",
      "info": [
        {
          "code": 0,
          "name": "待确认收货"
        },
        {
          "code": 1,
          "name": "部分收货"
        },
        {
          "code": 2,
          "name": "确认收货"
        }
      ]
    }
  ],
  "total": 417
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||0表示成功|
|» msg|string|true|none||提示信息|
|» data|[object]|true|none||发货单列表|
|»» id|integer|false|none||发货单id|
|»» shipment_no|string|false|none||发货单号|
|»» customer_id|integer|false|none||代理商id|
|»» customer_person_id|null|false|none||none|
|»» order_id|integer|false|none||订单id|
|»» quantity|integer|false|none||发货数量|
|»» confirm_quantity|integer|false|none||确认收货数量|
|»» delivery_time|string|false|none||发货时间|
|»» confirm_time|string|false|none||收货时间|
|»» status|integer|false|none||none|
|»» storehouse|integer|false|none||none|
|»» delivery_type|integer|false|none||none|
|»» logistics_no|null|false|none||none|
|»» logistics_type|null|false|none||none|
|»» cost_type|integer|false|none||none|
|»» type|integer|false|none||none|
|»» wz_id|string|false|none||none|
|»» created_at|string|false|none||none|
|»» updated_at|string|false|none||none|
|»» receiver_phone|null|false|none||none|
|»» sender_phone|null|false|none||none|
|»» logistics_status|integer|false|none||none|
|»» logistics_trace|null|false|none||none|
|»» logistics_errmsg|null|false|none||none|
|»» wz_updated|string|false|none||none|
|»» is_yj|integer|false|none||none|
|»» orig_customer_id|integer|false|none||none|
|»» platform_id|integer|false|none||平台商ID|
|»» return_order_id|null|false|none||none|
|»» send_status|integer|false|none||none|
|»» send_error|null|false|none||none|
|» total|integer|true|none|总数量|none|
|» dictionary|object|true|none|字典|none|

## POST 发货详情

POST /control/shipment/detail

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|shipmentNo|query|string| 是 |发货单号|

> 返回示例

> 成功

```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "mainData": [
      {
        "title": "发货单",
        "field": "shipment_id",
        "info": 122698
      },
      {
        "title": "客户",
        "field": "customer_name",
        "info": "江苏曼太医疗科技有限公司"
      },
      {
        "title": "订单",
        "field": "order_no",
        "info": "SA2209160078"
      },
      {
        "title": "厂家",
        "field": "producer_name",
        "info": "威海禾木吉瑞生物科技有限公司"
      },
      {
        "title": "收货地址",
        "field": "address",
        "info": "苏州市姑苏区南环东路10号新联大厦2幢1308室"
      },
      {
        "title": "运单号",
        "field": "logistics_no",
        "info": ""
      }
    ],
    "productList": [
      [
        {
          "title": "产品名称",
          "field": "name",
          "info": "血管内通路导管系统"
        },
        {
          "title": "型号",
          "field": "model",
          "info": "ERAC-071-115"
        },
        {
          "title": "规格",
          "field": "specification",
          "info": "ERAC-071-115"
        },
        {
          "title": "批号",
          "field": "lot",
          "info": "13220061"
        },
        {
          "title": "有效期",
          "field": "valid_date",
          "info": "2025-04-01"
        },
        {
          "title": "数量",
          "field": "quantity",
          "info": 1
        }
      ],
      [
        {
          "title": "产品名称",
          "field": "name",
          "info": "血管内通路导管系统"
        },
        {
          "title": "型号",
          "field": "model",
          "info": "ERAC-065-127"
        },
        {
          "title": "规格",
          "field": "specification",
          "info": "ERAC-065-127"
        },
        {
          "title": "批号",
          "field": "lot",
          "info": "13210144"
        },
        {
          "title": "有效期",
          "field": "valid_date",
          "info": "2024-07-13"
        },
        {
          "title": "数量",
          "field": "quantity",
          "info": 1
        }
      ]
    ]
  },
  "dictionary": null,
  "total": 1
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|object|true|none||none|
|»» mainData|[object]|true|none||none|
|»»» title|string|true|none||none|
|»»» field|string|true|none||none|
|»»» info|integer|true|none||none|
|»» productList|[array]|true|none||none|
|»»» title|string|true|none||none|
|»»» field|string|true|none||none|
|»»» info|string|true|none||none|
|dictionary|null|true|none||none|
|total|integer|true|none||none|

## POST 植入列表

POST /control/implant/list

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|page|query|integer| 是 |页码1开始|
|rows|query|integer| 是 |每页条数|
|startDate|query|string| 否 |开始日期yyyy-MM-DD|
|endDate|query|string| 否 |结束日期YYYY-MM-DD|
|hospitalName|query|string| 否 |医院名称|
|customerName|query|string| 否 |代理商名称|
|implantNo|query|string| 否 |植入单号|
|hosCusName|query|string| 否 |医院名称或者代理商名称|

> 返回示例

> 成功

```json
{
  "code": 0,
  "msg": "success",
  "data": [
    {
      "id": 105203,
      "implant_no": "IM2208300130",
      "customer_id": 4935,
      "customer_person_id": 3215,
      "producer_id": 4777,
      "hospital_id": 5220,
      "date": "2022-08-01",
      "invoice_no": "32756645",
      "invoice_file": "[{\"download_link\":\"implant-invoices\\/ZoEwQwkLqVKkU6Cj0vOVkYYblZy6avC3BDir1NTX.jpg\",\"original_name\":\"\\u5fae\\u4fe1\\u56fe\\u7247_202208301450022.jpg\"}]",
      "invoice_company_id": 1696,
      "invoice_date": "2022-08-01",
      "status": 3,
      "wz_id": null,
      "wz_updated": null,
      "created_at": "2022-08-30T14:57:59",
      "updated_at": "2022-08-30T14:57:59",
      "return_memo": null,
      "platform_id": 1840,
      "send_status": 0,
      "submit_time": "2022-08-30T14:57:59",
      "memo": null,
      "is_reopen": 0,
      "checked_customer_id": null,
      "checked_at": null,
      "tax_rate": null,
      "receipt_file": null
    },
    {
      "id": 105676,
      "implant_no": "IM2208310336",
      "customer_id": 4914,
      "customer_person_id": 2563,
      "producer_id": 4777,
      "hospital_id": 4691,
      "date": "2022-08-30",
      "invoice_no": "12240597",
      "invoice_file": "[{\"download_link\":\"implant-invoices\\/n1OWnoJtPX1frCIsueIdc1K2tAaYdYdkMiPzVzHj.jpg\",\"original_name\":\"12240597.jpg\"}]",
      "invoice_company_id": 1279,
      "invoice_date": "2022-08-30",
      "status": 3,
      "wz_id": null,
      "wz_updated": null,
      "created_at": "2022-08-31T16:25:16",
      "updated_at": "2022-08-31T16:25:16",
      "return_memo": null,
      "platform_id": 1840,
      "send_status": 0,
      "submit_time": "2022-08-31T16:25:16",
      "memo": null,
      "is_reopen": 0,
      "checked_customer_id": null,
      "checked_at": null,
      "tax_rate": null,
      "receipt_file": null
    }
  ],
  "dictionary": [
    {
      "field": "hospital_id",
      "describe": "医院名称",
      "info": [
        {
          "code": 4691,
          "name": "徐州市矿山医院"
        },
        {
          "code": 5220,
          "name": "如东县人民医院"
        }
      ]
    },
    {
      "field": "customer_id",
      "describe": "代理商名称",
      "info": [
        {
          "code": 4914,
          "name": "上海巧穆贸易有限公司"
        },
        {
          "code": 4935,
          "name": "上海木仪医疗科技有限公司"
        }
      ]
    },
    {
      "field": "platform_id",
      "describe": "平台名称",
      "info": [
        {
          "code": 1840,
          "name": "嘉事吉建"
        }
      ]
    }
  ],
  "total": 150
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none|返回码|0 表示成功|
|» msg|string|true|none|提示信息|none|
|» data|[object]|true|none|数据|none|
|»» id|integer|true|none||植入列表id|
|»» implant_no|string|true|none||植入编号|
|»» customer_id|integer|true|none||代理商id|
|»» customer_person_id|integer|true|none||none|
|»» producer_id|integer|true|none||厂商id|
|»» hospital_id|integer|true|none||医院id|
|»» date|string|true|none||植入日期|
|»» invoice_no|string|true|none||发票号|
|»» invoice_file|string|true|none||发票附件|
|»» invoice_company_id|integer|true|none||开票公司ID|
|»» invoice_date|string|true|none||发票日期|
|»» status|integer|true|none||状态|
|»» wz_id|null|true|none||none|
|»» wz_updated|null|true|none||none|
|»» created_at|string|true|none||创建时间|
|»» updated_at|string|true|none||更新时间|
|»» return_memo|null|true|none||退回备注信息|
|»» platform_id|integer|true|none||平台id|
|»» send_status|integer|true|none||上传到厂家的状态|
|»» submit_time|string|true|none||单据提交时间|
|»» memo|null|true|none||备注|
|»» is_reopen|integer|true|none||是否补报|
|»» checked_customer_id|null|true|none||审核的上级平台ID|
|»» checked_at|null|true|none||审核时间|
|»» tax_rate|null|true|none||税率|
|»» receipt_file|null|true|none||none|
|» dictionary|[object]|true|none|字典|none|
|»» field|string|true|none||none|
|»» describe|string|true|none||none|
|»» info|[object]|true|none||none|
|»»» code|integer|true|none||none|
|»»» name|string|true|none||none|
|» total|integer|true|none|总条数|none|

## POST 植入详情

POST /control/implant/detail

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|implantNo|query|string| 否 |植入单号|

> 返回示例

> 成功

```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "mainData": [
      {
        "title": "植入单号",
        "field": "implant_no",
        "info": "IM2208300130"
      },
      {
        "title": "客户",
        "field": "customer_name",
        "info": "上海木仪医疗科技有限公司"
      },
      {
        "title": "医院",
        "field": "hospital_name",
        "info": "如东县人民医院"
      },
      {
        "title": "植入日期",
        "field": "date",
        "info": "2022-08-01"
      },
      {
        "title": "发票号",
        "field": "invoice_no",
        "info": "32756645"
      },
      {
        "title": "发票附件",
        "field": "invoice_num",
        "info": [
          1,
          2
        ]
      }
    ],
    "productList": [
      [
        {
          "title": "产品名称",
          "field": "name",
          "info": "血管内通路导管系统"
        },
        {
          "title": "型号",
          "field": "model",
          "info": "ERAC-088-90"
        },
        {
          "title": "规格",
          "field": "specification",
          "info": "ERAC-088-90"
        },
        {
          "title": "批号",
          "field": "lot",
          "info": "13210212"
        },
        {
          "title": "有效期至",
          "field": "valid_date",
          "info": "2024-11-11"
        },
        {
          "title": "数量",
          "field": "quantity",
          "info": 1
        }
      ]
    ]
  },
  "dictionary": null,
  "total": 1
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|object|true|none||none|
|»» mainData|[object]|true|none||none|
|»»» title|string|true|none||none|
|»»» field|string|true|none||none|
|»»» info|[integer]|true|none||none|
|»» productList|[array]|true|none||none|
|»»» title|string|true|none||none|
|»»» field|string|true|none||none|
|»»» info|string|true|none||none|
|dictionary|null|true|none||none|
|total|integer|true|none||none|

## POST 查询是否绑定

POST /control/user/isBind

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|openid|query|string| 是 |微信唯一标识|
|wx|query|string| 是 |微信号|

> 返回示例

> 成功

```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "name": "ccx",
    "type": "manufacture",
    "username": "ccx"
  },
  "dictionary": null,
  "total": 0
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|object|true|none||none|
|»» name|string|true|none||姓名|
|»» type|string|true|none||角色|
|»» username|string|true|none||登录名|
|» dictionary|null|true|none||none|
|» total|integer|true|none||none|

## POST 绑定

POST /control/user/bind

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|username|query|string| 是 |用户名|
|password|query|string| 是 |密码|
|openid|query|string| 是 |微信openid|
|wx|query|string| 是 |微信号|

> 返回示例

> 成功

```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "name": "ccx",
    "type": "manufacture",
    "username": "ccx"
  },
  "dictionary": null,
  "total": 0
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|object|true|none||none|
|»» name|string|true|none||姓名|
|»» type|string|true|none||角色类型|
|»» username|string|true|none||登录名|
|» dictionary|null|true|none||none|
|» total|integer|true|none||none|

## POST 解除绑定

POST /control/user/bindFree

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|openid|query|string| 是 |微信唯一标识|
|wx|query|string| 是 |微信号|

> 返回示例

> 成功

```json
{
  "code": 0,
  "msg": "解绑成功！",
  "data": null,
  "dictionary": null,
  "total": 0
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|string|true|none||none|
|» dictionary|null|true|none||none|
|» total|integer|true|none||none|

## POST 代理商列表

POST /control/customer/list

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|page|query|integer| 是 |none|
|rows|query|integer| 是 |none|
|customerName|query|string| 否 |代理商名称|

> 返回示例

> 成功

```json
{
  "code": 0,
  "msg": "success",
  "data": [
    {
      "yj_customer_id": 3495,
      "customer_name": "安徽迅康医疗科技有限公司",
      "hospital_total": 2
    },
    {
      "yj_customer_id": 4260,
      "customer_name": "广西瑞豪医药咨询有限公司",
      "hospital_total": 4
    },
    {
      "yj_customer_id": 3396,
      "customer_name": "贵州和奕医疗器械有限公司",
      "hospital_total": 15
    },
    {
      "yj_customer_id": 4263,
      "customer_name": "湖北贝左斯商贸有限公司",
      "hospital_total": 1
    },
    {
      "yj_customer_id": 3270,
      "customer_name": "湖南长懋进出口贸易股份有限公司",
      "hospital_total": 8
    },
    {
      "yj_customer_id": 2970,
      "customer_name": "江苏曼太医疗科技有限公司",
      "hospital_total": 14
    },
    {
      "yj_customer_id": 3702,
      "customer_name": "江苏润嘉医疗器械有限公司",
      "hospital_total": 1
    },
    {
      "yj_customer_id": 4193,
      "customer_name": "江西汉优商贸有限公司",
      "hospital_total": 3
    },
    {
      "yj_customer_id": 3869,
      "customer_name": "江西赫曼医疗器械有限公司",
      "hospital_total": 6
    },
    {
      "yj_customer_id": 3738,
      "customer_name": "江西瑞晟康贸易有限公司",
      "hospital_total": 8
    }
  ],
  "dictionary": null,
  "total": 31
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|[object]|true|none||none|
|»» yj_customer_id|integer|true|none||none|
|»» customer_name|string|true|none||none|
|»» hospital_total|integer|true|none||none|
|» dictionary|null|true|none||none|
|» total|integer|true|none||none|

## POST 代理商详情

POST /control/customer/detail

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|yjCusId|query|integer| 是 |代理商的医佳系统id|

> 返回示例

> 成功

```json
{
  "code": 0,
  "msg": "success",
  "data": {
    "mainData": [
      {
        "title": "全称",
        "field": "name",
        "info": "江苏曼太医疗科技有限公司"
      },
      {
        "title": "省份",
        "field": "provinces",
        "info": ""
      },
      {
        "title": "城市",
        "field": "city",
        "info": ""
      },
      {
        "title": "发货总数",
        "field": "shipmentTotal",
        "info": 28
      },
      {
        "title": "发货总金额",
        "field": "shipmentPriceTotal",
        "info": 51672
      },
      {
        "title": "退货总数",
        "field": "returnTotal",
        "info": 5
      },
      {
        "title": "退货总金额",
        "field": "returnPriceTotal",
        "info": 10000
      }
    ],
    "productList": [
      [
        {
          "title": "医院名称",
          "field": "hospitalName",
          "info": "东莞市人民医院普济分院"
        },
        {
          "title": "植入总量",
          "field": "implantTotal",
          "info": 37
        }
      ]
    ]
  },
  "dictionary": null,
  "total": 1
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|object|true|none||none|
|»» mainData|[object]|true|none||none|
|»»» title|string|true|none||none|
|»»» field|string|true|none||none|
|»»» info|string|true|none||none|
|»» productList|[array]|true|none||none|
|»»» title|string|true|none||none|
|»»» field|string|true|none||none|
|»»» info|string|true|none||none|
|dictionary|null|true|none||none|
|total|integer|true|none||none|

## POST 微信首页提示信息

POST /control/note/index

> 返回示例

> 成功

```json
{
  "code": 0,
  "msg": "success",
  "data": "这里是首页提示信息占位字符串！",
  "dictionary": null,
  "total": 0
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||none|
|» msg|string|true|none||none|
|» data|string|true|none||none|
|» dictionary|null|true|none||none|
|» total|integer|true|none||none|

## POST 查看发票

POST /control/implant/invoice

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|implantNo|query|string| 否 |植入单号|
|num|query|integer| 否 |第几张发票|

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

# 数据模型

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc5ODU2MzIyNSwtNjQ0NjY1NjAsMTI4MD
kwNjUzNl19
-->