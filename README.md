SAAS迭代升级系统
## **web网站api文档**


[一、导航](#1)  
>   [1.1获取导航栏信息](#1.1)<br/>  
>   [1.2获取小程序分类列表信息](#1.2)  

[二、订单](#2)  
>   [2.1订单列表](#2.1)<br/>  
>   [2.2快递单表导入](#2.2)<br/>  
>   [2.3发货(物流信息)](#2.3)<br/>  
>   [2.4订单详情](#2.4)<br/>  
>   [2.5售后订单](#2.5)<br/>  
>   [2.6评价管理](#2.6)<br/>  
>   [2.7虚拟评价编辑](#2.7)<br/>  
>   [2.8虚拟评价回复](#2.8) 

[三、web用户](#3)  
>   [3.1用户注册](#3.1)<br/>    
>   [3.2用户登录](#3.2)<br/>  
>   [3.3获取用户信息](#3.3)<br/>  
>   [3.4修改用户信息](#3.4) 

[四、明细流水](#3)  
>   [4.1明细流水](#4.1)<br/>    
>   [4.2常见问题](#4.2)<br/>  
>   [4.3工单](#4.3)
 

###### **接口说明：**
<h3 id="1">**一、导航**</h3>
<h4 id="1.1">**1.1获取导航栏信息**</h4>
接口说明：
>获取小程序应用列表的首页导航
请求实例：
   GET
   [cate/index]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]
返回结果：
登录成功

```json
{
    "code": 0,
    "message": "获取导航栏信息成功",
    "data": [
        {
            "id": 1,
            "name": "移动电商",
            "sort": 1
        },
        {
            "id": 2,
            "name": "本地O2O",
            "sort": 2
        },
        {
            "id": 3,
            "name": "智慧门店",
            "sort": 3
        }
    ]
}
```
返回参数：

| 参数名       | 含义              | 参数类型   | 长度 |
| ------------ | ------------------| ---------- | ---- |
|id            | 导航栏表主键ID    | integer    |  -   |
|name          | 导航栏名称        | string     |  -   |
|sort          | 排序，越小越靠前  | integer    |  -   |



<h4 id="1.2">**1.2获取小程序分类列表信息**</h4>
接口说明：
>根据选中的导航栏获取对应的小程序分类列表
>请求参数：

| 参数名       | 含义       |           规则说明           | 参数类型    | 是否必须 | 缺省值|
| ------------ | --------   | ---------------------------- | ----------- | -------  | ----  |
| cateid       |导航栏类型ID|商户ID（配置商户信息时生成的）|  integer    | 是       | 无    |


请求实例：
   POST
   [cate/tpl]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]

 返回结果：
 成功

```json
{
    "code": 0,
    "message": "ok",
    "data": [
        {
            "id": 21,
            "tpl_name": "实时音视频",
            "logo": "",
            "desc": "自适应网络变化，智能无回声降噪处理;满足一对一、一对多的实时音视频通话场景需要"
        },
        {
            "id": 29,
            "tpl_name": "房产经纪人",
            "logo": "",
            "desc": "房地产全新拓客渠道平台;通过强关系进行高效推荐;经纪人可赚取佣金"
        }
    ]
}
```

返回参数：

| 参数名       | 含义              | 参数类型   | 长度 |
| ------------ | ------------------| ---------- | ---- |
|id            | 小程序分类ID      | integer    |  -   |
|tpl_name      | 小程序分类名称    | string     |  -   |
|logo          | 小程序类型logo    | string     |  -   |
|desc          | 小程序类型描述    | string     |  -   |




<h3 id="2">**二、订单**</h3>
<h4 id="2.1">**2.1订单列表**</h4>
接口说明：
>根据一定的条件参数获取订单列表，无参数默认获取该用户的所有订单
>请求参数：

| 参数名       | 含义    |           规则说明                                               | 参数类型    | 是否必须 | 缺省值|
| ------------ | --------| -----------------------------------------------------------------| ----------- | -------  | ----  |
| order_sn     |订单编号 |订单唯一编号                                                      |  string     | 否       | 无    |
| start_time   |开始时间 |用于查询时间范围内相应订单的开始时间                              |  string     | 否       | 无    |
| end_time     |结束时间 |用于查询时间范围内相应订单的结束时间                              |  string     | 否       | 无    |
| order_status |订单状态 |订单状态 1未付款 2待发货 3待收货 4已完成 5待处理 6已取消 7异常订单|  integer    | 否       | 无    |

请求实例：
   POST
   [order/list]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]

返回结果：
登录成功

```json
{
    "code": 0,
    "message": "获取订单列表成功",
    "data": [
        {
            "order_id": 1,
            "order_sn": "2018091102194685029",
            "money_amount": "229.00",
            "pay_amount": "178.80",
            "order_status": 1,
            "freight": 10,
            "add_time": "2018-11-29 10:15:45",
            "pay_time": "0000-00-00 00:00:00",
            "num": "7",
            "goods_name": "innisfree悦诗风吟控油矿物质散粉5g",
            "picture": ""
        },
        {
            "order_id": 2,
            "order_sn": "2018091102194685033",
            "money_amount": "229.00",
            "pay_amount": "178.80",
            "order_status": 2,
            "freight": 8,
            "add_time": "2018-11-29 10:15:45",
            "pay_time": "2018-11-29 17:21:16",
            "num": "3",
            "goods_name": "innisfree悦诗风吟控油矿物质散粉5g",
            "picture": ""
        }
    ]
}
```
返回参数：

| 参数名       | 含义                 | 参数类型   | 长度 |
| ------------ | ---------------------| ---------- | ---- |
|order_id      | 订单表主键ID         | integer    |  -   |
|order_sn      | 订单编号             | string     |  -   |
|money_amount  |付款金额(保留2位小数) | number     |  -   |
|pay_amount    |实际支付金额          | number     |  -   |
|order_status  |订单状态 1未付款 2待发货 3待收货 4已完成 5待处理 6已取消 7异常订单| number     |  -   |
|freight       |运费                  | number     |  -   |
|add_time      |下单时间              | string     |  -   |
|pay_time      |付款时间              | string     |  -   |
|num           |商品总数量            | string     |  -   |
|goods_name    |显示的第一件商品信息  | string     |  -   |
|picture       |显示的第一件商品的图片| string     |  -   |

<h4 id="2.4">**2.4订单详情**</h4>
接口说明：
>根据订单ID获取相应的订单详情
>请求参数：

| 参数名       | 含义       |           规则说明           | 参数类型    | 是否必须 | 缺省值|
| ------------ | --------   | ---------------------------- | ----------- | -------  | ----  |
| order_id     |订单ID      |订单表主键ID                  |  integer    | 是       | 无    |
请求实例：
   POST
   [order/detail]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]

返回结果：
登录成功

```json
{
    "code": 0,
    "message": "获取订单详情成功",
    "data": {
        "orderinfo": {
            "order_sn": "2018091102194685029",
            "add_time": "2018-11-29 10:15:45",
            "order_status": 1,
            "pay_method": 5,
            "money_amount": "229.00",
            "freight": 10,
            "shipping_time": "2018-11-30 13:59:19",
            "receive_time": "2018-11-30 11:30:48",
            "deduction_integral": 0,
            "get_integral": 178,
            "use_integral": 0,
            "address": "成都市武侯区领事馆路新17号鸿川大楼8楼",
            "nickname": "賢偉"
        },
        "goodsinfo": [
            {
                "goods_name": "innisfree悦诗风吟控油矿物质散粉5g",
                "act_price": "50.00",
                "total_price": 50,
                "num": 1,
                "sku": "内存:128G 版本:iphone8"
            },
            {
                "goods_name": "the SAEM得鲜丝滑遮瑕液棒",
                "act_price": "50.00",
                "total_price": 300,
                "num": 6,
                "sku": "内存:64G 版本:iphone8s"
            }
        ]
    }
}

```
返回参数：

| 参数名       | 含义                 | 参数类型   | 长度 |
| ------------ | ---------------------| ---------- | ---- |
|order_sn      |订单编号              | string     |  -   |
|add_time      |下单时间              | string     |  -   |
|order_status  |订单状态 1未付款 2待发货 3待收货 4已完成 5待处理 6已取消 7异常订单|  integer  |  -   |
|pay_method    |支付方式：1现金，2余额，3网银，4支付宝，5微信 |integer     |  -   |
|money_amount  |付款金额(保留2位小数) | number     |  -   |
|freight       |运费                  | integer    |  -   |
|shipping_time |发货时间              | string     |  -   |
|receive_time  |收货时间              | string     |  -   |
|deduction_integral |积分抵扣         | integer    |  -   |
|get_integral  |可获得积分            | integer    |  -   |
|use_integral  |积分使用              | integer    |  -   |
|address       |收货地址              | integer    |  -   |
|nickname      |用户昵称              | string     |  -   |
|goods_name    |显示的第一件商品信息  | string     |  -   |
|act_price     |此订单中该商品单价    | number     |  -   |
|total_price   |此订单中该商品价格小计| number     |  -   |
|num           |此订单中该商品总数量  | integer    |  -   |
|sku           |规格                  | string     |  -   |


<h4 id="2.5">**2.5售后订单**</h4>
接口说明：
>根据一定的条件参数获取售后订单列表，无参数默认获取该用户的所有售后订单
>请求参数：

| 参数名       | 含义    |           规则说明                                               | 参数类型    | 是否必须 | 缺省值|
| ------------ | --------| -----------------------------------------------------------------| ----------- | -------  | ----  |
| order_sn     |订单编号 |订单唯一编号                                                      |  string     | 否       | 无    |
| nickname     |用户     |用于搜索结果的小程序客户端用户微信昵称                            |  string     | 否       | 无    |
| consignee    |收货人   |用于搜索结果的收货地址对应的收货人姓名                            |  string     | 否       | 无    |
| start_time   |开始时间 |用于查询时间范围内相应订单的开始时间                              |  string     | 否       | 无    |
| end_time     |结束时间 |用于查询时间范围内相应订单的结束时间                              |  string     | 否       | 无    |
| handle_status|处理状态 |处理状态：1待处理 2已处理                                         |  integer    | 否       | 无    |
请求实例：
   POST
   [aftersale/list]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]

返回结果：

登录成功

```json
{
    "code": 0,
    "message": "获取售后订单成功",
    "data": [
        {
            "aftersale": {
                "sale_id": 1,
                "order_id": 3,
                "after_type": 2,
                "refund_amount": "50.00",
                "app_reason": "不太适合自己用",
                "status": 3,
                "app_time": "2018-12-01 17:13:14"
            },
            "orderinfo": {
                "order_sn": "2018091102194685044",
                "nickname": "小明"
            },
            "goodsinfo": {
                "goods_name": "the SAEM得鲜丝滑遮瑕液棒",
                "num": 2,
                "picture": "",
                "sku": "内存:64G 版本:iphone8s",
                "price": "28.00"
            },
            "addressinfo": {
                "consignee": "向秋婷",
                "mobile": "15882027589",
                "address": "领事馆路新17号鸿川大楼8F"
            }
        },
        {
            "aftersale": {
                "sale_id": 2,
                "order_id": 4,
                "after_type": 1,
                "refund_amount": "8.80",
                "app_reason": "质量不是太好",
                "status": 1,
                "app_time": "2018-12-01 17:13:14"
            },
            "orderinfo": {
                "order_sn": "2018091102194685045",
                "nickname": "賢偉"
            },
            "goodsinfo": {
                "goods_name": "innisfree悦诗风吟控油矿物质散粉5g",
                "num": 2,
                "picture": "",
                "sku": "颜色:黑色 版本:新版",
                "price": "32.50"
            },
            "addressinfo": {
                "consignee": "向秋婷",
                "mobile": "15882027589",
                "address": "领事馆路新17号鸿川大楼8F"
            }
        }
    ]
}
```
返回参数：

| 参数名       | 含义                 | 参数类型   | 长度 |
| ------------ | ---------------------| ---------- | ---- |
|sale_id       |售后订单表主键ID      | integer    |  -   |
|order_id      |订单表主键ID          | integer    |  -   |
|after_type    |售后类型：1退款 2换货 3退款退货|integer|  -   |
|refund_amount |退款金额              | string     |  -   |
|app_reason    |申请理由              | string     |  -   |
|status        |商家是否同意：1已经同意 2不同意 3暂未处理| integer|  -   |
|app_time      |售后申请时间          | string     |  -   |
|order_sn      |订单编号              | string     |  -   |
|nickname      |小程序端用户昵称      | string     |  -   |
|goods_name    |显示的第一件商品信息  | string     |  -   |
|num           |此订单中该商品总数量  | integer    |  -   |
|picture       |显示的第一件商品的图片| string     |  -   |
|sku           |规格                  | string     |  -   |
|price         |显示的第一件商品单价  | string     |  -   |
|consignee     |收货人姓名            | string     |  -   |
|mobile        |收货人电话            | string     |  -   |
|address       |收货人地址            | string     |  -   |

<h4 id="2.6">**2.6评价管理**</h4>
接口说明：
>新增或者根据评论ID修改相应的评价
>请求参数：

| 参数名       | 含义       |           规则说明           | 参数类型    | 是否必须 | 缺省值|
| ------------ | --------   | ---------------------------- | ----------- | -------  | ----  |
| member_id    |会员表ID    |小程序商户ID                  |  integer    | 否       | 无    |



请求实例：
   POST
   [comment/list]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]


返回结果：
评价/修改成功

```json
{
    "code": 0,
    "message": "获取评价管理列表成功过",
    "data": [
        {
            "comment_id": 1,
            "user_id": null,
            "nickname": null,
            "virtual_user": "hxq",
            "grade": "2",
            "desc": "质量很好，快递非常快wuwuwu",
            "reply": "谢谢你啦啦啦"
        },
        {
            "comment_id": 2,
            "user_id": null,
            "nickname": null,
            "virtual_user": "hxq",
            "grade": "2",
            "desc": "质量很好",
            "reply": "谢谢"
        }
    ]
}

```

返回参数：

| 参数名       | 含义                 | 参数类型   | 长度 |
| ------------ | ---------------------| ---------- | ---- |
|comment_id    |评论ID                | integer    |  -   |
|user_id       |发表评论的用户ID      | integer    |  -   |
|nickname      |用户昵称              | string     |  -   |
|virtual_user  |虚拟用户名            | string     |  -   |
|grade         |评分:0差评 1中评 2好评| integer    |  -   |
|desc          |评论内容详情          | string     |  -   |
|reply         |回复内容详情          | string     |  -   |


<h4 id="2.7">**2.7虚拟评价编辑**</h4>
接口说明：
>新增或者根据评论ID修改相应的评价
>请求参数：

| 参数名       | 含义       |           规则说明           | 参数类型    | 是否必须 | 缺省值|
| ------------ | --------   | ---------------------------- | ----------- | -------  | ----  |
| comment_id   |评论ID      |修改评价时需要提供的评论ID    |  integer    | 否       | 无    |
| virtual_user |虚拟用户名  |订单表主键ID                  |  string     | 是       | 无    |
| grade        |评分        |0差评 1中评 2好评             |  integer    | 是       | 无    |
| desc         |订单ID      |订单表主键ID                  |  integer    | 是       | 无    |
| goods_id     |商品ID      |商品表主键ID                  |  integer    | 是       | 无    |
| goods_name   |商品名称    |所评价的商品对应的商品名称    |  string     | 是       | 无    |
| user_img     |用户头像    |用户头像url地址               |  string     | 否       | 无    |
| comment_img  |评价图片    |评价图片url地址               |  string     | 否       | 无    |
| is_hidden    |是否隐藏    |0显示,1隐藏                   |  integer    | 否       | 无    |


请求实例：
   POST
   [comment/edit]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]


返回结果：
评价/修改成功

```json
{
    "code": 0,
    "message": "新增虚拟评价成功",
    "data": ""
}

```

<h4 id="2.8">**2.8虚拟评价回复**</h4>
接口说明：
>新增或者根据评论ID修改相应的评价
>请求参数：

| 参数名       | 含义       |           规则说明           | 参数类型    | 是否必须 | 缺省值|
| ------------ | --------   | ---------------------------- | ----------- | -------  | ----  |
| comment_id   |评论ID      |回复评价时需要提供的评论ID    |  integer    | 是       | 无    |
| reply        |回复内容    |回复内容                      |  string     | 是       | 无    |


请求实例：
   POST
   [comment/reply]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]


返回结果：
回复成功

```json
{
    "code": 0,
    "message": "回复成功",
    "data": ""
}
```



<h3 id="3">**三、web用户**</h3>
<h4 id="3.1">**3.1用户注册**</h4>
接口说明：
>用户注册
>请求参数：

| 参数名      | 含义    |           规则说明           | 参数类型    | 是否必须 | 缺省值|
| ------------| --------| ---------------------------- | ----------- | -------  | ----  |
| usrname     |用户帐号 |用户注册填入用于登录的帐号    |  string     | 是       | 无    |
| pwd         |用户密码 |用户注册填入的登录密码        |  string     | 是       | 无    |
请求实例：
   POST
   [user/regist]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]

返回结果：
注册成功

```json
{
  "code": 0,
  "message": "注册成功.",
  "data": []
}
```

<h4 id="3.2">**3.2用户登录**</h4>
接口说明：
>用户登录
>请求参数：

| 参数名      | 含义     |           规则说明           | 参数类型    | 是否必须 | 缺省值|
| ------------| -------- | ---------------------------- | ----------- | -------  | ----  |
| usrname     |用户帐号  |用户注册时填入的登录的帐号    |  string     | 是       | 无    |
| pwd         |用户密码  |用户注册时填入的登录密码      |  string     | 是       | 无    |
请求实例：
   POST
   [user/login]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]

返回结果：
登录成功

```json
{
  "code": 0,
  "message": "登录成功.",
  "data": [
    {
      "member_id": 3,
      "member_name": "cn181",
      "last_login_at": 1543373649,
      "last_login_ip": "127.0.0.1",
      "token": null
    }
  ]
}
```

返回参数：

| 参数名       | 含义                | 参数类型   | 长度 |
| ------------ | --------------------| ---------- | ---- |
|member_id     | 用户id号            | int        |  -   |
|member_name   | 用户帐号            | string     |  -   |
|last_login_at | 最后登录时间(时间戳)| int        |  -   |
|last_login_ip | 最后登录ip地址      | string     |  -   |
|token         | token令牌           | string     |  -   |

<h4 id="3.3">**3.3获取用户信息**</h4>
接口说明：
>获取用户基本信息
>请求参数：

| 参数名      | 含义     |           规则说明           | 参数类型    | 是否必须 | 缺省值|
| ------------| -------- | ---------------------------- | ----------- | -------  | ----  |
| token       |用户ID    |用户ID（配置商户信息时生成的）|  integer    | 是       | 无    |
| usrid       |用户帐号  |用户注册时填入的登录的帐号    |  string     | 是       | 无    |
请求实例：
   POST
   [user/info]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]

返回结果：
获取成功

```json
{
  "code": 0,
  "message": "获取数据成功.",
  "data": [
    {
      "member_id": 4,
      "member_name": "cm",
      "password": "9c05af5a0fd404bd768f",
      "head": null,
      "head_url": null,
      "name": null,
      "tel": "",
      "authority": null,
      "balance": "0.00",
      "regist_at": 1543397943,
      "expdate": null,
      "last_login_at": 1543397943,
      "last_login_ip": "127.0.0.1",
      "token": null,
      "delete_at": null
    }
  ]
}
```
返回参数：

| 参数名       | 含义              | 参数类型    | 长度 |
| ------------ | ------------------| ----------  | ---- |
|member_id     | 用户id号           | int        |  -   |
|member_name   | 用户帐号           | string     |  -   |
|password      | 用户密码            |string     |  -   |
|head          | 用户头像物里存放地址 | string   |  -   |
|head_url      | 用户头像http访问地址 | string   |  -   |
|name          | 用户姓名            | string    |  -   |
|tel           | 电话                | string    |  -   |
|authority     | 权限                | string    |  -   |
|balance       | 余额                | decimal   |  -   |
|regist_at     | 注册日期            | int       |   -  |
|expdate       | 过期日期            | int       |   -  |
|last_login_at | 最后登录时间(时间戳)| int       |  -   |
|last_login_ip | 最后登录ip地址      | string    |  -   |
|token         | token令牌          | string     |  -   |
|delete_at     | 删除标记,非空为删除 |  int      | -    |


<h4 id="3.4">**3.4修改用户信息**</h4>
接口说明：
>修改用户基本信息
>请求参数：

| 参数名      | 含义    |           规则说明            | 参数类型    | 是否必须 | 缺省值|
| ------------| -------- | ---------------------------- | ----------- | -------  | ----  |
| token       |用户ID    |用户ID（配置商户信息时生成的）|  integer    | 是       | 无    |
| usrid       |用户帐号  |用户注册时填入的登录的帐号    |  string     | 是       | 无    |
| pwd         |用户密码  |用户注册时填入的登录的帐号    |  string     | 否       | 无    |
| usrname     |用户姓名  |用户姓名                      |  string     | 否       | 无    |
| phone       |联系方式  |用户联系方式                  |  string     | 否       | 无    |
请求实例：
   POST
   [user/updUsrInfo]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]

返回结果：
操作成功

```json
{
  "code": 0,
  "message": "操作成功.",
  "data": []
}
```


<h3 id="4">**二、明细流水**</h3>
<h4 id="4.1">**4.1明细流水**</h4>
接口说明：
>分页查询明细流水列表
>请求参数：

| 参数名       | 含义    |           规则说明                                               | 参数类型    | 是否必须 | 缺省值|
| ------------ | --------| -----------------------------------------------------------------| ----------- | -------  | ----  |
| start_time   |开始时间 |用于查询时间范围内明细流水的开始时间                              |  string     | 否       | 无    |
| end_time     |结束时间 |用于查询时间范围内明细流水的结束时间                              |  string     | 否       | 无    |
| keyword      |关键字   |用于搜索的关键字                                                  |  string     | 否       | 无    |
| per_page     |显示条数 |每页显示的条数                                                    |  integer    | 否       | 10    |
| cur_page     |当前页   |当前是第几页                                                      |  integer    | 否       | 1     |

请求实例：
   POST
   [subwater/list]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]

返回结果：
登录成功

```json
{
    "code": 0,
    "message": "获取明细流水成功",
    "data": [
        {
            "water_id": 1,
            "num": 3,
            "desc": "小程序：ddd（uniacid:8846）关联【微商城】模块",
            "create_at": "2018-12-03 08:17:44"
        },
        {
            "water_id": 2,
            "num": 5,
            "desc": "\t\r\n小程序：test（uniacid:8842）关联【微商城（多商户）】模块",
            "create_at": "2018-12-04 10:18:06"
        }
    ]
}

```
返回参数：

| 参数名       | 含义              | 参数类型    | 长度 |
| ------------ | ------------------| ----------  | ---- |
|water_id      | 明细流水表主键    | int         |  -   |
|num           | 数额              | int         |  -   |
|desc          | 描述              | string      |  -   |
|create_at     | 时间              | string      |  -   |



<h4 id="4.2">**4.2常见问题**</h4>
接口说明：
>分页查询常见问题列表
>请求参数：

| 参数名       | 含义    |           规则说明                                               | 参数类型    | 是否必须 | 缺省值|
| ------------ | --------| -----------------------------------------------------------------| ----------- | -------  | ----  |
| start_time   |开始时间 |用于查询时间范围内明细流水的开始时间                              |  string     | 否       | 无    |
| end_time     |结束时间 |用于查询时间范围内明细流水的结束时间                              |  string     | 否       | 无    |
| keyword      |关键字   |用于搜索的关键字                                                  |  string     | 否       | 无    |
| per_page     |显示条数 |每页显示的条数                                                    |  integer    | 否       | 10    |
| cur_page     |当前页   |当前是第几页                                                      |  integer    | 否       | 1    |

请求实例：
   POST
   [question/list]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]
   
   返回结果：
   获取常见问题列表成功

   ```json
   {
    "code": 0,
    "message": "获取常见问题列表成功",
    "data": [
        {
            "fre_id": 3,
            "title": "小程序复用公众号资质快速认证2",
            "read_num": 102,
            "source": "新浪",
            "author": "test",
            "content": "小程序已创建成功但未开通微信认证，但已跟公众号关联，可以复用公众号微信认证资质。快速认证不需要重新提交认证资质，不需要支付300元支付费用，即时生效。小程序的认证截止日期与公众号认证截止日期一致，到期后，请开发者重新年审或再次复用资质认证。 条件： 1.可快速认证的小程序：企业、媒体、政府和其他组织类型的小程序； 2.要求公众号必须先完成微信认证； 3.公众号与小程序关联，且主体相同。 申请入口：",
            "create_at": "2018-12-04 14:59:34",
            "type_name": "微商城"
        },
        {
            "fre_id": 4,
            "title": "小程序复用公众号资质快速认证3",
            "read_num": 102,
            "source": "新浪",
            "author": "test1",
            "content": "小程序已创建成功但未开通微信认证，但已跟公众号关联，可以复用公众号微信认证资质。快速认证不需要重新提交认证资质，不需要支付300元支付费用，即时生效。小程序的认证截止日期与公众号认证截止日期一致，到期后，请开发者重新年审或再次复用资质认证。 条件： 1.可快速认证的小程序：企业、媒体、政府和其他组织类型的小程序； 2.要求公众号必须先完成微信认证； 3.公众号与小程序关联，且主体相同。 申请入口：",
            "create_at": "2018-12-03 14:59:34",
            "type_name": "小程序开通"
        }
    ]
}

```
返回参数：

| 参数名       | 含义              | 参数类型    | 长度 |
| ------------ | ------------------| ----------  | ---- |
|fre_id        | 常见问题表主键ID  | int         |  -   |
|title         | 标题              | string      |  -   |
|read_num      | 阅读次数          | int         |  -   |
|source        | 来源              | string      |  -   |
|author        | 作者              | string      |  -   |
|content       | 内容              | string      |  -   |
|create_at     | 添加时间          | string      |  -   |
|type_name     | 所属常用问题类型  | string      |  -   |


<h4 id="4.3">**4.3工单**</h4>
接口说明：
>分页查询常见问题列表
>请求参数：

| 参数名       | 含义    |           规则说明                                               | 参数类型    | 是否必须 | 缺省值|
| ------------ | --------| -----------------------------------------------------------------| ----------- | -------  | ----  |
| start_time   |开始时间 |用于查询时间范围内明细流水的开始时间                              |  string     | 否       | 无    |
| end_time     |结束时间 |用于查询时间范围内明细流水的结束时间                              |  string     | 否       | 无    |
| keyword      |关键字   |用于搜索的关键字                                                  |  string     | 否       | 无    |
| per_page     |显示条数 |每页显示的条数                                                    |  integer    | 否       | 10    |
| cur_page     |当前页   |当前是第几页                                                      |  integer    | 否       | 1    |

请求实例：
   POST
   [workorder/list]()
   HTTP/1.1 Host: [http://web.server.com:8080/api/]
   
   返回结果：
   获取常见问题列表成功

   ```json
   
  {
    "code": 0,
    "message": "获取工单列表成功",
    "data": [
        {
            "work_id": 1,
            "work_sn": "201811202351336442",
            "fre_id": 2,
            "desc": "\t\r\n不知道怎么设置首页客服图标",
            "secret": null,
            "phone": "18508236982",
            "company": "忆享",
            "commit_at": "2018-12-04 14:52:06",
            "status": 0,
            "type_name": "小程序开通",
            "member_name": "lj"
        },
        {
            "work_id": 2,
            "work_sn": "201811202351036442",
            "fre_id": 3,
            "desc": "设置内页样式的问题",
            "secret": null,
            "phone": "18508236981",
            "company": "忆享",
            "commit_at": "2018-12-05 10:52:13",
            "status": 1,
            "type_name": "微商城",
            "member_name": "lj"
        }
    ]
  }


  ```
返回参数：

| 参数名       | 含义              | 参数类型   | 长度 |
| ------------ | ------------------| ---------- | ---- |
|work_id       | 常见问题表主键ID  | int        |  -   |
|work_sn       | 工单编号          | string     |  -   |
|fre_id        | 常见问题表主键ID  | int        |  -   |
|desc          | 问题描述          | int        |  -   |
|secret        | 机密信息          | string     |  -   |
|phone         | 手机号码          | string     |  -   |
|company       | 提交单位          | string     |  -   |
|commit_at     | 提交时间          | string     |  -   |
|status        |工单状态 工单状态0待处理 1已结单| int  |  -  |
|type_name     | 问题分类名称     | string      |  -   |
|member_name   | 提交用户         | string      |  -   |