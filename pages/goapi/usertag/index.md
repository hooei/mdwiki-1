#费睿 usertag API 文档  V1.0

## API 调用示例
* 1.1 [添加用户标签](index.md#1.1_添加用户标签)
* 1.2 [获取总人数和次数](index.md#1.2_获取总人数和次数)
* 1.3 [按标签分组获取总人数和次数](index.md#1.3_按标签分组获取总人数和次数)
* 1.4 [按指定标签获取总人数和次数](index.md#1.4_按指定标签获取总人数和次数)
* 1.5 [统计指定标签分组的所有标签次数](index.md#1.5_统计指定标签分组的所有标签次数)
* 1.6 [获取所有标签](index.md#1.6_获取所有标签)
* 1.7 [获取标签分组](index.md#1.7_获取标签分组)
* 1.8 [检索指定标签](index.md#1.8_检索指定标签)
* 1.9 [创建详细报告](index.md#1.9_创建详细报告)

###1.1 添加用户标签

####接口说明
添加用户标签

| URL      | http://hiproapi.verystar.cn/user_tag/add_user_tag |
| :------- | :---- |
| Request 方法 | POST |
| Return 格式 | json |

####请求 Url 参数

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| authcode | 是 | string |  签名值, 详情见 [签名示例](../introduce/index.md#签名示例) |

####请求参数(POST)

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| client_code | 是 | string | `client_code`作为公钥用于验证用户ID |
| req_time | 是 | int | 请求时的时间戳 |
| open_id | 是 | string | 用户openid |
| tag_val | 是 | string | tag值 |

####返回值
```json
{
    "retcode": 200,
    "data": nil,
    "msg": nil
}
```

####返回值状态说明

| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| retcode | int | 200 | 请求成功 |
| data |   | nil | 默认值为nil |
| msg | string | nil | 错误描述,nil表示增加成功 |

###1.2 获取总人数和次数

####接口说明
按天或截至目前为止获取该商户下所有的打标签的人数或打标签的次数 

| URL      | http://hiproapi.verystar.cn/user_tag/get_daily_summary |
| :------- | :---- |
| Request 方法 | POST |
| Return 格式 | json |

####请求 Url 参数

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| authcode | 是 | string |  签名值, 详情见 [签名示例](../introduce/index.md#签名示例) |

####请求参数(POST)

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| client_code | 是 | string | `client_code`作为公钥用于验证用户ID |
| req_time | 是 | int | 请求时的时间戳 |
| query_type | 是 | string | 查询类型  |
| start_date | 是 | string | 查询开始日期 |
| end_date   | 是 | string | 查询截至日期 |

####返回值
```json
{
	"data":{
		"2016-04-24":"3139856",
		"2016-04-25":"3211541",
		"2016-04-26":"3320382"
	},
	"msg":null,
	"retcode":200
}
```

####返回值状态说明

| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| retcode | int | 200 | 请求成功 |
| data | json |  | 返回值结构 |
| msg | string | nil | 错误描述,nil表示增加成功 |

####返回值结构说明
| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| date  | string | | 打标签的日期 |
| count | string | | （按查询类型返回的）打标签的人数或打标签的次数 |

###1.3 按标签分组获取总人数和次数

####接口说明
按天或截至目前为止获取该商户下按标签分组的所有打标签的人数或打标签的次数 

| URL      | http://hiproapi.verystar.cn/user_tag/get_group_daily_summary |
| :------- | :---- |
| Request 方法 | POST |
| Return 格式 | json |

####请求 Url 参数

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| authcode | 是 | string |  签名值, 详情见 [签名示例](../introduce/index.md#签名示例) |

####请求参数(POST)

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| client_code | 是 | string | `client_code`作为公钥用于验证用户ID |
| req_time | 是 | int | 请求时的时间戳 |
| group_name | 是 | string | 标签分组名称 |
| query_type | 是 | string | 查询类型  |
| start_date | 是 | string | 查询开始日期 |
| end_date   | 是 | string | 查询截至日期 |

####返回值
```json
{
   "data":{
   		"Brand":{
   				"2016-04-25":"3136",
   				"2016-04-26":"2605"
   		},
   		"DP":{
   				"2016-04-25":"21",
   				"2016-04-26":"20"
   		},
   		"DP关注":{
   				"2016-04-25":"85",
   				"2016-04-26":"86"
   		},
   		"Lifestyle":{
   				"2016-04-25":"324",
   				"2016-04-26":"276"
   		},
   		"门店关注":{
  				"2016-04-25":"431",
  				"2016-04-26":"371"
   		}
   },
   "msg":null,
   "retcode":200
}
```

####返回值状态说明

| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| retcode | int | 200 | 请求成功 |
| data |  json |   | 返回值结构 |
| msg | string | nil | 错误描述,nil表示增加成功 |

####返回值结构说明
| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| group_name | 是 |  json | 标签组名 |

####group_name结构说明
| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| date  | string | | 打标签的日期 |
| count | string | | （按查询类型返回的）打标签的人数或打标签的次数 |

###1.4 按指定标签获取总人数和次数

####接口说明
按天或截至目前为止获取该商户下指定标签的打标签的人数或打标签的次数

| URL      | http://hiproapi.verystar.cn/user_tag/get_tag_daily_summary |
| :------- | :---- |
| Request 方法 | POST |
| Return 格式 | json |

####请求 Url 参数

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| authcode | 是 | string |  签名值, 详情见 [签名示例](../introduce/index.md#签名示例) |

####请求参数(POST)

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| client_code | 是 | string | `client_code`作为公钥用于验证用户ID |
| req_time | 是 | int | 请求时的时间戳 |
| tag_name | 是 | string | 指定的标签名称  |　
| query_type | 是 | string | 查询类型  |
| start_date | 是 | string | 查询开始日期 |
| end_date   | 是 | string | 查询截至日期 |

####返回值
```json
{
    "data": {
        "15 FW-外套": {
            "2016-04-25": "1"
        },
        "15 FW-外套关注": {
            "2016-04-25": "1",
            "2016-04-27": "1"
        },
        "15FW-DP": {
            "2016-04-25": "17",
            "2016-04-26": "18",
            "2016-04-27": "29"
        }
    },
    "msg": null,
    "retcode": 200
}
```

####返回值状态说明

| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| retcode | int | 200 | 请求成功 |
| data |  json |   | data结构 |
| msg | string | nil | 错误描述,nil表示增加成功 |

####data结构说明

| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| tag_name | json | 15FW-DP | 标签名称     |


####tag_name结构说明
| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| date  | string | | 打标签的日期 |
| count | string | | （按查询类型返回的）打标签的人数或打标签的次数 |

###1.5 统计指定标签分组的所有标签次数

####接口说明
统计指定标签分组的所有标签次数

| URL      | http://hiproapi.verystar.cn/user_tag/get_tag_daily_summary_by_group |
| :------- | :---- |
| Request 方法 | POST |
| Return 格式 | json |

####请求 Url 参数

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| authcode | 是 | string |  签名值, 详情见 [签名示例](../introduce/index.md#签名示例) |

####请求参数(POST)

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| client_code | 是 | string | `client_code`作为公钥用于验证用户ID |
| req_time | 是 | int | 请求时的时间戳 |
| group_name | 是 | string | 标签分组名称 |
| query_type | 是 | string | 查询类型  |
| start_date | 是 | string | 查询开始日期 |
| end_date   | 是 | string | 查询截至日期 |

####返回值
```json
{
    "data": {
        "15 FW-外套": {
            "2016-04-25": "3",
            "2016-04-26": "3"
        },
        "15FW-DP": {
            "2016-04-25": "542",
            "2016-04-26": "560"
        },
        "15FW-牛仔": {
            "2016-04-25": "7",
            "2016-04-26": "7"
        },
        "15SS-AIRism（女）": {
            "2016-04-25": "2",
            "2016-04-26": "2"
        },
        "15SS-家居服（男）": {
            "2016-04-25": "2",
            "2016-04-26": "2"
        }
    },
    "msg": null,
    "retcode": 200
}
```

####返回值状态说明

| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| retcode | int | 200 | 请求成功 |
| data |  json | nil | data 结构 |
| msg | string | nil | 错误描述,nil表示增加成功 |

####data结构说明

| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| tag_name | json | 15FW-DP | 标签名称     |

####tag_name结构说明
| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| date  | string | | 打标签的日期 |
| count | string | | （按查询类型返回的）打标签的人数或打标签的次数 |

###1.6 获取所有标签

####接口说明
获取所有标签

| URL      | http://hiproapi.verystar.cn/user_tag/get_tags |
| :------- | :---- |
| Request 方法 | POST |
| Return 格式 | json |

####请求 Url 参数

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| authcode | 是 | string |  签名值, 详情见 [签名示例](../introduce/index.md#签名示例) |

####请求参数(POST)

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| client_code | 是 | string | `client_code`作为公钥用于验证用户ID |
| req_time | 是 | int | 请求时的时间戳 |
| cur_page | 是 | string | 指定查询的页码 |
| limit | 是 | string  | 查询条数 |
| group_id | 否 | string | 标签分组 ID | 

####返回值
```json
{
    "data": [
        "16SS-UT",
        "搭配时尚",
        "16SS-POLO",
        "搭配时尚",
        "功能控",
        "16SS-BRATOP",
        "16SS-KAWS",
        "16SS-UT",
        "搭配时尚",
        "搭配时尚"
    ],
    "msg": null,
    "retcode": 200
}
```

####返回值状态说明

| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| retcode | int | 200 | 请求成功 |
| data |  数组 | nil | 标签数组,数组值为标签名称 |
| msg | string | nil | 错误描述,nil表示增加成功 |


###1.7 获取标签分组

####接口说明
获取标签分组

| URL      | http://hiproapi.verystar.cn/user_tag/get_groups |
| :------- | :---- |
| Request 方法 | POST |
| Return 格式 | json |

####请求 Url 参数

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| authcode | 是 | string |  签名值, 详情见 [签名示例](../introduce/index.md#签名示例) |

####请求参数(POST)

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| client_code | 是 | string | `client_code`作为公钥用于验证用户ID |
| req_time | 是 | int | 请求时的时间戳 |
| cur_page | 是 | string | 指定查询的页码 |
| limit    | 是 | string  | 查询条数 |

####返回值
```json
{
    "data": [
        {
            "group_id": "18",
            "group_name": "DP关注"
        },
        {
            "group_id": "17",
            "group_name": "粉丝价值"
        },
        {
            "group_id": "8",
            "group_name": "取消收藏品类"
        }
    ],
    "msg": null,
    "retcode": 200
}
```

####返回值状态说明

| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| retcode | int | 200 | 请求成功 |
| data | 数组  |   | data数组 |
| msg | string | nil | 错误描述,nil表示增加成功 |

####data数组结构说明

| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
|group_id| string || 标签分组id|
|group_name| string || 标签分组名称 |

###1.1 检索指定标签

####接口说明
检索指定标签

| URL      | http://hiproapi.verystar.cn/user_tag/search_tag |
| :------- | :---- |
| Request 方法 | POST |
| Return 格式 | json |

####请求 Url 参数

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| authcode | 是 | string |  签名值, 详情见 [签名示例](../introduce/index.md#签名示例) |

####请求参数(POST)

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| client_code | 是 | string | `client_code`作为公钥用于验证用户ID |
| req_time | 是 | int | 请求时的时间戳 |
| tag_name | 是 | string | 待检索的标签名称  | 
| cur_page | 是 | string | 指定查询的页码 |
| limit    | 是 | string  | 查询条数 |

####返回值
```json
{
    "data": [
        "16SS-UT",
        "16SS-UT",
        "16SS-UT",
        "16SS-UT",
        "16SS-UT",
        "16SS-UT",
    ],
    "msg": null,
    "retcode": 200
}
```

####返回值状态说明

| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| retcode | int | 200 | 请求成功 |
| data |  数组 | nil | 标签数组,数组值为标签名称 |
| msg | string | nil | 错误描述,nil表示增加成功 |

###1.9 创建详细报告

####接口说明
创建详细报告

| URL      | http://hiproapi.verystar.cn/user_tag/create_detail_report |
| :------- | :---- |
| Request 方法 | POST |
| Return 格式 | json |

####请求 Url 参数

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| authcode | 是 | string |  签名值, 详情见 [签名示例](../introduce/index.md#签名示例) |

####请求参数(POST)

| 名称 | 是否必须 | 类型 | 描述 |
| :-------- | :--------:| :------ | :------ |
| client_code | 是 | string | `client_code`作为公钥用于验证用户ID |
| req_time | 是 | int | 请求时的时间戳 |
| task_name| 是 | string | 任务名称 |
| tag_names| 是 | string | 标签名称 [注解1](index.md#_注解1)|
| report_type | 是 | string | 报告类型 [注解2](index.md#_注解2)|
| start_date | 是 | string | 查询开始日期 |
| end_date   | 是 | string | 查询截至日期 |
| callback_url | 是 | string | 回调uri | 

####返回值
```json
{
    "retcode": 200,
    "data": nil,
    "msg": nil
}
```

####返回值状态说明

| 名称 | 类型 | 值  | 描述 |
| :-------- | :------ | :------ | :------ |
| retcode | int | 200 | 请求成功 |
| data |   | nil | 默认值为nil |
| msg | string | nil | 错误描述,nil表示增加成功 |

[错误码列表]

## 错误代码一览表

###错误代码列表

| 错误码      | 错误描述 |
| :------- | :---- |
|101 | 请求时间非法 |
|102 | 请求参数不足 |
|103 | authcode验证失败 | 
|104 | 非法client_code | 
|105 | client_code已被关闭 |
|106 | 没有授权访问本接口 |
|107 | 没有授权访问本接口 |
|108 | 非法 client_code |
|109 | authcode 非法 |


#### 注解1: 
> 
tag_names json 格式； 比如有 `16SS-UT` 和 `搭配时尚` 两个tag_name 
tag_names  = "[\"16SS-UT\",\"搭配时尚\"]",

#### 注解2:
> 
report_type 可选值为1, 2 或 3。 