## 接口出入参详情
### 1.查看详情页

[请求地址]: http://localhost:3000/appDatails?id=1

| 名称     | 说明 | 备注   |
| -------- | ---- | ------ |
| 请求方式 | get  |        |
| 参数     | id   | 商品id |

返回参数

| 字段  | 说明            | 类型 |
| ----- | --------------- | ---- |
| sku   | sku商品数据结构 |      |
| param | 商品详情页数据  |      |

```
        title: select[0].p_title,     //标题
        stock: select[0].stock,   //库存
        sales: select[0].sales,   //销量
        describes: select[0].describes,   //销量
        is_put: select[0].is_put, //评论
        price: select[0].price, //商品的原价
        vip_price: select[0].vip_price //商品降价之后的价格
```

### 2.查询购物车

[请求地址]: http://localhost:3000/getShopping?userId=123456789

| 名称     | 说明   | 类型 |
| -------- | ------ | ---- |
| 请求方式 | get    |      |
| 参数     | userId |      |

返回参数

```
{
    "code": 0,
    "msg": "请求成功",
    "payload": [
        {
            "product_id": 1,					//商品id
            "p_name": "卫衣",					  //商品名称
            "p_title": "男士帅气卫衣",			//商品标题
            "describes": "这是一条卫衣",			//商品描述
            "diss_num": 22,						//商品评论条数
            "sku_id": 1,						//商品的skuId
            "color_id": 1,						//商品颜色id
            "size_id": 3,						//商品尺寸id
            "vip_price": 30,					//商品价格
            "stock": 50,						//商品库存
            "num": 20,							//商品购买数量
            "color": "红色",						//商品颜色
            "img": "1.img",						//商品图片
            "name": "XL"						//商品尺寸名称
        },
      ]
  }
```

### 3.添加、修改到购物车

[请求地址]: http://localhost:3000/setShopping

| 名称           | 说明                | 类型 |
| -------------- | ------------------- | ---- |
| 请求方式       | psot                |      |
| 参数           |                     |      |
| userId         | 用户id，在cookies里 |      |
| skuId          | 商品skuid           |      |
| procuctId      | 商品id              |      |
| shoppingNumber | 购买的数量          |      |

后面可能补充colorId和sizeId

### 4.删除购物车

[请求地址]: http://localhost:3000/deleteShopping?userId=123&amp;amp;amp;amp;amp;amp;amp;amp;skuId=1

| 名称     | 说明                | 类型 |
| -------- | ------------------- | ---- |
| 请求方式 | get                 |      |
| 参数     |                     |      |
| userId   | 用户id，在cookies里 |      |
| skuId    | 商品skuid           |      |

### 5.添加订单

[请求地址]: http://localhost:3000/setOrder

| 名称        | 说明                                        | 类型      |
| ----------- | ------------------------------------------- | --------- |
| 请求方式    | post                                        |           |
| o_num       | 订单生成方式： 1（app生成） ，2（后台生成） | string    |
| p_id        | 商品id                                      | int       |
| p_num       | 商品数量                                    | int       |
| u_id        | 用户id                                      | int       |
| phone       | 手机号                                      | string    |
| adderss     | 收货地址                                    | string    |
| order_time  | 下单时间，格式：2020-05-08                  | timestamp |
| order_way   | 支付方式 1 微信 2支付宝 3银行卡             | int       |
| pay_time    | 支付时间，格式：2020-05-08                  | timestamp |
| total       | 商品总额                                    | double    |
| pay_total   | 实际支付                                    | double    |
| remark      | 备注                                        | string    |
| validstatus | 订单状态 0待付款 1已付款 2待收取 3已完成    | string    |
| is_delete   | 是否有效 1有效 0无效                        | int       |
| 补充        |                                             |           |
| s_id        | 商品skuid                                   | int       |

### 6.查询订单

[请求地址]: http://localhost:3000/getOrder?userId=17

| 名称     | 说明   | 类型 |
| -------- | ------ | ---- |
| 请求方式 | get    |      |
| 参数     |        |      |
| userId   | 用户id | int  |

返回参数，同添加订单需要的参数

```
{
"o_id": 1111111112,				
"o_num": "1",					
"p_id": 1,
"p_num": 10,
"u_id": 17,
"phone": "18777718237",
"adderss": "广州海珠",
"order_time": "2020-05-07T16:00:00.000Z",
"order_way": 1,
"pay_time": "2020-05-07T16:00:00.000Z",
"total": 998,
"pay_total": 1000,
"remark": "",
"validstatus": 1,
"is_delete": 1
},
```
