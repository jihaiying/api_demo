# Fang88 API 开发文档

```

```

## 房源列表

### 获取二手房总数

#### 简要描述
* 获取指定条件的二手房的房源总数

#### 请求URL
* /api/home/get_total_count

##### 请求方式
* POST

##### 参数 

| 参数名 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| current_list_price_filter_on | 否 | boolean | 是否过滤价格，默认false | 
| current_list_price_filter_max | 否 | integer | 最高价格 | 
| current_list_price_filter_min | 否 | integer | 最低价格 | 
| sqft_filter_on | 否 | boolean | 是否过滤房屋面积，默认false | 
| sqft_filter_min | 否 | integer | 最小面积 | 
| sqft_filter_max | 否 | integer | 最大面积 | 
| bedrooms_filter_on | 否 | boolean | 是否过滤卧室数，默认false | 
| bedrooms_filter_min | 否 | integer | 最小卧室数 | 
| bedrooms_filter_max | 否 | integer 最大卧室数 | 
| bathrooms_filter_on | 否 | boolean | 是否过滤浴室数，默认false | 
| bathrooms_filter_min | 否 | integer | 最小浴室数 | 
| bathrooms_filter_max | 否 | integer | 最大浴室数 | 
| year_built_filter_on | 否 | boolean | 是否过滤建筑年份，默认false | 
| year_built_filter_min | 否 | integer | 最小建筑年份 | 
| year_built_filter_max | 否 | integer | 最大建筑年份 | 
| roi_filter_on | 否 | boolean | 是否过滤投资回报率，默认false | 
| roi_filter_min | 否 | float | 最低回报率 | 
| location_rect_filter_on | 否 | boolean | 是否过滤地理位置，默认false | 
| location_rect_filter_type | 否 | string | 地理过滤方式, 如果用最大最小经纬度过滤，传”min_max_degrees” | 
| latitude_min | 否 | float | 最小纬度 | 
| latitude_max | 否 | float | 最大纬度 | 
| longitude_min | 否 | float | 最小经度 | 
| longitude_max | 否 | float | 最大经度 | 
| property_type_candidate_array_on | 否 | boolean | 是否过滤房产类型，默认false | 
| property_type_candidate_array | 否 | array | 房产类型数组:独栋别墅对应RESI,联排别墅对应COND,公寓对应APT,多户住宅对应MULT | 
| status_candidate_array_on | 否 | boolean | 是否过滤状态，默认true}
| status_candidate_array | 否 | array | 房产状态数组:在售对应A,已售S,成交中P,默认["A"] | 
| area_candidate_array_on | 否 | boolean | 是否开启按城市圈数据筛选，默认false | 
| area_candidate_array | 否 | array | 城市圈 数组 | 
| city_candidate_array_on | 否 | boolean | 是否过滤城市，默认false | 
| city_candidate_array | 否 | array | 城市数组 | 
| zip_candidate_array_on | 否 | boolean | 是否过滤邮编，默认false | 
| zip_candidate_array | 否 | array | 邮编数组 | 
| page_size | 否 | integer | 每页显示数量，默认1000 | 
| page_number | 否 | integer | 第几页，默认1 | 

#### 请求示例
```
{
 "property_type_candidate_array_on": true,
 "property_type_candidate_array": ["RESI", "COND"]
}

```

#### 返回示例
```
{
 "total_count": "114788"
}
```

##### 返回参数说明
| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| total_count | integer | 总数 |

##### 抛出异常
* 无

--- 

### 获取二手房列表

#### 简要描述
* 获取指定条件的二手房的房源列表

#### 请求URL
* /api/home/get_homes_list

##### 请求方式
* POST

##### 参数
| 参数名 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| current_list_price_filter_on | 否 | boolean | 是否过滤价格默认false |
| current_list_price_filter_max | 否 | integer | 最高价格 |
| current_list_price_filter_min | 否 | integer | 最低价格 |
| sqft_filter_on | 否 | boolean | 是否过滤房屋面积默认false |
| sqft_filter_min | 否 | integer | 最小面积 |
| sqft_filter_max | 否 | integer | 最大面积 |
| bedrooms_filter_on | 否 | boolean | 是否过滤卧室数默认false |
| bedrooms_filter_min | 否 | integer | 最小卧室数 |
| bedrooms_filter_max | 否 | integer | 最大卧室数 |
| bathrooms_filter_on | 否 | boolean | 是否过滤浴室数默认false |
| bathrooms_filter_min | 否 | integer | 最小浴室数 |
| bathrooms_filter_max | 否 | integer | 最大浴室数 |
| year_built_filter_on | 否 | boolean | 是否过滤建筑年份默认false |
| year_built_filter_min | 否 | integer | 最小建筑年份 |
| year_built_filter_max | 否 | integer | 最大建筑年份 |
| roi_filter_on | 否 | boolean | 是否过滤投资回报率默认false |
| roi_filter_min | 否 | float | 最低回报率 |
| decoded | 否 | boolean | 是否返回解密数据 |
| location_rect_filter_on | 否 | boolean | 是否过滤地理位置默认false |
| location_rect_filter_type | 否 | string | 地理过滤方式, | 如果用最大最小经纬度过滤传”min_max_degrees” |
| latitude_min | 否 | float | 最小纬度 |
| latitude_max | 否 | float | 最大纬度 |
| longitude_min | 否 | float | 最小经度 |
| longitude_max | 否 | float | 最大经度 |
| property_type_candidate_array_on | 否 | boolean | 是否过滤房产类型默认false |
| property_type_candidate_array | 否 | array | 房产类型数组:独栋别墅对应RESI,联排别墅对应COND,公寓对应APT,多户住宅对应MULT |
| status_candidate_array_on | 否 | boolean | 是否过滤状态默认true |
| status_candidate_array | 否 | array | 房产状态数组:在售对应A,已售S,成交中P,默认["A"] |
| area_candidate_array_on | 否 | boolean | 是否开启按城市圈数据筛选默认false |
| area_candidate_array | 否 | array | 城市圈 | 数组 |
| city_candidate_array_on | 否 | boolean | 是否过滤城市默认false |
| city_candidate_array | 否 | array | 城市数组 |
| zip_candidate_array_on | 否 | boolean | 是否过滤邮编默认false |
| zip_candidate_array | 否 | array | 邮编数组 |
| updated_at_orderBy_on | 否 | boolean | 是否按照过滤时间排序默认true |
| updated_at_orderBy_order | 否 | string | "DESC"或者"ASC" |
| recommend_orderBy_on | 否 | boolean | 是否按照推荐顺序排序默认false |
| recommend_orderBy_order | 否 | string | "DESC"或者"ASC" |
| roi_orderBy_on | 否 | boolean | 是否按照投资回报率排序默认false |
| roi_orderBy_order | 否 | string | "DESC"或者"ASC" |
| page_size | 否 | integer | 每页显示数量默认18 |
| page_number | 否 | integer | 第几页默认1 | 

#### 请求示例
```
{
  "property_type_candidate_array_on": true,
  "property_type_candidate_array": [
    "RESI",
    "COND"
  ],
  "decoded": true,
  "page_size": 3,
  "page_number": 1
}

```

#### 返回示例
```
[
  {
    "area": "\u65e7\u91d1\u5c71\u57ce\u5e02\u5708",
    "address": "681 Bayview Dr",
    "fav_users_num": 0,
    "bathrooms": "2.00",
    "bedrooms": "3.0",
    "city": "Aptos",
    "current_list_price": 1188000,
    "estimated_monthly_rent": 3449,
    "estimated_yearly_return": "0.0444959",
    "id": 11555558,
    "location_latitude": "36.9600892",
    "location_longitude": "-121.8890695",
    "openhouses": [
      {
        "start_time": "2017-07-09T14:00:00+0800",
        "end_time": "2017-07-09T16:00:00+0800"
      },
      {
        "start_time": "2017-07-08T14:00:00+0800",
        "end_time": "2017-07-08T16:00:00+0800"
      }
    ],
    "photo_json": "[{\"path\":\"d5665aa6ad38fd0bcba1c4128f41106b.jpg\"},{\"path\":\"a546455201b62d83dcd854b5701b744d.jpg\"},{\"path\":\"a76ad030f875e5eb2db653a8fa577db1.jpg\"},{\"path\":\"11bed7adbe57e32b8c9f78b5bd069323.jpg\"},{\"path\":\"f66df44a7b332552f2ca4521a5085a83.jpg\"},{\"path\":\"15b4706b1f357cf468e406d6a451bf54.jpg\"},{\"path\":\"bf00ceb26d5917f37ee5c214067c36ad.jpg\"},{\"path\":\"9b3b072d7ec9cccd3c3f64e0f1dc12c8.jpg\"},{\"path\":\"3b2280eb6acfc3a7666bea959f85cba5.jpg\"},{\"path\":\"0b941819e047175773fcf368af3aa8fd.jpg\"},{\"path\":\"71763977070bc42259b0ec7355916d81.jpg\"},{\"path\":\"e1f1a86410b823405a1ebac02f52fc23.jpg\"},{\"path\":\"2a3be72bd3eaa4cd4a668daf3e8738c6.jpg\"},{\"path\":\"990e18620ffedbf3d3fe2b95c8f4d5e5.jpg\"},{\"path\":\"1121c94521382c28d017d154ade936ea.jpg\"},{\"path\":\"e081d9b88a3b21b053cb149ed107d20d.jpg\"},{\"path\":\"c3cf9f6bf06279bb6b31b87c324fb20f.jpg\"},{\"path\":\"6f6f9dc13b23e8a873f05204d2627d89.jpg\"},{\"path\":\"2050cdaa979622ea0c4a10a70bfe6244.jpg\"},{\"path\":\"7a8c5c909a46dc7152dac3615fd2f693.jpg\"},{\"path\":\"0882137bf1f3e060809862d116b3fe3c.jpg\"},{\"path\":\"109a8be626d779847fc3f14f7af3453f.jpg\"},{\"path\":\"3331548a6892c006a1b9a93ce4a262b6.jpg\"},{\"path\":\"9b5249bd63b571fff1a95ba0aaa3d516.jpg\"},{\"path\":\"8bbb4f139d1235800a4fbc8c73854744.jpg\"},{\"path\":\"6b1e2059a60a3937369c9745840f99e9.jpg\"},{\"path\":\"1e9c6f8a87bf1d7f5bb1349fdd145fb8.jpg\"},{\"path\":\"76677a80be6421eecbd6a54657ab5e45.jpg\"},{\"path\":\"fe39fe81cced737e615d0102fbf42dc4.jpg\"}]",
    "property_type": "RESI",
    "school_score": 9,
    "sqft": 1320,
    "source": "MLSListings",
    "state": "CA",
    "status": "A",
    "tags": [
      
    ],
    "unique_id": "MLSListings_81668344",
    "updated_at": "2017-07-03T08:40:00+0800",
    "year_built": 1960,
    "zip": "95003"
  },
  {
    "area": "\u897f\u96c5\u56fe\u57ce\u5e02\u5708",
    "address": "18 6th St",
    "fav_users_num": 0,
    "bathrooms": "3.25",
    "bedrooms": "3.0",
    "city": "Kirkland",
    "close_price": 0,
    "current_list_price": 1448000,
    "estimated_monthly_rent": 5199,
    "estimated_yearly_return": "0.0449748",
    "id": 11500349,
    "list_date": "2017-06-13T07:00:00+0800",
    "location_latitude": "47.6758250",
    "location_longitude": "-122.1965350",
    "openhouses": [
      {
        "start_time": "2017-06-25T12:00:00+0800",
        "end_time": "2017-06-25T15:00:00+0800"
      }
    ],
    "photo_json": "[{\"path\":\"fb31e33a5ca075a4b3cd9335180c9869.jpg\"},{\"path\":\"a6afa75839fbd8a1d07b967cc511493d.jpg\"},{\"path\":\"c4a56588bede21c3acb6cf31e5ded860.jpg\"},{\"path\":\"91ec7225b846e94f9c3c7fddb20da00d.jpg\"},{\"path\":\"750256b45cba4306664e7c40745100a0.jpg\"},{\"path\":\"facc905935c4207c80fe9eaa8a9eb650.jpg\"},{\"path\":\"a86fb9d6d633b5036171e0ad30b2fd25.jpg\"},{\"path\":\"911e58082326c4fec69b39c2a1244db9.jpg\"},{\"path\":\"de0a5521b8067bb35b64d42bba10269c.jpg\"},{\"path\":\"3d86f55ee28b13879b46a72400e9ed67.jpg\"},{\"path\":\"5a04ec1b49688105def6c9208ab1e799.jpg\"},{\"path\":\"c5a97a6518934257b212c26e171f6a3d.jpg\"},{\"path\":\"9d3a89728116c1e2fcf4ff9d81561542.jpg\"},{\"path\":\"d9e18e40819a4455f6cfb3773e392940.jpg\"},{\"path\":\"04e504d986a2649b724eeede1b00715c.jpg\"},{\"path\":\"7e20396ea267b02eb88bb0c148c6d55a.jpg\"},{\"path\":\"ed339aea95f71daf0ee8df09fc84aa82.jpg\"},{\"path\":\"f41b56e08d97e160e18da3e1d561dfee.jpg\"},{\"path\":\"0e0f9bf1346ec94cd449706228c7918c.jpg\"},{\"path\":\"270c9b14f37572d423dd3597195256e9.jpg\"}]",
    "property_type": "COND",
    "school_score": 10,
    "sqft": 2650,
    "source": "NWMLS",
    "state": "WA",
    "status": "A",
    "tags": [
      
    ],
    "unique_id": "NWMLS_1149370",
    "updated_at": "2017-07-03T08:24:22+0800",
    "year_built": 2013,
    "zip": "98033"
  }
]
```

##### 返回参数说明
| 参数名 | 类型 | 说明 | 
| --- | --- | --- |
| area | string | 所属城市圈 | 
| address | string | 街道地址 | 
| bathrooms | float | 浴室数 | 
| bedrooms | int | 卧室数 | 
| city | string | 城市 | 
| close_price | int | 成交价格 | 
| current_list_price | int | 挂牌价格 | 
| estimated_monthly_rent | int | 预计月租金 | 
| estimated_yearly_return | float | 预计年回报率 | 
| list_date | datetime | 挂牌日期, UTC时间 | 
| openhouses | array | 开放日 | 
| photo_json | string | 图片JSON | 
| property_type | string | 房产类型 | 
| school_score | int | 学校分数 | 
| sqft | int | 平方英尺数 | 
| source | string | 来源 | 
| state | string | 州 | 
| unique_id | string | 唯一ID | 
| updated_at | datetime | 更新时间, UTC时间 | 
| year_built | int | 建筑时间 | 
| zip | string | 邮编  | 

##### 抛出异常
* 无

--- 

### 获取地图上二手房列表

#### 简要描述
* 获取指定条件的地图上的二手房的房源列表

#### 请求URL
* /api/home/get_homes_map_list

##### 请求方式
* POST

##### 参数
| 参数名 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| current_list_price_filter_on | 否 | boolean | 是否过滤价格默认false | 
| current_list_price_filter_max | 否 | integer | 最高价格 | 
| current_list_price_filter_min | 否 | integer | 最低价格 | 
| sqft_filter_on | 否 | boolean | 是否过滤房屋面积默认false | 
| sqft_filter_min | 否 | integer | 最小面积 | 
| sqft_filter_max | 否 | integer | 最大面积 | 
| bedrooms_filter_on | 否 | boolean | 是否过滤卧室数默认false | 
| bedrooms_filter_min | 否 | integer | 最小卧室数 | 
| bedrooms_filter_max | 否 | integer | 最大卧室数 | 
| bathrooms_filter_on | 否 | boolean | 是否过滤浴室数默认false | 
| bathrooms_filter_min | 否 | integer | 最小浴室数 | 
| bathrooms_filter_max | 否 | integer | 最大浴室数 | 
| year_built_filter_on | 否 | boolean | 是否过滤建筑年份默认false | 
| year_built_filter_min | 否 | integer | 最小建筑年份 | 
| year_built_filter_max | 否 | integer | 最大建筑年份 | 
| roi_filter_on | 否 | boolean | 是否过滤投资回报率默认false | 
| roi_filter_min | 否 | float | 最低回报率 | 
| location_rect_filter_on | 否 | boolean | 是否过滤地理位置默认false | 
| location_rect_filter_type | 否 | string | 地理过滤方式, 如果用最大最小经纬度过滤传”min_max_degrees” | 
| latitude_min | 否 | float | 最小纬度 | 
| latitude_max | 否 | float | 最大纬度 | 
| longitude_min | 否 | float | 最小经度 | 
| longitude_max | 否 | float | 最大经度 | 
| property_type_candidate_array_on | 否 | boolean | 是否过滤房产类型默认false | 
| property_type_candidate_array | 否 | array | 房产类型数组:独栋别墅对应RESI,联排别墅对应COND,公寓对应APT,多户住宅对应MULT | 
| status_candidate_array_on | 否 | boolean | 是否过滤状态默认true | 
| status_candidate_array | 否 | array | 房产状态数组:在售对应A,已售S,成交中P,默认["A"] | 
| area_candidate_array_on | 否 | boolean | 是否开启按城市圈数据筛选默认false | 
| area_candidate_array | 否 | array | 城市圈 数组 | 
| city_candidate_array_on | 否 | boolean | 是否过滤城市默认false | 
| city_candidate_array | 否 | array | 城市数组 | 
| zip_candidate_array_on | 否 | boolean | 是否过滤邮编默认false | 
| zip_candidate_array | 否 | array | 邮编数组 | 
| updated_at_orderBy_on | 否 | boolean | 是否按照过滤时间排序默认true | 
| updated_at_orderBy_order | 否 | string | "DESC"或者"ASC" | 
| page_size | 否 | integer | 每页显示数量默认800 | 
| page_number | 否 | integer | 第几页默认1  | 

#### 请求示例
```
{
  "property_type_candidate_array_on": true,
  "property_type_candidate_array": [
  "RESI",
  "COND"
  ],
  "latitude_min": 36.106451583947454,
 "latitude_max": 37.435255615976935,
 "longitude_min": -122.35619565585932,
 "longitude_max": -121.15044614414057,
 "location_rect_filter_on": true
}
```

#### 返回示例
```
[
  {
    "p": 885000,
    "y": "36.9865420",
    "x": "-121.9187780",
    "i": "MLSListings_81667677",
    "t": "RESI"
  },
  {
    "p": 899000,
    "y": "36.9802890",
    "x": "-121.9057170",
    "i": "MLSListings_81667753",
    "t": "COND"
  },
  {
    "p": 1299000,
    "y": "37.3280842",
    "x": "-121.9124769",
    "i": "MLSListings_81667345",
    "t": "RESI"
  },
  {
    "p": 1399000,
    "y": "37.2403673",
    "x": "-121.9299622",
    "i": "MLSListings_81667889",
    "t": "RESI"
  },
  {
    "p": 589000,
    "y": "37.1052150",
    "x": "-122.1022210",
    "i": "MLSListings_81667931",
    "t": "RESI"
  },
  {
    "p": 929000,
    "y": "36.9890290",
    "x": "-121.9869883",
    "i": "MLSListings_81667663",
    "t": "RESI"
  }
]
```

##### 返回参数说明
| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| p | int | 挂牌价格 |
| y | float | 纬度 |
| x | float | 经度 |
| i | string | 唯一ID |
| t | string | 房产类型 |

##### 抛出异常
* 无

--- 

## 房源详情数据

### <del>二手房详情（旧）</del>

#### 简要描述
* 获取指定二手房的详情

#### 请求URL
* /api/home/get_one_home_by_unique_id

##### 请求方式
* POST

##### 参数
| 参数名 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| unique_id | 是 | string | 房源唯一ID |

#### 请求示例
```
{
"unique_id": "MLSListings_81667802"
}
```

#### 返回示例
```
{
  "area": "\u65e7\u91d1\u5c71\u57ce\u5e02\u5708",
  "address": "5319 Leigh Ave",
  "appendix": "{\"\u516c\u5171\u8bbe\u65bd\":\"\u516c\u5171\u8bbe\u65bd\",\"\u5176\u4ed6\u8bbe\u65bd\":\"\u5929\u7a97\",\"\u5236\u51b7\":\"\u4e2d\u592e\u7a7a\u8c03\",\"\u5236\u70ed\":\"\u4e2d\u592e\u7a7a\u8c03\",\"\u53a8\u623f\":\"\u82b1\u5c97\u5ca9\u53f0\u9762,\u6d17\u7897\u673a,\u6709\u6c34\u69fd\u7684\u53a8\u623f\u5de5\u4f5c\u53f0,\u98df\u54c1\u50a8\u85cf\u5ba4,\u9152\u67dc\",\"\u5730\u57fa\":\"\u5730\u677f\u4e0b\u9762\u4f9b\u7535\u7ebf\u6216\u6c34\u7ba1\u7b49\u901a\u8fc7\u7684\u69fd\u9699\",\"\u5730\u677f\":\"\u786c\u6728,\u74e6\",\"\u5b89\u5168\":\"\u89c6\u9891\u7cfb\u7edf,\u5176\u4ed6\",\"\u5c4b\u9876\":\"\u6df7\u5408\",\"\u623f\u95f4\":\"\u5f00\u653e\u6d3b\u52a8\u5ba4\",\"\u6d17\u8863\u623f\":\"\u5728\u8f66\u5e93\",\"\u989d\u5916\u4fe1\u606f\":\"\u4e0d\u9002\u7528\"}",
  "fav_users": [
    
  ],
  "fav_users_num": 0,
  "bathrooms": "2.00",
  "bedrooms": "3.0",
  "city": "San Jose",
  "current_list_price": 1249000,
  "description": "Innovative designed, quality materials with immaculate details in this beautiful home located in a very desirable neighborhood. This fabulous complete remodeled home consists of new hardwood floor, central A\/C,  new copper plumbing, all high-end energy efficient LG\u00c2\u00ae appliances. Kitchen is equip with pantry, barn sinks, built-in wine cooler in an oversize island. Spacious formal dining room. Bathrooms are built with skylight, standup shower, rain forest showered and motion-sensor toilet. Energy efficient with brand-new recessed LED lighting, garage Epoxy flooring and new covered wooden deck. Stunning front & back landscaping completed with all pavers driveway. Complete with Arlo\u00c2\u00ae video camera, Nest\u00c2\u00ae thermo and detectors, Ring\u00c2\u00ae doorbell, keyless front door entry, lawn sprinkler system and more. Smart systems are control though cell phone. Access to top schools as such Alta Vista Elem, Union MS and Leigh HS. Offer if any will be due 7\/14\/17 at 2pm. Strong preemptive offer are welcome.",
  "estimated_monthly_rent": 3650,
  "estimated_yearly_return": "0.0452615",
  "garage": 2,
  "hoa": "0",
  "id": 11545346,
  "listing_company": "PHP Group, Inc",
  "listing_name": "Tam Nguyen",
  "location_latitude": "37.2416077",
  "location_longitude": "-121.9229933",
  "lot_sqft": 6820,
  "mls_number": "ML81667802",
  "openhouses": [
    {
      "start_time": "2017-07-08T13:00:00+0800",
      "end_time": "2017-07-08T16:00:00+0800"
    },
    {
      "start_time": "2017-07-09T13:00:00+0800",
      "end_time": "2017-07-09T16:00:00+0800"
    },
    {
      "start_time": "2017-07-05T11:00:00+0800",
      "end_time": "2017-07-05T14:00:00+0800"
    },
    {
      "start_time": "2017-07-12T16:00:00+0800",
      "end_time": "2017-07-12T19:00:00+0800"
    }
  ],
  "photo_json": "[{\"path\":\"45af205424978d676f933526bd307b6e.jpg\"},{\"path\":\"4c71bf6a38b8a20298b3a6e95a6f008b.jpg\"},{\"path\":\"0210631a8db6781588ec8d14064a6d0d.jpg\"},{\"path\":\"7d925fe88094f1aa7d458a2e5bf8cee9.jpg\"},{\"path\":\"606fdf9bab99dcae0c5586ae78bff92b.jpg\"},{\"path\":\"c435121aad25bb89ccd7f9aec96e7dfe.jpg\"},{\"path\":\"4f56c33d767dfefbee75df993e52a07a.jpg\"},{\"path\":\"6cf434fc80d701833087430e093ce6e0.jpg\"},{\"path\":\"1976069888b35c0d5fe3691c7ddebce7.jpg\"},{\"path\":\"703237f8a6ab3a138031401232e0bc03.jpg\"},{\"path\":\"521a1e11dbf93990ced440526a4d4545.jpg\"},{\"path\":\"32738211e60e1a1d529ee7e6fbe13167.jpg\"},{\"path\":\"d29690fdb7d82e2c2c4c9a4216aa316a.jpg\"},{\"path\":\"675bbb0419d32e24bba9577c03c28d42.jpg\"},{\"path\":\"8f074d1a1812c0d49fb0f7179f23b94b.jpg\"},{\"path\":\"408ca8cf51c9468695beed1e2258f8a4.jpg\"},{\"path\":\"27f9794ef7cbccc5ae74fc88cbc5d16f.jpg\"},{\"path\":\"67ff8698d5567342a77637eba894e4ce.jpg\"},{\"path\":\"d64050953c910651da29846daaffda31.jpg\"},{\"path\":\"d73a234013e5fe1ed608a53b6804dd34.jpg\"},{\"path\":\"c4b039079da29b26140e559b2a4f2458.jpg\"},{\"path\":\"609b056c2d39d1a957d3dcd06b957b89.jpg\"},{\"path\":\"b2fd60bb0d30d77d1e4d5e9ca5f3915c.jpg\"},{\"path\":\"dffc586ad10624c5890c8966db54f806.jpg\"},{\"path\":\"64e9fd39c2f2209e0925f3a3dd3db468.jpg\"},{\"path\":\"2a2f314e98f3ad59117abfd7160f3e69.jpg\"},{\"path\":\"aa96e04be5e645671e6a4e9d915b9dd1.jpg\"},{\"path\":\"31c7e86582a94b57abfe8c14fcd7cdcb.jpg\"},{\"path\":\"6a82c80499d0ce4c504dbaebadf9856f.jpg\"},{\"path\":\"f6045de207ba968621487a7c16329b6b.jpg\"},{\"path\":\"c6d8f75136076cb1520e021263db275e.jpg\"},{\"path\":\"35c057e2b9b7f8c4eb05e2a2451f8173.jpg\"},{\"path\":\"835d44a35c74736d41f617d4f5ca12f9.jpg\"},{\"path\":\"b1f9030b89506017547ff223f50d4753.jpg\"},{\"path\":\"849e32df9476b5b063936bc6f38ff8c2.jpg\"},{\"path\":\"33a780bd3c04265dc53f7756bb0647e6.jpg\"},{\"path\":\"7284ddcaa871cb0777509c57b43925bd.jpg\"},{\"path\":\"0e06a5e475d589919f387158ab81c773.jpg\"},{\"path\":\"541f1b054ecc65cbf3dae29319798ebb.jpg\"},{\"path\":\"af0864e1f6977f2476a5eb7f15455c69.jpg\"},{\"path\":\"49f31d4dff8e97bcbba5e73affcd6fba.jpg\"},{\"path\":\"a5f00400aa53b2f3703dac9595512fce.jpg\"},{\"path\":\"35e372625ebbf859b5eb2277468f9963.jpg\"},{\"path\":\"81b759c30d4590d9e6c71f036cfed927.jpg\"},{\"path\":\"22c51039e4e307be0eee5cab2ca8fcc2.jpg\"},{\"path\":\"901d7af1e4cad09cc9f428d702a88fcf.jpg\"},{\"path\":\"9d4b3c540c88990c09aa991cce52a5a1.jpg\"},{\"path\":\"82be423772c00de7388a2308d018a8f4.jpg\"}]",
  "property_type": "RESI",
  "schools": [
    {
      "district_name": "",
      "grade_range": "PK-8",
      "id": 7312,
      "name": "Almaden Preparatory School",
      "overview_link": "http:\/\/www.greatschools.org\/california\/san-jose\/9543-Almaden-Preparatory-School\/?s_cid=gsapi",
      "type": "private",
      "unique_id": "02158971"
    },
    {
      "district_name": "",
      "grade_range": "6-12",
      "id": 7328,
      "name": "Beacon",
      "overview_link": "http:\/\/www.greatschools.org\/california\/san-jose\/8703-Beacon\/?s_cid=gsapi",
      "type": "private",
      "unique_id": "00083983"
    },
    {
      "district_name": "",
      "grade_range": "K-8",
      "id": 7349,
      "name": "Carden Academy of Almaden",
      "overview_link": "http:\/\/www.greatschools.org\/california\/san-jose\/8937-Carden-Academy-Of-Almaden\/?s_cid=gsapi",
      "type": "private",
      "unique_id": "00092692"
    },
    {
      "district_name": "",
      "grade_range": "PK-11",
      "id": 7359,
      "name": "Champion School",
      "overview_link": "http:\/\/www.greatschools.org\/california\/san-jose\/26701-Champion-School\/?s_cid=gsapi",
      "type": "private",
      "unique_id": "A0900265"
    },
    {
      "district_name": "Campbell Union High",
      "gs_rating": 10,
      "grade_range": "9-12",
      "id": 7452,
      "name": "Leigh High School",
      "overview_link": "http:\/\/www.greatschools.org\/california\/san-jose\/5425-Leigh-High-School\/?s_cid=gsapi",
      "type": "public",
      "unique_id": "060723008122"
    },
    {
      "district_name": "Union Elementary",
      "gs_rating": 10,
      "grade_range": "K-5",
      "id": 11626,
      "name": "Alta Vista Elementary School",
      "overview_link": "http:\/\/www.greatschools.org\/california\/los-gatos\/5710-Alta-Vista-Elementary-School\/?s_cid=gsapi",
      "type": "public",
      "unique_id": "064032006667"
    },
    {
      "district_name": "",
      "grade_range": "K-5",
      "id": 11639,
      "name": "Mulberry School",
      "overview_link": "http:\/\/www.greatschools.org\/california\/los-gatos\/9799-Mulberry-School\/?s_cid=gsapi",
      "type": "private",
      "unique_id": "A9101133"
    },
    {
      "district_name": "",
      "grade_range": "K-5",
      "id": 11640,
      "name": "Mulberry School",
      "overview_link": "http:\/\/www.greatschools.org\/california\/los-gatos\/10277-Mulberry-School\/?s_cid=gsapi",
      "type": "private",
      "unique_id": "A9500591"
    },
    {
      "district_name": "",
      "grade_range": "PK-8",
      "id": 50938,
      "name": "St. Frances Cabrini Elementary School",
      "overview_link": "http:\/\/www.greatschools.org\/california\/san-jose\/9098-St.-Frances-Cabrini-Elementary-School\/?s_cid=gsapi",
      "type": "private",
      "unique_id": "01609214"
    },
    {
      "district_name": "",
      "grade_range": "PK-5",
      "id": 50939,
      "name": "St. Timothy's Lutheran School",
      "overview_link": "http:\/\/www.greatschools.org\/california\/san-jose\/9449-St.-Timothy's-Lutheran-School\/?s_cid=gsapi",
      "type": "private",
      "unique_id": "02013415"
    },
    {
      "district_name": "Union Elementary",
      "gs_rating": 10,
      "grade_range": "6-8",
      "id": 50943,
      "name": "Union Middle School",
      "overview_link": "http:\/\/www.greatschools.org\/california\/san-jose\/5719-Union-Middle-School\/?s_cid=gsapi",
      "type": "public",
      "unique_id": "064032006680"
    },
    {
      "district_name": "",
      "grade_range": "K-5",
      "id": 50946,
      "name": "South Valley Childrens Center A",
      "overview_link": "http:\/\/www.greatschools.org\/california\/san-jose\/22465-South-Valley-Childrens-Center-A\/?s_cid=gsapi",
      "type": "private",
      "unique_id": "A0770592"
    },
    {
      "district_name": "",
      "grade_range": "PK-8",
      "id": 125063,
      "name": "South Valley Carden School, Inc.",
      "overview_link": "http:\/\/www.greatschools.org\/california\/san-jose\/9274-South-Valley-Carden-School,-Inc.\/?s_cid=gsapi",
      "type": "private",
      "unique_id": "01900521"
    }
  ],
  "school_score": 10,
  "sqft": 1740,
  "sqft_price": 718,
  "source": "MLSListings",
  "state": "CA",
  "status": "A",
  "stories": 1,
  "tags": [
    
  ],
  "unique_id": "MLSListings_81667802",
  "updated_at": "2017-07-03T12:20:01+0800",
  "year_built": 1958,
  "zip": "95124",
  "rank_score": 8,
  "total_visit_count": 3
}
```

##### 返回参数说明

| 参数名 | 类型 | 说明 |
| --- | --- | --- | 
| area | string | 所属城市圈 |
| address | string | 街道地址 |
| appendix | string | 额外数据 |
| bathrooms | float | 浴室数 |
| bedrooms | int | 卧室数 |
| city | string | 城市 |
| close_price | int | 成交价格 |
| current_list_price | int | 挂牌价格 |
| description | string | 房源描述 |
| estimated_monthly_rent | int | 预计月租金 |
| estimated_yearly_return | float | 预计年回报率 |
| garage | int | 车库数 |
| hoa | int | 物业费 |
| listing_company | string | 挂牌公司 |
| listing_name | string | 挂牌中介名字 |
| listing_email | string | 挂牌中介邮件 |
| listing_phone | string | 挂牌中介电话 |
| list_date | datetime | 挂牌日期, UTC时间 |
| location_latitude | float | 纬度 |
| location_longitude | float | 经度 |
| lot_sqft | int | 占地面积 |
| mls_number | string | MLS号码 |
| openhouses | array | 开放日 |
| photo_json | string | 图片JSON |
| property_type | string | 房产类型 |
| schools | array | 学校 |
| school_score | int | 学校分数 |
| sqft | int | 平方英尺数 |
| sqft_price | int | 单位面积价格 |
| source | string | 来源 |
| state | string | 州 |
| status | string | 状态 |
| stories | int | 楼层数 |
| unique_id | string | 唯一ID |
| updated_at | datetime | 更新时间, UTC时间 |
| year_built | int | 建筑时间 |
| zip | string | 邮编 |

##### 抛出异常
* HOME_101: 房源的unique_id不存在

--- 

### 二手房详情（新）

#### 简要描述
* 获取指定二手房的详情，
* 主要是返回的学校数据优化，其他同旧api

#### 请求URL
* /api/home/get_home_info_by_unique_id

##### 请求方式
* POST

##### 参数
| 参数名 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| unique_id | 是 | string | 房源唯一ID |

#### 请求示例
```
{
"unique_id": "MLSListings_81667802"
}
```

#### 返回示例
```
{
    "area": "旧金山城市圈",
    "address": "145 Duncan Way",
    "appendix": "{\"停车\":\"1车位车库,街边停车\",\"制热\":\"中央空调1区,其他供暖\",\"厨房\":\"早餐吧台,石头台面,洗碗机,垃圾处理机,微波炉,餐具室,独立烤箱,冰箱,更新的厨房\",\"地基\":\"地板下面供电线或水管等通过的槽隙\",\"地板\":\"全部硬木地板,瓦\",\"屋顶\":\"组合木瓦\",\"景观\":\"水,树木繁茂\",\"浴室\":\"淋浴间,瓷砖,翻新的卫生间\",\"特殊信息\":\"无\",\"院子\":\"后院,甲板,围栏,前院,旁院,自动喷水器,工具棚\",\"风格\":\"现代的\"}",
    "fav_users_num": 0,
    "bathrooms": "2.00",
    "bathrooms_half": 0,
    "bedrooms": "3.0",
    "city": "Oakland",
    "close_date": "2016-12-12T00:00:00+0800",
    "close_price": 1100000,
    "community": "Oakland Zip Code 94611",
    "current_list_price": 997000,
    "description": "One of a kind! John Hans Ostwald Garden Chalet on a picturesque .24 acre lot. Open interior spaces, vaulted ceilings, large windows and an overall feeling of being enveloped in nature. Two parcels merged into one. In the heart of Montclair and a short commute to San Francisco. OH 11/6, 2pm-4:30pm.",
    "estimated_monthly_rent": 4200,
    "estimated_yearly_return": "0.1052068",
    "garage": 0,
    "hoa": "0",
    "id": 7785331,
    "list_date": "2016-10-28T00:00:00+0800",
    "listing_company": "Dudum Real Estate Group",
    "location_latitude": "37.8379389",
    "location_longitude": "-122.2201616",
    "lot_sqft": 10601,
    "mls_number": "40762328",
    "new_construction": false,
    "openhouses": [],
    "photo_json": "[{\"path\":\"8aeded91d6fbd7b833b1a0ce3445acd6.jpg\"},{\"path\":\"19dca16d0d44b36851ba5065eaaf67a5.jpg\"},{\"path\":\"af556dc40cf4eb049dbd13ff8fd514e0.jpg\"},{\"path\":\"328705b2eaf6212dad764e4ff72b05fa.jpg\"},{\"path\":\"c4f4ae14942fe36eff0713ee24bcec93.jpg\"},{\"path\":\"2d2f6b87f092607622773106ea9693dc.jpg\"},{\"path\":\"8f928a9384202dd9efabba2ea189027c.jpg\"},{\"path\":\"20d88eaa04ee46752bf9283e899b5bb4.jpg\"},{\"path\":\"59851fe6336d7266d7aa6104cbfb7fbd.jpg\"},{\"path\":\"dfc274d02783d2c8016a85c59bf5a8ac.jpg\"},{\"path\":\"2742c7fdf72ca3a2b9b913c53f06a138.jpg\"},{\"path\":\"0d912717bbf689e2143751277f8da801.jpg\"},{\"path\":\"0d3363c6d4bff6a273423446a985b59d.jpg\"},{\"path\":\"ae95ffba788a9de1b3913f8eedde3254.jpg\"},{\"path\":\"25c440f19ae0687f3bb0721e323bd2cf.jpg\"}]",
    "photos_num": 0,
    "property_type": "RESI",
    "schools": {
        "private": [],          // 私立学校
        "unknow": [],           // 未知学校类型
        "public": [             // 公立学校
            {
                "address": "1023 Macarthur Boulevard, \nOakland, CA  94610",
                "city": "Oakland",
                "district_name": "Oakland Unified School District",
                "district_nces_id": "0628050",
                "enrollment": 1515,
                "fax": "(510) 879-3049",
                "gs_id": 247,
                "gs_rating": 4,
                "grade_range": "9-12",
                "id": 266782,
                "lat": "37.8053130",
                "lon": "-122.2365100",
                "name": "Oakland High School",
                "nces_id": "062805004304",
                "overview_link": "https://www.greatschools.org/california/oakland/247-Oakland-High-School/?s_cid=gsapi",
                "parent_rating": 3,
                "phone": "(510) 874-3676",
                "ratings_link": "https://www.greatschools.org/school/rating.page?state=CA&id=247&s_cid=gsapi",
                "reviews_link": "https://www.greatschools.org/school/parentReviews.page?state=CA&id=247&s_cid=gsapi",
                "school_stats_link": "https://www.greatschools.org/modperl/achievement/CA/247",
                "state": "CA",
                "type": "public",
                "unique_id": "CA_247",
                "website": "http://www.ousd.org/oaklandhigh",
                "grade_range_cn": "高中",     // 学校年级
                "sort": "F4"
            }
        ]
    },
    "school_score": 9,
    "sqft": 1820,
    "sqft_price": 604,
    "source": "EBRD",
    "state": "CA",
    "status": "S",
    "unique_id": "EBRD_40762328",
    "updated_at": "2018-02-08T00:12:00+0800",
    "year_built": 1972,
    "zip": "94611",
    "is_restricted": false,
    "rank_score": 7,
    "total_visit_count": 5,
    "extended_homes": []
}
```

##### 返回参数说明

| 参数名 | 类型 | 说明 |
| --- | --- | --- | 
| area | string | 所属城市圈 |
| address | string | 街道地址 |
| appendix | string | 额外数据 |
| bathrooms | float | 浴室数 |
| bedrooms | int | 卧室数 |
| city | string | 城市 |
| close_price | int | 成交价格 |
| current_list_price | int | 挂牌价格 |
| description | string | 房源描述 |
| estimated_monthly_rent | int | 预计月租金 |
| estimated_yearly_return | float | 预计年回报率 |
| garage | int | 车库数 |
| hoa | int | 物业费 |
| listing_company | string | 挂牌公司 |
| listing_name | string | 挂牌中介名字 |
| listing_email | string | 挂牌中介邮件 |
| listing_phone | string | 挂牌中介电话 |
| list_date | datetime | 挂牌日期, UTC时间 |
| location_latitude | float | 纬度 |
| location_longitude | float | 经度 |
| lot_sqft | int | 占地面积 |
| mls_number | string | MLS号码 |
| openhouses | array | 开放日 |
| photo_json | string | 图片JSON |
| property_type | string | 房产类型 |
| schools | array | 学校 |
| school_score | int | 学校分数 |
| sqft | int | 平方英尺数 |
| sqft_price | int | 单位面积价格 |
| source | string | 来源 |
| state | string | 州 |
| status | string | 状态 |
| stories | int | 楼层数 |
| unique_id | string | 唯一ID |
| updated_at | datetime | 更新时间, UTC时间 |
| year_built | int | 建筑时间 |
| zip | string | 邮编 |

##### 抛出异常
* HOME_101: 房源的unique_id不存在

--- 

### 新房详情（新）

#### 简要描述
* 获取指定新房的详情

#### 请求URL
* /api/community/get_home_info_by_unique_id

##### 请求方式
* POST

##### 参数
| 参数名 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| unique_id | 是 | string | 房源唯一ID |

#### 请求示例
```
{
"unique_id": "BDX_3336_113948"
}
```

#### 返回示例
```
{
    "id": 2641749,
    "address": "6809 Skyview Drive",
    "area": "旧金山城市圈",
    "builder": "Discovery Homes",
    "bdx_id": "113948",
    "builder_website": "http://www.discoveryhomes.com/california/oakland/skyview/floorplans",
    "city": "Oakland",
    "description": "NOW OPEN!\r\n\r\nSkyview is a brand new collection of homes where  executive living reaches a new height. The prestigious Oakland hills  location boasts breathtaking 4 bridge views to enjoy from each of the  homes relaxing balconies. With 3 different residences  to choose, you will find prestigious amenities and quality  craftsmanship throughout. Luxury living is key at Skyview.\r\n\r\nYou won’t want to miss your exclusive opportunity  to own your own piece of the best in bay area living!",
    "display": true,
    "email": "sales@discoveryhomes.com",
    "location_latitude": "37.7788000",
    "location_longitude": "-122.1610000",
    "name": "Skyview",
    "photos": [],
    "photo_json": "[{\"path\":\"6171b19f29995c500b746d8cb43f7704.jpg\"},{\"path\":\"fbdbfd58315f1ea917a1c1f0cb66d11c.jpg\"},{\"path\":\"1026dd42a3ec4af9676e675685503789.jpg\"},{\"path\":\"445d67a1fd4263f7a7d1ee2f2178be67.jpg\"},{\"path\":\"a3a2cdec7d2cd9c4a03e2d5d091017d5.jpg\"},{\"path\":\"70c00c5008daa3adc2b8ce0a63e35e33.jpg\"},{\"path\":\"dc65dbe007495a77714b8b2cf3f23575.jpg\"},{\"path\":\"ac1d3022b230fa5c89611bb4254a6c02.jpg\"},{\"path\":\"2d32f400c1e431c307c164799bdc2ca1.jpg\"},{\"path\":\"f175932df2d7fc265c1316a0e0ffed14.jpg\"},{\"path\":\"4f20d78931a918c74fbe213ce2c23368.jpg\"},{\"path\":\"281a66f83df8a1d09ff7c8357204a160.jpg\"}]",
    "plans": {
        "BDX_PLAN_1457140": {
            "id": 8396317,
            "appendix": "{\"户型预览\":\"http://www.discoveryhomes.com/pdf/floorplan/skyview-residence-a.pdf\"}",
            "bathrooms": "2.00",
            "bdx_id": "1457140",
            "bedrooms": "4.0",
            "current_list_price": 1049000,
            "garage": 2,
            "min_price": 1049000,
            "name": "Residence 1",
            "photo_json": "[{\"path\":\"0253f8944dd60ec03a9edff78fb5ff28.jpg\"}]",
            "property_type": "RESI",
            "sqft": 2903,
            "status": "A",
            "stories": 2,
            "unique_id": "BDX_PLAN_1457140",
            "updated_at": "2018-03-04T05:49:36+0800"
        }
    },
    "property_type": "RESI",
    "schools": {
        "private": [],      // 私立学校
        "public": [         // 公立学校
            {
                "address": "1023 Macarthur Boulevard, \nOakland, CA  94610",
                "city": "Oakland",
                "district_name": "Oakland Unified School District",
                "district_nces_id": "0628050",
                "enrollment": 1515,
                "fax": "(510) 879-3049",
                "gs_id": 247,
                "gs_rating": 4,
                "grade_range": "9-12",
                "id": 266782,
                "lat": "37.8053130",
                "lon": "-122.2365100",
                "name": "Oakland High School",
                "nces_id": "062805004304",
                "overview_link": "https://www.greatschools.org/california/oakland/247-Oakland-High-School/?s_cid=gsapi",
                "parent_rating": 3,
                "phone": "(510) 874-3676",
                "ratings_link": "https://www.greatschools.org/school/rating.page?state=CA&id=247&s_cid=gsapi",
                "reviews_link": "https://www.greatschools.org/school/parentReviews.page?state=CA&id=247&s_cid=gsapi",
                "school_stats_link": "https://www.greatschools.org/modperl/achievement/CA/247",
                "state": "CA",
                "type": "public",
                "unique_id": "CA_247",
                "website": "http://www.ousd.org/oaklandhigh",
                "grade_range_cn": "高中",         // 年级
                "sort": "F4"
            }
        ],
        "unknow": []        // 未知类型
    },
    "source": "BDX",
    "state": "CA",
    "status": "A",
    "unique_id": "BDX_3336_113948",
    "updated_at": "2018-03-04T05:49:35+0800",
    "zip": "94605",
    "photos_num": 0,
    "plans_count": 0,
    "plan_bathrooms_max": "3.00",
    "plan_bathrooms_min": "2.00",
    "plan_bedrooms_max": "4.0",
    "plan_bedrooms_min": "4.0",
    "plan_current_list_price_max": 1499500,
    "plan_current_list_price_min": 1049000,
    "plan_sqft_max": 3312,
    "plan_sqft_min": 2903,
    "total_visit_count": 1,
    "commission_type": "PREC",
    "commission_prec_min": "0.00",
    "commission_prec_max": "0.00",
    "fix_top": 0,
    "deleted": false
}
```

##### 返回参数说明
* 

##### 抛出异常
* HOME_101: 房源的unique_id不存在

--- 


### 市场分析

#### 简要描述
* 获取指定二手房的市场分析挂牌价格和成交价格的对比

#### 请求URL
* /api/home/get_home_cma

##### 请求方式
* POST

##### 参数
| 参数名 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| year | 是 | int | 年份 |
| month | 是 | int | 月份 |
| zip | 否 | string | 邮编 |
| city | 否 | string | 城市 |
| state | 否 | string | 州 |

#### 请求示例
```
{
"city": "Sunnyvale",
"state": "CA",
"year": 2017,
"month": 4
}
```

#### 返回示例
```
[
  {
    "current_list_price": 875000,
    "unique_id": "MLSListings_81636123",
    "close_price": 965888,
    "sqft_price": 862
  },
  {
    "current_list_price": 799888,
    "unique_id": "MLSListings_81638766",
    "close_price": 870000,
    "sqft_price": 743
  },
  {
    "current_list_price": 599950,
    "unique_id": "MLSListings_81643341",
    "close_price": 660000,
    "sqft_price": 868
  },
  {
    "current_list_price": 575000,
    "unique_id": "MLSListings_81640658",
    "close_price": 600000,
    "sqft_price": 764
  },
  {
    "current_list_price": 1188000,
    "unique_id": "MLSListings_81644340",
    "close_price": 1220000,
    "sqft_price": 725
  },
]
```

##### 返回参数说明
| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| current_list_price | int | 挂牌价格 |
| unique_id | string | 唯一ID |
| close_price | int | 成交价格 |
| sqft_price | int | 单位面积价格 |

##### 抛出异常
* GENERAL_101: 必需的参数未提供

--- 

### <del>想要看房（旧）</del>

#### 简要描述
* 用户想要看房

#### 请求URL
* /api/home/saveUserWantLook

##### 请求方式
* POST
 
#### 请求示例
```
{
	"token":"test_ccy_token",
	"obj_type":1,
	"unique_id":"BDX_44858_110476",
	"time_bespoke":"2017-04-19 08:24:41",
	"type_look":1
}
```

##### 请求参数
| 参数名 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| obj_type | 是 | int | 房源类型 1（subdivision）, 2（home）|
| unique_id | 是 | string | 房源unique_id |
| time_bespoke | 是 | string | 预约时间 |
| type_look | 是 | int | 看房选项-1、实地自己直接看房 2、实地陪同看房  3、视频看房 |

#### 返回示例
```
{
  "state": 1,
  "msg": "record success",
  "msg_desc": "记录成功"
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 |  |

##### 抛出异常
* User not login - 用户未登录
* Params invalid - 必填参数有未填

---

### 预约看房

#### 简要描述
* 用户想要看房（新）
* 获取验证码，使用/api/auth/sendMobileVcode这个api，type=7

#### 请求URL
* /api/home/save_bespeak_house

##### 请求方式
* POST
 
#### 请求示例
```
{
	"token":"test_token",
	"obj_type":1,
	"unique_id":"BDX_44858_110476",
	"mobile":13800001111,
	"vcode":1234
}
```

##### 请求参数
| 参数名 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 否 | string | 用户token |
| obj_type | 是 | int | 房源类型 1（subdivision）, 2（home）|
| unique_id | 是 | string | 房源unique_id |
| mobile | 是 | int | 手机号 |
| vcode | 是 | int | 如果手机不需要验证该值为-1 |

#### 返回示例
```
{
  "state": 1,
  "msg": "record success",
  "msg_desc": "记录成功"
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 |  |

##### 抛出异常
* User not login - 用户未登录
* Params invalid - 必填参数有未填
* verify code invalid - 验证码无效

---

### <del>想下单</del>

#### 简要描述
* 用户想下单
* 新产品已取消

#### 请求URL
* /api/home/saveUserWantOrder

##### 请求方式
* POST
 
#### 请求示例
```
{
	"token":"test_ccy_token",
	"obj_type":1,
	"unique_id":"BDX_44858_110476",
	"type_pay":1,
	"offer_amount":9.99,
	"is_system_decide_price":1,
	"downpay_amount":20
}
```

##### 请求参数
| 参数名 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| obj_type | 是 | int | 房源类型 1（subdivision）, 2（home）|
| unique_id | 是 | string | 房源unique_id |
| type_pay | 是 | int | 付款类型 - 1：分期，2：全款 |
| offer_amount | 否 | decimal | 用户出价 |
| is_system_decide_price | 否 | int | 是否由平台帮客户定价 |
| downpay_amount | 否 | int | 首付金额比例,如果用户选的是付款,该值可不传。默认值0 |
| downpay_type | 否 | int | 首付金额类型 - 1:百分比, 2:实际金额 |


#### 返回示例
```
{
  "state": 1,
  "msg": "record success",
  "msg_desc": "记录成功"
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 |  |

##### 抛出异常
* User not login - 用户未登录
* Params invalid - 必填参数有未填

---

### 预估回报率

#### 简要描述
* 计算二手房源预估回报率
* 计算公式

#### 请求URL
* /api/home/get_house_estimated_return

##### 请求方式
* POST
 
#### 请求示例
```
{
	"unique_id":"CRMLS_302777790"
}
```

##### 请求参数
| 参数名 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| unique_id | 是 | string | 房源unique_id |

#### 返回示例
```
{
    "cost_transfer": 3000,                                  // 过户费用
    "cost_trade_ratio": 0.06,                               // 交易费率
    "estimated_yearly_return": "0.0959472",                 // 预估年回报率
    "house_price": 2999888,                                 // 购买价格
    "down_payment_ratio": 0.2,                              // 首付比例
    "down_payment": 599977.6,                               // 首付金额
    "cost_cash_buied": 602977.6,                            // 购买花费现金（首付金额+过户费用）
    "house_holding_period": 10,                             // 房源持有年限（默认10年）
    "estimated_yearly_increment_ratio": 0.08855,            // 房价年涨幅
    "last_yearly_increment_ratio": 0.0744,                  // 上一年涨幅
    "rent_yearly_income": 143316,                           // 租金年收入
    "rent_monthly_income": 11943,                           // 租金月收入
    "rent_yearly_increment_ratio": 0.0481,                  // 租金年涨幅
    "cost_vacancy_ratio": 0.05,                             // 房屋出租空置率（默认0）
    "cost_house_manage": 0,                                 // 房屋出租管理费
    "cost_property_tax":100,                                // 房产税/年
    "cost_property_tax_yearly_increment_ratio": 0.03,       // 房产税年增长
    "cost_hoa": "0",                                        // 物业费/年
    "cost_hoa_yearly_increment_ratio": 0.02,                // 物业费年增长
    "cost_insurance_ratio": 0.001,                          // 保险费费率（默认房价千万之一）
    "cost_insurance": 2999,                                 // 保险费
    "cost_insurance_yearly_increment_ratio": 0.01,          // 保险费年增长
    "cost_maintenance": 0,                                  // 维护费/年（默认无）
    "cost_maintenance_yearly_increment_ratio": 0.01,        // 维护费年增长
    "cost_other": 0,                                        // 其他费用/年（默认无）
    "cost_other_yearly_increment_ratio": 0.01,              // 其他费用年增长
    "mortgage_year": 30,                                    // 贷款年限
    "loan_rate": 0.045,                                     // 贷款利率
    "loan_expenses_monthly": 12159.99,                      // 还贷金额/月
    "loan_expenses_yearly": 145919.92,                      // 还贷金额/年
    "list": [               // 未来N年预估
        {                   // 第1年
            "cost_all": 2999,                               // 持有成本
            "cost_property_tax": 0,                         // 房产税
            "cost_hoa": 0,                                  // 物业费
            "cost_insurance": 2999,                         // 保险费  
            "cost_maintenance": 0,                          // 维护费
            "cost_other": 0,                                // 其他费用
            "future_sale_price": 2999888,                   // 未来售价
            "future_cost_trade": 179993.28,                 // 未来交易费用
            "future_loan_no_returned": 2399911.2,           // 未来交易时未还贷款
            "future_sale_house_income": 419983.52,          // 售房收入
            "future_price_difference": -179993.27,          // 交易价差
            "future_price_difference_ratio": -0.06,         // 价差比率
            "future_yearly_rent": 143316,                   // 未来年回报率
            "loan_expenses_yearly": 145919.92,              // 贷款支出/年
            "rent_net_earning": -5602.92,                   // 租金净收益/年
            "yearly_cash_rio": -0.0093,                     // 现金回报率/年
            "yearly_return_ratio": -0.3128,                 // 此时出售回报率
            "total_rent_net_earning": 0,                    // 累计租金净收益 
            "total_loan_expenses": 0                        // 累计贷款总支出
        }
    ],
    "rent_net_earning_ratio": 0.0467                        // 现金购房出租净收益
    "n_year_return_ratio_year": 10,                         // N年回报率，年数
    "n_year_return_ratio_nums": "212.25%"                   // N年回报率，回报率
}
```

##### 计算公式

| 数据 | 类型 | 公式 | 备注 |
| --- | --- | --- | --- |
| 年租金收入 | 被动 | rent_yearly_income * pow((1 + rent_yearly_increment_ratio), N) | N年 |
| 持有成本 | 被动 | cost_all = cost_property_tax + cost_hoa + cost_insurance + cost_maintenance + cost_other | 第N年 cost_property = cost_property * pow((1+cost_property_ratio), N) |
| 贷款支出 | 被动 | l = house_price * (1 - down_payment_ratio); <br>c = loan_rate / 12; <br>n = mortgage_months * 12; <br>cn = pow(1.0 + c, n); <br>loan_expenses_monthly = round(l * (c * cn) / (cn - 1), 2); <br> loan_expenses_yearly = loan_expenses_monthly * 12 | 每月还贷金额 |
| 净收益 | 被动 | rent_net_earning = rent_yearly_income - loan_expenses_yearly - cost_all |  |
| 现金回报率 | 被动 | rent_net_earning / cost_cash_buied |  |
| 首付现金支出 | 被动 | cost_cash_buied = down_payment + cost_transfer |  |
| 未还贷款 | 被动 | future_loan_no_returned = loan_monthly_principal * ((mortgage_months - N) * 12) |  |
| 此时出售·售房收益 | 被动 | sale_house_income = future_sale_price - future_cost_trade - future_loan_no_returned | TODO |
| 此时出售·年化回报率 | 被动 |  | TODO |
| N年年化投资回报率 | 被动 |  | 取最后一年的出售年化回报率 |
| 购买价格 | 主动 | house_price |  |
| 首付金额 | 主动+被动 | down_payment <br> house_price * down_payment_ratio |  |
| 首付比例 | 主动+被动 | down_payment_ratio <br> down_payment / house_price | 默认20% |
| 贷款年限 | 主动 | mortgage_year | 默认30 |
| 贷款利率 | 主动 | loan_rate | 默认4.5% |
| 过户费用 | 主动 | cost_transfer | 默认3000 |
| 现金购房出租净收益率 | 被动 | rent_net_earning_ratio = (rent_yearly_income - cost_all) / (house_price + cost_transfer) |  |
| 月租金 | 主动 | rent_monthly_income |  |
| 年增长 | 主动 | rent_yearly_increment_ratio |  |
| 空置率 | 无 |  |  |
| 管理费 | 无 |  |  |
| 房产税/年 | 主动 | cost_property_tax |  |
| 房产税增长幅度 | 主动 | cost_property_tax_yearly_increment_ratio |  |
| 保险费/年 | 主动 | cost_insurance |  |
| 保险费增长幅度 | 主动 | cost_insurance_yearly_increment_ratio |  |
| 维护费 | 无 |  |  |
| 其他费用 | 无 |  |  |
| 房屋年增值率 | 主动 | estimated_yearly_increment_ratio |  |
| 上次出售年增长率 | 固定 | last_yearly_increment_ratio |  |
| 持有年限 | 主动 | n_year_return_ratio_year |  |
| 售出价格 | 被动 | future_sale_price = house_price * pow((1 + (estimated_yearly_increment_ratio)), N) |  |
| 交易费用·费率 | 主动 | cost_trade_ratio | 默认6% |
| 交易费用 | 被动 | future_cost_trade = future_sale_price * cost_trade_ratio |  |
| 价差·百分比 | 被动 | (future_cost_trade - house_price) / house_price |  |
| 价差 | 被动 | future_cost_trade - house_price |  |

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 |  |

##### 抛出异常
* params invalid - 必填参数有未填
* the home unique_id can not be found - 房源id无效

---


### 获取zillow数据

#### 简要描述
* 获取zillow数据

#### 请求URL
* /api/home/getHomeInfo

##### 请求方式
* POST
 
#### 请求示例
```
{
	"unique_id":"ConnectMLS_09615554",
	"type":2
	"proxy":""
}
```

##### 请求参数
| 参数名 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| type | 是 | int | 房源类型 1（subdivision）, 2（home）|
| unique_id | 是 | string | 房源unique_id |
| proxy | 否 | string | 代理，默认不使用。[storm,abuyun] |
| debug | 否 | boolean | 是否debug，默认false |

#### 返回示例
```
{
    "zpid": 28977581,              // zpid
    "sale_zestimate": "652256",    // 预估售价
    "rental_zestimate": "3988",    // 预估租金
    "zillow_data": {               // zillow爬取数据
        "id": "458965",
        "zpid": "28977581",
        "url": "https://www.zillow.com/homedetails/805-Edna-Dr-Fort-Worth-TX-76140/28977581_zpid/",
        "linkmd5id": "131e9fb831cbad2018bfe2b7ffbbc942",
        
        // 交易历史数据
        "data_price_history": "[[\"02/13/06\", \"Sold: \", \"$85,263\", 0, \"$64\", 0]]",
        
        // 税历史数据
        "data_tax_history": "[[\"2016\", \"$1,800\", \"--\", \"$66,000\", \"+10.9%\"], [\"2015\", \"$1,800\", \"--\", \"$59,500\", \"--\"], [\"2014\", \"$1,800\", \"--\", \"$59,500\", \"+4.9%\"], [\"2013\", \"--\", \"--\", \"$56,700\", \"-0.2%\"], [\"2012\", \"--\", \"--\", \"$56,800\", \"--\"], [\"2011\", \"--\", \"--\", \"$56,800\", \"+18.6%\"], [\"2010\", \"--\", \"--\", \"$47,900\", \"-28.0%\"], [\"2009\", \"--\", \"--\", \"$66,500\", \"-3.3%\"], [\"2008\", \"--\", \"--\", \"$68,800\", \"-8.4%\"], [\"2007\", \"--\", \"--\", \"$75,100\", \"-11.8%\"], [\"2006\", \"--\", \"--\", \"$85,100\", \"--\"], [\"2005\", \"--\", \"--\", \"$85,100\", \"+18.7%\"], [\"2004\", \"--\", \"--\", \"$71,700\", \"--\"], [\"2003\", \"--\", \"--\", \"$71,700\", \"+14.0%\"], [\"2002\", \"--\", \"--\", \"$62,900\", \"+7.5%\"], [\"2001\", \"--\", \"--\", \"$58,500\", \"--\"]]",
        "has_price_history": "1",
        "has_tax_history": "1",
        "url_price_history": "https://www.zillow.com/AjaxRender.htm?encparams=3~4979708942308449090~o9sSm0dcJR0pjimibXK8bzERsFD7tVvQBwvRiT_rP7FYF4mq0XUYPf6ydp7vbS-Klr-Id1Z-916rcq5fuMx9lOCvS-DzeNDH1RryKieU7LCxNh8mtSb-RnuuY3KSYrFLbG1bdt5zIisVukYzcsA2rS9lNPPstYiIFSCoaMIYETB4cLAl7Z-JZn6CNEQPNCAnNJhHPWNrctR9cWPDRVFK9ySeQ-ykhvSd6u0ASnuFVIudKgDroqedem9QeCTDlYglS8Dn6qcRMafQT1JMmDP3OJRNzc-OcwacufjjLR9zEh6w5Tp79j6qQcMOt_rjeGcg0zXhdAOVFoqx4kqdQta_xA==&rwebid=53011205&rhost=1",
        "url_tax_history": "https://www.zillow.com/AjaxRender.htm?encparams=10~7439359312622275201~2uZ5cwv9RQqsDGbJc6q4kjD69AomezVYlPOq-HB7EekK2Bzk_jwAFwHEQSvXT7RGLj6Jyr1ZCBmUyZjHKD2DlR85B7fIJfHKHd5bi7wAC-2Ww0csDokm7oojXW-vNmPNElGnCcACiMWZhRFhmqHtSIk_TN_UMkRo8slScJYdFJ-RYjCNTy4EV85sz5TKVv9lXJ4dmG9HpjT6ZrWnTyb0oNCcMm67cNeMx6RY0nZusSMz3IPFdFExdLBlx5-llrU8HErdervVqrb2VgUGRz8CN2Mnh52lSD465S2u1LQsAzw=&rwebid=53011205&rhost=1",
        "nums_spider": "2"
    },
    "zillow_base": {
        "id": "472344",
        "updated_at": "2017-08-17 01:47:47",
        "address": "805 Edna Dr, ",
        "city": "Fort Worth",
        "state": "TX",
        "zip": "76140",
        "current_list_price": "Off Market",
        "bedrooms": "3",
        "bathrooms": "2.00",
        "sqft": "1322",
        "log_sqft": "0",
        "status": "",
        "year_built": "1967",
        "location_latitude": "32.6269170",
        "location_longitude": "-97.2921630",
        "close_price": "0",
        "close_date": "",
        "property_type": "",
        "url": "https://www.zillow.com/homedetails/805-Edna-Dr-Fort-Worth-TX-76140/28977581_zpid/",
        "linkmd5id": "131e9fb831cbad2018bfe2b7ffbbc942"
    }
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 |  |

##### 抛出异常

---

### 获取zillow数据

#### 简要描述
* 使用地址获取zillow数据

#### 请求URL
* /api/home/getHomeInfoByAddress

##### 请求方式
* POST
 
#### 请求示例
```
{
	"address":"225 Fox Sparrow Ln",
	"city":"Brisbane",
	"state":"CA"
	"proxy":""
}
```

##### 请求参数
| 参数名 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| address | 是 | string | 地址 |
| city | 是 | string | 城市 |
| state | 是 | string | 州 |
| proxy | 否 | string | 代理，默认不使用。[storm,abuyun,other] |
| debug | 否 | boolean | 是否debug，默认false |

#### 返回示例
```
{
    "zpid": 28977581,              // zpid
    "sale_zestimate": "652256",    // 预估售价
    "rental_zestimate": "3988",    // 预估租金
    "zillow_data": {               // zillow爬取数据
        "id": "458965",
        "zpid": "28977581",
        "url": "https://www.zillow.com/homedetails/805-Edna-Dr-Fort-Worth-TX-76140/28977581_zpid/",
        "linkmd5id": "131e9fb831cbad2018bfe2b7ffbbc942",
        
        // 交易历史数据
        "data_price_history": "[[\"02/13/06\", \"Sold: \", \"$85,263\", 0, \"$64\", 0]]",
        
        // 税历史数据
        "data_tax_history": "[[\"2016\", \"$1,800\", \"--\", \"$66,000\", \"+10.9%\"], [\"2015\", \"$1,800\", \"--\", \"$59,500\", \"--\"], [\"2014\", \"$1,800\", \"--\", \"$59,500\", \"+4.9%\"], [\"2013\", \"--\", \"--\", \"$56,700\", \"-0.2%\"], [\"2012\", \"--\", \"--\", \"$56,800\", \"--\"], [\"2011\", \"--\", \"--\", \"$56,800\", \"+18.6%\"], [\"2010\", \"--\", \"--\", \"$47,900\", \"-28.0%\"], [\"2009\", \"--\", \"--\", \"$66,500\", \"-3.3%\"], [\"2008\", \"--\", \"--\", \"$68,800\", \"-8.4%\"], [\"2007\", \"--\", \"--\", \"$75,100\", \"-11.8%\"], [\"2006\", \"--\", \"--\", \"$85,100\", \"--\"], [\"2005\", \"--\", \"--\", \"$85,100\", \"+18.7%\"], [\"2004\", \"--\", \"--\", \"$71,700\", \"--\"], [\"2003\", \"--\", \"--\", \"$71,700\", \"+14.0%\"], [\"2002\", \"--\", \"--\", \"$62,900\", \"+7.5%\"], [\"2001\", \"--\", \"--\", \"$58,500\", \"--\"]]",
        "has_price_history": "1",
        "has_tax_history": "1",
        "url_price_history": "https://www.zillow.com/AjaxRender.htm?encparams=3~4979708942308449090~o9sSm0dcJR0pjimibXK8bzERsFD7tVvQBwvRiT_rP7FYF4mq0XUYPf6ydp7vbS-Klr-Id1Z-916rcq5fuMx9lOCvS-DzeNDH1RryKieU7LCxNh8mtSb-RnuuY3KSYrFLbG1bdt5zIisVukYzcsA2rS9lNPPstYiIFSCoaMIYETB4cLAl7Z-JZn6CNEQPNCAnNJhHPWNrctR9cWPDRVFK9ySeQ-ykhvSd6u0ASnuFVIudKgDroqedem9QeCTDlYglS8Dn6qcRMafQT1JMmDP3OJRNzc-OcwacufjjLR9zEh6w5Tp79j6qQcMOt_rjeGcg0zXhdAOVFoqx4kqdQta_xA==&rwebid=53011205&rhost=1",
        "url_tax_history": "https://www.zillow.com/AjaxRender.htm?encparams=10~7439359312622275201~2uZ5cwv9RQqsDGbJc6q4kjD69AomezVYlPOq-HB7EekK2Bzk_jwAFwHEQSvXT7RGLj6Jyr1ZCBmUyZjHKD2DlR85B7fIJfHKHd5bi7wAC-2Ww0csDokm7oojXW-vNmPNElGnCcACiMWZhRFhmqHtSIk_TN_UMkRo8slScJYdFJ-RYjCNTy4EV85sz5TKVv9lXJ4dmG9HpjT6ZrWnTyb0oNCcMm67cNeMx6RY0nZusSMz3IPFdFExdLBlx5-llrU8HErdervVqrb2VgUGRz8CN2Mnh52lSD465S2u1LQsAzw=&rwebid=53011205&rhost=1",
        "nums_spider": "2"
    },
    "zillow_base": {
        "id": "472344",
        "updated_at": "2017-08-17 01:47:47",
        "address": "805 Edna Dr, ",
        "city": "Fort Worth",
        "state": "TX",
        "zip": "76140",
        "current_list_price": "Off Market",
        "bedrooms": "3",
        "bathrooms": "2.00",
        "sqft": "1322",
        "log_sqft": "0",
        "status": "",
        "year_built": "1967",
        "location_latitude": "32.6269170",
        "location_longitude": "-97.2921630",
        "close_price": "0",
        "close_date": "",
        "property_type": "",
        "url": "https://www.zillow.com/homedetails/805-Edna-Dr-Fort-Worth-TX-76140/28977581_zpid/",
        "linkmd5id": "131e9fb831cbad2018bfe2b7ffbbc942"
    }
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 |  |

##### 抛出异常

---




## 翻译

### 谷歌翻译
#### 简要描述
* 用谷歌翻译API将英文翻译成中文

#### 请求URL
* /api/translate/get_info

##### 请求方式
* POST

##### 参数
| 参数名 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| content | 是 | string | 待翻译英文内容 |

#### 请求示例
```
{
"content": "A big fox jump over a grey huge dog."
}

```

#### 返回示例
```
{
  "status": 1,
  "msg": "has chinese content",
  "info": "大狐狸跳过一个灰色的大狗。",
  "md5": "ebb5ea9765e11487a6358675f93f929a"
}
```

##### 返回参数说明
| 参数名 | 类型 | 说明 |
| --- | --- | --- | 
| status | int | API状态1为成功 |
| msg | string | 状态对应的消息 |
| info | string | 翻译的中文 |
| md5 | string | 待翻译英文的MD5 |

##### 抛出异常
* GENERAL_101: 必需的参数未提供

--- 



## 用户信息（UserInfoController）

### 获取用户信息 

#### 简要描述
* 获取用户信息，已登录状态

#### 请求URL
* /api/user/getUserInfo

##### 请求方式
* POST

##### 参数

| 参数名 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 必填 | string | 用户验证token |

#### 请求示例
```
{
	"token":"802385eee2f7f8670e0992518795bfa065c42633d635ef816a009d0f6b0f0377"
}
```

#### 返回示例
```
{
  "state": 1,
  "result": {
    "id": 11,
    "username": "方块七",
    "avatar": "http://wx.qlogo.cn/mmopen/xMwtEJibGa8aUicIudlGAYh0wuq0ty3Jy3QFLeFIUnB0SWHPzxfibcdaOgVbma0Kibtec8k7axGaxaCSoqnib9Ribic7EqHsMzHqk0r/0",
    "wx_id": 11
  }
}
```

##### 返回参数说明
| 参数 | 类型 | 说明 |
| --- | --- | --- |
| id | int | 用户ID |
| username | string | 用户名 | 
| email | string | 邮箱 | 
| mobile | string | 手机 |
| avatar | string | 用户头像 | 
| wx_id | int | 微信ID |

##### 抛出异常
* 无

---

### 保存用户信息（手机、邮箱） 
#### 简要描述
* 保存用户信息（手机、邮箱 ）

#### 请求URL
* /api/user/saveUserInfo

##### 请求方式
* POST

##### 参数
| 参数名 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 必填 | string | 用户token |
| mobile | 选填 | string | 用户手机 | 
| email | 选填 | string| 用户邮箱 |

#### 请求示例
```
{
	"token":"802385eee2f7f8670e0992518795bfa065c42633d635ef816a009d0f6b0f0377",
	"mobile":"1111",
	"email":"chenchuanyao@gmail.com"
}
```

#### 返回示例
```
{
  "state": 1,
  "msg": "update user info success",
  "msg_desc": "更新用户信息成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 保存用户名

#### 简要描述
* 保存用户名
 
#### 请求URL 
* /api/user/saveUsername

##### 请求方式
* POST

##### 参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 必填 | string | 用户token |
| username | 必填 | string | 用户名 |

#### 请求示例
```
{
	"token":"802385eee2f7f8670e0992518795bfa065c42633d635ef816a009d0f6b0f0377",
	"username":"这是方块七吗"
}
```

#### 返回示例
```
{
  "state": 1,
  "msg": "update username info success",
  "msg_desc": "更新用户名成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 记录邀请关系

#### 简要描述
* 保存用户名
 
#### 请求URL 
* /api/user/recordInviteRelation

##### 请求方式
* POST

##### 参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 必填 | string | 用户token |
| inviter_id | 必填 | int | 邀请者ID |

#### 请求示例
```
{
	"token":"test_ccy_token",
	"inviter_id":2
}
```

#### 返回示例
```
{
  "state": 1,
  "msg": "record invite relation success",
  "msg_desc": "记录邀请关系成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* GENERAL_101 - User not login 用户未登录
* GENERAL_101 - inviter uid invalid 邀请者ID无效
* GENERAL_101 - already record invite relation 邀请关系已经记录

---


### 邀请的用户

#### 简要描述
* 获取用户邀请的用户信息
 
#### 请求URL 
* /api/user/invitedUserList

##### 请求方式
* POST

##### 参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 必填 | string | 用户token |
| page_number | 选填 | int | 页码 ，默认1 |
| page_size | 选填 | int | 数量，默认20条 |

#### 请求示例
```
{
	"token":"token"
}
```

#### 返回示例
```
{
    "nums_look": 2,  // 要看房人数
    "nums_order": 1, // 要下单人数
    "nums_buy": 2,   // 已成交人数
    "page_number": 1,
    "page_size": 20,
    "count": 3,      // 总共邀请人数
    "list": [
        {
            "info": {
                "user_id": 519,
                "username": "test",   // 邀请用户名
                "avatar": "http://wx.qlogo.cn/mmopen/hNcbBHricu4NugZop8W8aSjT2zyiaCx2CjwdzI7P7QJNROyp5LFuAezwQvsicx4ia2EraNBkXIiclISfCTicJdPvqR03jUtgK7OEWR/0",  // 用户头像
                "time_reg": "2017-06-29T14:52:31+0000",
                "status": "已成交"     // 用户状态
            }
        }
    ],
    "account": {
        "id": 1,
        "user_id": 11,
        "amount_total": "57.00",   // 用户账户金额
        "amount_use": "57.00",     // 可用金额
        "amount_freeze": "0.00",   // 冻结金额
        "amount_estimate": 3000,   // 预计收益金额
        "time_add": "2017-08-02T08:24:48+0000",
        "time_upd": "2017-08-04T06:46:21+0000",
        "deleted": false
    }
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* GENERAL_101 - User not login 用户未登录

---

### 获取邀请码

#### 简要描述
* 获取用户邀请码
 
#### 请求URL 
* /api/user/getInviteQrCode

##### 请求方式
* POST

##### 参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 必填 | string | 用户token |

#### 请求示例
```
{
	"token":"token",
}
```

#### 返回示例
```
{
  "id": 11,
  "username": "这是方块七吗",
  "invite_qrcode": "2626aaa007a544d89363648bd666deda.jpg",
  "img": "http://images-cn.fang88.com/2626aaa007a544d89363648bd666deda.jpg"
}
```

##### 返回参数说明

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| id | int | 用户ID |
| username | string | 用户名 | 
| invite_qrcode | string | 邀请码 |
| img | string | 图片链接 |

##### 抛出异常
* GENERAL_101 - User not login 用户未登录

---

### 验证管理员

#### 简要描述
* 判断用户是不是管理
 
#### 请求URL 
* /api/user/getUserAdmin

##### 请求方式
* POST

##### 参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 必填 | boolean | 用户token |

#### 请求示例
```
{
	"token":"token",
}
```

#### 返回示例
```
{
  "is_admin": true
}
```

##### 返回参数说明

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| is_admin | boolean | 是否是管理员 |

##### 抛出异常
* GENERAL_101 - User not login 用户未登录

---

### 保存外链网站用户信息

#### 简要描述
* 保存外链网站用户信息
 
#### 请求URL 
* /api/user/saveUserInfoOther

##### 请求方式
* POST

##### 参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| mobile | 否 | string | 手机号 |
| email | 否 | string | 邮箱 |
| type | 否 | int | 外链类型，1：乐居 |

#### 请求示例
```
{
	"mobile":"1111",
	"email":"ccy034106@163.com",
	"type":1
}
```

#### 返回示例
```
{
    "state": 1,
    "msg": "record user info success",
    "msg_desc": "记录用户信息成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 推荐状态

#### 简要描述
* 保存用户推荐状态
 
#### 请求URL 
* /api/user/saveRecommendStatus

##### 请求方式
* POST

##### 参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| status | 是 | int | 状态类型，1：每日推荐、2：每周推荐、3：每月推荐、9：不推荐 |

#### 请求示例
```
{
	"token":"test_ccy_token",
	"status":2
}
```

#### 返回示例
```
{
    "state": 1,
    "msg": "update username recommend status success",
    "msg_desc": "更新用户推荐状态成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---


### 保存用户密码

#### 简要描述
* 保存用户密码
 
#### 请求URL 
* /api/user/save_password

##### 请求方式
* POST

##### 参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 是 | string | token |
| password | 是 | string | 密码 |
| check_password | 是 | string | 确认密码 |

#### 请求示例
```
{
	"token": "test",
	"password": "123456",
	"check_password":"12345"
}
```

#### 返回示例
```
{
    "state": 1,
    "msg": "update password success",
    "msg_desc": "密码设置成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* User not login - 用户未登录，token错误
* params invalid - 参数无效，没传password或check_password
* password dissimilar - 两次密码不一致

---

### 更新用户密码

#### 简要描述
* 更新用户密码
* 使用旧密码
 
#### 请求URL 
* /api/user/update_password

##### 请求方式
* POST

##### 参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 是 | string | token |
| old_password | 是 | string | 密码 |
| password | 是 | string | 密码 |
| check_password | 是 | string | 确认密码 |

#### 请求示例
```
{
	"token": "test",
	"old_password": "123456",
	"password": "123456",
	"check_password":"12345"
}
```

#### 返回示例
```
{
    "state": 1,
    "msg": "update password success",
    "msg_desc": "密码修改成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* User not login - 用户未登录，token错误
* params invalid - 参数无效，没传password或check_password
* old password invalid - 旧密码无效
* password dissimilar - 两次密码不一致

---

### 更新手机号码

#### 简要描述
* 更新用户手机
 
#### 请求URL 
* /api/user/save_mobile

##### 请求方式
* POST

##### 参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 是 | string | token |
| mobile | 是 | int | 手机 |
| vcode | 是 | int | 验证码 |

#### 请求示例
```
{
	"token":"test",
	"mobile":"15800001111",
	"vcode":"123456"
}
```

#### 返回示例
```
{
    "state": 1,
    "msg": "update mobile success",
    "msg_desc": "手机验证成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* User not login - 用户未登录，token错误
* params invalid - 参数无效，没传password或check_password
* mobile is register - 手机已注册
* verify code invalid - 验证码无效

---

### 更新邮箱号码

#### 简要描述
* 更新用户邮箱
 
#### 请求URL 
* /api/user/save_email

##### 请求方式
* POST

##### 参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 是 | string | token |
| email | 是 | int | 邮箱 |
| vcode | 是 | int | 验证码 |

#### 请求示例
```
{
	"token":"test",
	"email":"test@xxx.com",
	"vcode":"123456"
}
```

#### 返回示例
```
{
    "state": 1,
    "msg": "update email success",
    "msg_desc": "邮箱验证成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* User not login - 用户未登录，token错误
* params invalid - 参数无效，没传password或check_password
* verify code invalid - 验证码无效

---


## 授权控制器（AuthController）

```
· 用于用户登录、注册。
· 可以使用微信openid+password登录。password在微信登录时会返回。
· mysql库中的密码使用sha256加密。
· 保存在session中密码的加密方式：sha256( sha256(password) + salt )
· 现在用户信息都保存在session中，后面扩展可以移到redis中
```

### 退出登录

#### 简要描述
* 清除session、token信息

#### 请求URL
* /api/auth/doLogout

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 必填 | string | 用户token |

#### 请求示例
```
{
	"token":"802385eee2f7f8670e0992518795bfa065c42633d635ef816a009d0f6b0f0377"
}
```

#### 返回示例
```
{
  "state": 1,
  "msg": "user logout success",
  "msg_desc": "退出成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---


### 其他渠道用户注册

#### 简要描述
* 其他渠道用户注册

#### 请求URL
* /api/auth/otherRegisterUser

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| username | 是 | string | 用户名 |
| source | 是 | int | 来源：1 微信小程序、2 google、3 facebook、4 房多多、5 linkedin |
| uid | 是 | string | 来源用户id |
| email | 是 | string | 邮箱 |
| mobile | 否 | string | 手机号 |
| avatar | 否 | string | 头像 |

#### 请求示例
```
{
	"username":"lind",
	"uid":1223423,
	"source":3,
	"email":"ccy@fang88.me"
}
```

#### 返回示例
```
{
    "state": 1,
    "result": {
        "id": 524,
        "username": "lind",
        "headimgurl": "",
        "email": "",   // 邮箱
        "mobile": "",  // 手机
        "is_chk_email": 0,  // 是否验证邮箱，不做强制验证
        "is_chk_mobile": 0, // 是否验证手机
        "source": 3,    // 用户来源
        "source_uid": "1223423",  // 用户来源id
        "token": "ee26fd4dd238f137a948e9eefa49d32c7abfe471953372fe32b1057f703a45fa"
    }
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常

---

### 检测手机号

#### 简要描述
* 检测手机号格式是否正确、是否注册过

#### 请求URL
* /api/auth/doChkMobile

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| mobile | 是 | int | 手机号 |
| area | 是 | string | 区域(us,cn) |

#### 请求示例
```
{
	"mobile":"13011112221",
	"area":"us"
}
```

#### 返回示例
```
{
    "state": 1,
    "msg": "ok"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1:成功, 0:失败 |
| msg | 英文消息 | 消息：<br> params invalid - 参数无效 <br> mobile invalid - 手机无效 <br> mobile already register - 手机已注册 <br> ok - 可以注册 |

##### 抛出异常

---

### 检查邮箱

#### 简要描述
* 注册时验证邮箱格式是否正确、是否注册过

#### 请求URL
* /api/auth/doChkMobile

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| email | 是 | string | 邮箱 |

#### 请求示例
```
{
	"mobile":"ccy@fang88.me",
}
```

#### 返回示例
```
{
    "state": 1,
    "msg": "ok"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1:成功, 0:失败 |
| msg | 英文消息 | 消息：<br> params invalid - 参数无效 <br> email invalid - 邮箱无效 <br> email already register - 邮箱已注册 <br> ok - 可以注册 |

##### 抛出异常

---

### 正常注册

#### 简要描述
* 美国、中国，手机、邮箱注册

#### 请求URL
* /api/auth/doRegister

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| area | 是 | string | 区域（us,cn） |
| password | 是 | string | 密码 |
| mobile | 否 | string | 手机，如果 area=cn 则是必填 |
| vcode | 否 | int | 验证码，如果 area=cn 则是必填 |
| email | 否 | string | 邮箱，如果 area=us 则是必填 |

#### 请求示例
```
{
	"mobile":"13011112221",
	"password":"111111",
	"area":"cn"
}
```

#### 返回示例
```
{
    "state": 1,
    "result": {
        "id": 527,
        "username": "130****2221",
        "email": "",
        "mobile": "13011112221",
        "is_chk_email": 0,
        "is_chk_mobile": 1,
        "source": 0,
        "token": "202f6107543534433150b0e844ec8d8a9e0e09b5ac54d48172e33f52b4fdb604"
    }
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1:成功, 0:失败 |
| msg | 英文消息 | 消息：<br> params invalid - 参数无效 <br> email invalid - 邮箱无效 <br> email already register - 邮箱已注册 <br> mobile invalid - 手机无效 <br> mobile already register - 手机已注册 <br> vcode invalid - 验证码无效 <br> vcode error01 - 验证码错误，数据库没有记录 <br> vcode error02 - 验证码错误，数据库有记录，但不同 <br> register area invalid - 注册区域无效  <br> ok - 可以注册 |

##### 抛出异常

---


### 正常登录

#### 简要描述
* 美国|中国 的 手机|邮箱 登录

#### 请求URL
* /api/auth/doLogin

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| obj | 是 | string | 手机或邮箱 |
| password | 是 | string | 密码 |

#### 请求示例
```
{
	"obj":"13011112221",
	"password":"111111"
}
```

#### 返回示例
```
{
    "state": 1,
    "result": {
        "id": 527,
        "username": "130****2221",
        "email": "",
        "mobile": "13011112221",
        "is_chk_email": 0,
        "is_chk_mobile": 1,
        "source": 0,
        "token": "202f6107543534433150b0e844ec8d8a9e0e09b5ac54d48172e33f52b4fdb604"
    }
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1:成功, 0:失败 |
| msg | 英文消息 | 消息：<br> params invalid - 参数无效 <br> password error - 密码错误 <br> account no exist - 账号不存在 |

##### 抛出异常

---

### 获取手机验证码

#### 简要描述
* 获取手机验证码

#### 请求URL
* /api/auth/sendMobileVcode

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| mobile | 是 | string | 手机 |
| type | 是 | int | 验证码类型，1:手机注册、3:忘记密码、7:预约看房、8:短信登录 |

#### 请求示例
```
{
	"mobile":"13011112221",
	"type":1
}
```

#### 返回示例
```
{
    "state": 1,
    "msg": "send vcode success"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1:成功, 0:失败 |
| msg | 英文消息 | 消息 |

##### 抛出异常

---

### 验证邮箱

#### 简要描述
* 验证邮箱

#### 请求URL
* /api/auth/sendEmailVcode

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| email | 是 | string | 邮箱 |
| type | 是 | int | 验证码类型，2:邮箱注册、4:忘记密码 |

#### 请求示例
```
{
	"email":"ccy@fang88.me",
	"type":2
}
```

#### 返回示例
```
{
    "state": 1,
    "msg": "send vcode success"
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1:成功, 0:失败 |
| msg | 英文消息 | 消息 |

##### 抛出异常

---

### 绑定邮箱

#### 简要描述
* 注册用户没有邮箱，绑定邮箱

#### 请求URL
* /api/auth/setEmail

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| email | 是 | string | 邮箱 |
| token | 是 | string | 用户token |

#### 请求示例
```
{
	"email":"ccy@163.com",
	"token":"token"
}
```

#### 返回示例
```
{
    "state": 1,
    "msg": "绑定邮箱成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1:成功, 0:失败 |
| msg | 英文消息 | 消息：<br> 参数无效 <br> 邮箱无效 <br> 该用户不存在 <br> 该邮箱已注册 <br> |

##### 抛出异常

---

### 绑定手机

#### 简要描述
* 注册用户没有手机，绑定手机

#### 请求URL
* /api/auth/setMobile

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| mobile | 是 | string | 手机 |
| token | 是 | string | 用户token |
| vcode | 是 | int | 验证码 |

#### 请求示例
```
{
	"mobile":"15800001111",
	"token":"token",
	"vcode":"1111"
}
```

#### 返回示例
```
{
    "state": 1,
    "msg": "绑定手机成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1:成功, 0:失败 |
| msg | 英文消息 | 消息：<br> 参数无效 <br> 手机无效 <br> 该用户不存在 <br> 验证码无效 <br> 该手机已注册 <br> |

##### 抛出异常

---

### 验证邮箱

#### 简要描述
* 从邮件链接过来，调用该api，验证邮箱

#### 请求URL
* /api/auth/bindingEmail

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| email | 是 | string | 邮箱 |
| vcode | 是 | int | 验证码 |

#### 请求示例
```
{
	"email":"ccy@163.com",
	"vcode":"1111"
}
```

#### 返回示例
```
{
    "state": 1,
    "msg": "绑定邮箱成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1:成功, 0:失败 |
| msg | 英文消息 | 消息：<br> 参数无效 <br> 验证码无效 <br> 该邮箱未注册 <br> |

##### 抛出异常

---

### 重置密码

#### 简要描述
* 重置密码api

#### 请求URL
* /api/auth/resetPassword

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| object | 是 | string | 邮箱或手机 |
| vcode | 是 | string | 验证码 |
| password | 是 | string | 首次密码 |
| repeat_password | 是 | string | 重复密码 |
| type | 是 | int | 类型 3:手机、4:邮箱 |

#### 请求示例
```
{
	"obj":"ccy@163.com",
	"vcode":"vcode",
	"password":"111111",
	"repeat_password":"111111",
	"type"4"
}
```

#### 返回示例
```
{
    "state": 1,
    "result": {
        "id": 527,
        "username": "130****2221",
        "email": "",
        "mobile": "13011112221",
        "is_chk_email": 0,
        "is_chk_mobile": 1,
        "source": 0,
        "token": "202f6107543534433150b0e844ec8d8a9e0e09b5ac54d48172e33f52b4fdb604"
    }
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1:成功, 0:失败 |
| msg | 英文消息 | 消息：<br> 参数无效 <br> 两次密码不一致 <br> 验证码无效 <br> 错误的类型 <br> 该{手机|邮箱}未注册 <br> |

##### 抛出异常

---


### 保存手机&邮箱 

#### 简要描述
* 主要用于下载报告时强制填写信息

#### 请求URL
* /api/auth/saveMobileAndEmail

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| mobile | 否 | string | 手机 |
| vcode | 否 | string | 手机验证码 |
| email | 否 | string | 邮箱 |
| token | 是 | string | 用户登录token |

#### 请求示例
```
{
    "mobile":"15801351819",
    "vcode":"vcode",
    "email":"ccy@fang88.me"
    "token":"token"
}
```

#### 返回示例
```
{
    "state": 1,
    "result": "保存成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 1:成功, 0:失败 |
| msg | 英文消息 | 消息：<br> 参数无效 <br> 验证码无效 <br> 该token无效 <br> |

##### 抛出异常

---

### 房多多注册用户

#### 简要描述
* 房多多注册用户

#### 请求URL
* /api/auth/fangdd_user

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| mobile | 是 | string | 手机号 |
| home_unique_id | 否 | string | 浏览的房源唯一ID（注：房源ID和文章ID，必填一个） |
| article_id | 否 | string | 浏览的百科唯一ID（注：房源ID和文章ID，必填一个） |
| username | 否 | string | 用户名 |
| email | 否 | string | 邮箱 |
| ip | 否 | string | ip |
| info | 否 | array | 用户其他信息 <br> city:用户所在城市<br>time_reg:用户注册时间<br>wechat_name:微信名称<br>avatar:头像 |

#### 请求示例
```
{
	"username":"test",
	"mobile":"13011112222",
	"email":"ccy@fang88.com",
	"ip":"192.168.0.1",
	"info":{
		"city":"北京",
		"time_reg":"2017-06-29 13:10:57",
		"wechat_name":"微信名称",
		"avatar":"http://wx.qlogo.cn/mmopen/LXqicVqwJiatruNxibyyasJPfx5CG1fiavBbYszu3J2Ev9ps2AsuES5RtcH0NBrW93QYRcT138uoswWoEBRFMEpliadhcY2gga1I4/0"
	},
	"home_unique_id":"MLSListings_81638255",
	"article_id":"c4c7b59563f997f73d40bea"
}
```

#### 返回示例
```
{
    "error": 0,
    "msg": "record user info success"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| error | 错误代码 |  |
| msg | 错误消息 |  |

##### 抛出异常
* GENERAL_101 - params invalid 传递参数无效
* GENERAL_102 - mobile invalid 手机格式无效
* GENERAL_103 - view object unique_id invalid home_unique_id、article_id 必须有一个

---

### 订阅文章

#### 简要描述
* 订阅文章，本默认注册成用户
*

#### 请求URL
* /api/auth/doSubscribeArticle

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| email | 否 | string | 邮箱 |

#### 请求示例
```
{
	"email":"ccy@fang88.com"
}
```

#### 返回示例
```
{
    "state": 0,
    "msg": "订阅成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| error | 错误代码 |  |
| msg | 错误消息 |  |

##### 抛出异常
* 无

---

### 手机、验证码登录

#### 简要描述
* 通过手机、验证码直接登录或注册

#### 请求URL
* /api/auth/mobile_vcode_login

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| mobile | 是 | int | 手机 |
| vcode | 是 | int | 验证码 |

#### 请求示例
```
{
	"email":"ccy@fang88.com"
}
```

#### 返回示例
```
{
	"mobile":"15800001111",
	"vcode":"123"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| error | 错误代码 |  |
| msg | 错误消息 |  |

##### 抛出异常
* Params invalid - 参数无效
* verify code invalid - 验证码无效

---

### 更换邮箱

#### 简要描述
* 通过密码登录修改邮箱

#### 请求URL
* /api/user/save_email_by_pwd

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| email | 是 | string | 邮箱 |
| password | 是 | string | 密码 |

#### 请求示例
```
{
	"email":"ccy@fang88.com",
	"password":"123456"
}
```

#### 返回示例
```
{
    "state": 0,
    "msg": "邮箱修改成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| error | 错误代码 |  |
| msg | 错误消息 |  |

##### 抛出异常
* User not login - 用户未登录
* params invalid - 参数无效
* password invalid - 旧密码无效

---


### 验证手机

#### 简要描述
* 修改手机号前验证当前手机

#### 请求URL
* /api/user/check_mobile

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| mobile | 是 | int | 手机 |
| vcode | 是 | int | 验证码 |

#### 请求示例
```
{
	"mobile":"15800001111",
	"vcode":"123"
}
```

#### 返回示例
```
{
    "state": 0,
    "msg": "手机验证成功"
}
```

##### 返回参数说明

| 参数 | 含义 | 说明 |
| --- | --- | --- |
| error | 错误代码 |  |
| msg | 错误消息 |  |

##### 抛出异常
* User not login - 用户未登录
* params invalid - 参数无效
* mobile invalid - 旧密码无效
* verify code invalid - 旧密码无效

---

## 问题控制器（DataQuestionController） 

### 获取问题列表

#### 简要描述
* 获取问题列表

#### 请求URL
* /api/dataQuestion/getQuestionList

##### 请求方式
* POST

##### 请求参数

| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| page_number | 选填 | int | 页码 ，默认1 |
| page_size | 选填 | int | 数量，默认5条 |

#### 请求示例
```
{	
	"page_number":1,
	"page_size":5
}
```

#### 返回示例
```
{
  "7": {
    "id": 7,  # 问题ID
    "type": 1, # 问题类型
    "question": "您买房的主要用途是什么？（多选）", #问题
    "answer_list": [  # 答案列表
      {
        "id": 2,
        "question_id": 7, # 答案ID
        "answer": "别墅", # 答案
        "order_id": 3, # 答案排序
        "deleted": false
      },
      {
        "id": 3,
        "question_id": 7,
        "answer": "投资出租",
        "order_id": 2,
        "deleted": false
      }
    ],
    "order_id": 1,  # 问题排序
    "deleted": false
  },
  "9": {
    "id": 9,
    "type": 1,
    "question": "测试问题1",
    "order_id": 100,
    "deleted": false
  }
}
```

##### 抛出异常
* 无

---

## 用户回答（UserAnswerController） 

### 保存用户回答

#### 简要描述
* 保存用户的回答

#### 请求URL
* /api/userAnswer/saveUserAnswer

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 必填 | string | 用户token |
| question_id | 必填 | int | 问题ID |
| answer_list | 必填 | array | 答案列表 |
| id | 必填 | 必填 | int | 答案ID | 
| order_id | 选填 | int | 答案排序 |

#### 请求示例

```
{
  "token" : "0falsdjfk3rj", 
  "list":{   # 回答列表
	  	"0": {
	    "question_id": 1,   # 问题ID
	    "answer_list": [    # 答案列表
	      {
	        "id": 2,        # 答案ID
	        "order_id":1    # 答案排序
	      },
	      {
	        "id": 3
	      }
	    ]
	  },
	  "1": {                # 另一个问题
	    "question_id": 2,
	    "answer_list": [
	      {
	        "id": 2
	      },
	      {
	        "id": 3
	      }
	    ]
	  }
  }
}
```


#### 返回示例
```
{
  "state": 1,
  "msg": "record user answer success",
  "msg_desc": "记录用户回答成功"
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 获取当前用户的回答

#### 简要描述
* 获取用户的回答

#### 请求URL
* /api/userAnswer/getUserAnswer

##### 请求方式
* POST

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 是 | string | 用户token |

#### 请求示例
```
{
	"token":"802385eee2f7f8670e0992518795bfa065c42633d635ef816a009d0f6b0f0377"
}
```

#### 返回示例 
```
{
  "state": 1, # 状态
  "result": {  # 返回结果集
    "1": {
      "question": "问题一",  # 问题
      "question_id": 1, # 问题ID
      "answer_list": [ # 答案列表
        {
          "answer_id": 3,  # 答案ID
          "answer_info": "投资出租", # 答案
          "order_id": 0 # 排序 
        },
        {
          "answer_id": 2,
          "answer_info": "别墅",
          "order_id": 1
        }
      ]
    },
    "2": {
      "question": "问题二",
      "question_id": 2,
      "answer_list": [
        {
          "answer_id": 2,
          "answer_info": "别墅",
          "order_id": 0
        },
        {
          "answer_id": 3,
          "answer_info": "投资出租",
          "order_id": 0
        }
      ]
    }
  }
}
```

##### 返回参数说明
| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| state | int | 0：失败、1：成功 |
| question | string | 问题标签 | 
| question_id | int | 问题ID |
| answer_list | array | 答案列表 |
| answer_id | int | 答案ID |
| answer_info | string | 答案内容 |
| order_id | int | 答案排序 |

##### 抛出异常
* 无

---

## UserDownloadController 用户下载控制器

```
· 这里的表结构保存对象不仅仅是ID，而是obj_type、obj_id，方便以后扩展下载不同类型数据。
```

### 保存用户下载记录

#### 简要描述
* 记录用户轨迹-下载记录

#### 请求URL
* /api/userDownload/saveUserDownload

##### 请求方式
* POST

##### 请求参数

| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| obj_id | 否 | int | 对象ID |
| type | 是 | int | 对象类型：0（查询报告）、1（新房）、2（二手房）、 |
| q | 是 | string | 参数 |

#### 请求示例
```
{
  "token" : "a7698d6771ea4f967ee4f177881f78ff384b1b92790d815831828c94ea7bb030",
  "obj_id":1,
  "type":1
}
```

#### 返回示例
```
{
  "state": 1,
  "msg": "download record success",
  "msg_desc": "下载记录成功"
}
```

##### 返回参数说明

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| state | int | 状态 - 0：失败、1：成功 |
| msg | string | 英文消息 | 
| msg_desc | string | 中文消息 |

##### 抛出异常
* 无


---

### 获取用户下载数据

#### 简单描述
* 获取用户下载数据

#### 请求URL
* /api/userDownload/getUserDownload

##### 请求方式
* POST

##### 请求参数 

| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| page_number | 否 | int | 页码 - 默认1 |
| page_size | 否 | int | 数量 - 默认5条 |

#### 请求示例
```
{
  "token" : "a7698d6771ea4f967ee4f177881f78ff384b1b92790d815831828c94ea7bb030"
}
```

#### 返回示例

```
{
  "state": 1,
  "result": [
    {
      "id": 8, # 用户下载关联ID
      "obj_id": 1, # 对象ID
      "obj_type": 1, # 对象类型
      "time_add": "2017-04-20T22:42:15+0800", # 下载时间
      "description": "这是报告1" # 下载标题
    }
  ]
}
```

##### 返回参数说明
| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| state | int | 状态 - 0：失败、1：成功 |
| obj_id | int | 下载对象ID | 
| time_add | date | 下载时间 |
| description | string | 下载文件描述 |

##### 抛出异常
* 无

---

## UserViewController 用户浏览控制器
```
· 这里的表结构保存对象不仅仅是ID，而是obj_type、obj_id，方便以后扩展下载不同类型数据。
```

### 保存用户浏览记录

#### 简要描述
* 记录用户轨迹-浏览房源详情信息

#### 请求URL
* /api/userView/saveUserView

##### 请求方式
* POST

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| obj_id | 是 | int | 对象ID |
| obj_type | 否 | int | 对象类型 - 默认：1（subdivision）, 2（home） |
| q | 否 | string | 参数 |

#### 请求示例
```
{
  "token" : "a7698d6771ea4f967ee4f177881f78ff384b1b92790d815831828c94ea7bb030",
  "obj_id":1,
  "obj_type":1
}
```

#### 返回示例
```
{
  "state": 1,
  "msg": "view record success",
  "msg_desc": "记录浏览成功"
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 获取用户浏览数据

#### 简要描述
* 获取用户浏览数据 
 
#### 请求URL
* /api/userView/getUserView
 
##### 请求方式
* POST

##### 请求参数 

| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| page_number | 否 | int | 页码 - 默认1 |
| page_size | 否 | int | 数量 - 默认5条 |

#### 请求示例
```
{
  "token" : "a7698d6771ea4f967ee4f177881f78ff384b1b92790d815831828c94ea7bb030",
  "page_number:1,
  "page_size"1
}
```

#### 返回示例

```
{
  "state": 1,   # 状态
  "result": [
    {
      "id": 8,
      "obj_type": 2,  # obj_type = 2 是 home
      "obj_id": 1,
      "time_add": "2017-04-20T23:10:19+0800",
      "home_name": "这是home" # 名称
    },
    {
      "id": 7,
      "obj_type": 1,    # obj_type = 1 是 subdivision
      "obj_id": 1,
      "time_add": "2017-04-20T23:07:08+0800",
      "subdivision_name": "项目一" # 名称
    }
  ]
}
```

##### 返回参数说明

| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| state | int | 状态 - 0：失败、1：成功 |
| obj_id | int | 浏览对象ID |
| obj_type | int | 浏览对象类型 ：1（subdivision）, 2（home） |
| time_add | date | 时间 |
| home_name | string | 二手房名称 |
| subdivision_name | string | 新房名称 |

##### 抛出异常
* 无

---

## UserFavController 用户收藏控制器

### 保存用户收藏记录

#### 简要描述
* 记录用户收藏轨迹

#### 请求URL
* /api/userFav/saveUserFav

##### 请求方式
* POST

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| obj_id | 是 | int | 对象ID |
| obj_type | 否 | int | 对象类型 - 默认：1（subdivision）, 2（home） |
| q | 否 | string | 参数 |

#### 请求示例
```
{
  "token" : "a7698d6771ea4f967ee4f177881f78ff384b1b92790d815831828c94ea7bb030",
  "obj_id":1,
  "obj_type":1
}
```

#### 返回示例
```
{
  "state": 1,
  "msg": "favorite success",
  "msg_desc": "收藏成功"
}
```

#### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 取消收藏

#### 简要描述
* 用户取消收藏

#### 请求URL
* /api/userFav/cancelUserFav

##### 请求方式
* POST

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| obj_id | 是 | int | 对象ID |
| obj_type | 否 | int | 对象类型 - 默认：1（subdivision）, 2（home） |
| q | 否 | string | 参数 |

#### 请求示例
```
{
  "token" : "a7698d6771ea4f967ee4f177881f78ff384b1b92790d815831828c94ea7bb030",
  "obj_id":1,
  "obj_type":1
}
```

#### 返回示例
```
{
  "state": 1,
  "msg": "cancel favorite success",
  "msg_desc": "取消收藏成功"
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 获取用户收藏

#### 简要描述
* 获取用户收藏

#### 请求URL
* /api/userFav/getUserFav

##### 请求方式
* POST

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| page_number | 否 | int | 页码 - 默认1 |
| page_size | 否 | int | 数量 - 默认5条 |
| only_id | 否 | boolean | 是否只返回ID |

#### 请求示例
```
{
  "token" : "a7698d6771ea4f967ee4f177881f78ff384b1b92790d815831828c94ea7bb030",
  "page_number:1,
  "page_size"1,
  "only_id":true
}
```

#### 返回示例

```
{
  "state": 1,
  "result": [
    {
      "id": 24,
      "obj_id": 1,
      "obj_type": 1,
      "time_add": "2017-04-20T23:15:28+0800",
      "subdivision_name": "项目一"
    },
    {
      "id": 23,
      "obj_id": 1,
      "obj_type": 2,
      "time_add": "2017-04-20T23:15:23+0800",
      "home_name": "这是home"
    }
  ]
}
```

##### 返回参数说明
| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| state | int | 状态 - 0：失败、1：成功 |
| obj_id | int | 收藏 对象ID |
| obj_type | int | 收藏 对象类型 ：1（subdivision）, 2（home） |
| time_add | date | 时间 |
| home_name | string | 二手房名称 |
| subdivision_name | string | 新房名称 |

##### 抛出异常
* 无

---

### 房源状态变更提醒

#### 简要描述
* 房源有变动时调用该API,通过微信模板提醒用户

#### 请求URL
* /api/userFav/changeStatus

##### 请求方式
* POST

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| obj_id | 是 | array | 对象ID |
| obj_type | 是 | int | 对象类型 1（subdivision）、2（home） |
| url | 是 | string | 跳转url |
| template_id | 是 | string | 微信模板id |
| data | 是 | array | 模板数据，对应微信模板中的设置 |

#### 请求示例
```
{
  "obj_id": ["MRIS_120958827401"],
  "obj_type": 2,
  "url": "http://fang88.me/app/listingDetail?lid=MRIS_120958827401&isNewHouse=false",
  "template_id": "1S3VRH5pc7It6sCVZWoTHwuxpP7Qm_0s3xzCwrWCwe4",
  "data": {"first": {"value": "为您找到一处房源。"}, "keyword1": {"value": "2300sqft"}, "keyword2": {"value": "1200000"}, "remark": {"value": "感谢您的信赖，我们将一如既往的为您服务！。"}}
}
```

#### 返回示例
```
{
  "state": 1,
  "msg": "notice success",
  "msg_desc": "提醒成功"
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 获取用户收藏的文章

#### 简要描述
* 获取用户收藏的文章

#### 请求URL
* /api/userFav/getUserFavWeArticle

##### 请求方式
* POST

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| page_number | 否 | int | 页码 - 默认1 |
| page_size | 否 | int | 数量 - 默认5条 |
| only_id | 否 | boolean | 是否只返回ID |

#### 请求示例
```
{
  "token" : "a7698d6771ea4f967ee4f177881f78ff384b1b92790d815831828c94ea7bb030",
  "page_number:1,
  "page_size"1,
  "only_id":true
}
```

#### 返回示例

```
[
    {
        "id": 5029,
        "unique_id": "e3c565954f74473aa2868f2",
        "fix_top": 0,
        "cover_image_path": "bff997f452637358f2ed4e667e0c68d06.jpg",
        "title": "在美国参加婚礼如何送礼物？这些东西最糟糕！",
        "abstract": "在美国，参加亲朋好友婚礼的传统和中国略有不同，当你收到婚礼请帖的时候，同时也会收到新人整理出的“新婚礼物愿望清单”。新婚夫妇们会列出一些他们新生活所需的用品，让参加婚礼的亲朋好友按能力所及选择赠送。但是，为什么不少夫妇却对自己要求的礼物感到越来越厌烦呢？",
        "publish_time": "2017-06-29T12:49:08+0000",
        "total_visit_count": 5855,
        "tags": [
            "生活",
            "娱乐",
            "攻略"
        ]
    }
]
```

##### 返回参数说明
| 参数名 | 类型 | 说明 |
| --- | --- | --- |
| state | int | 状态 - 0：失败、1：成功 |
| obj_id | int | 收藏 对象ID |
| obj_type | int | 收藏 对象类型 ：1（subdivision）, 2（home） |
| time_add | date | 时间 |
| home_name | string | 二手房名称 |
| subdivision_name | string | 新房名称 |

##### 抛出异常
* 无

---


## UserSearchController 用户搜索控制器

### 保存用户搜索词

#### 简要描述
* 记录用户搜索轨迹
* 搜索词会放在在词库（DataSearchWord），重复搜索词nums会+1

#### 请求URL
* /api/userSearch/saveUserSearch

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| word | 是 | string | 搜索词 |
| q | 否 | string | 参数 |

#### 请求示例
```
{
  "token" : "a7698d6771ea4f967ee4f177881f78ff384b1b92790d815831828c94ea7bb030",
  "word":"aaa"
}
```

#### 返回示例
```
{
  "state": 1,
  "msg": "record user search word success",
  "msg_desc": "记录用户搜索成功"
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 获取用户搜索词

#### 简要描述
* 获取用户搜索记录

#### 请求URL
* /api/userSearch/getUserSearch

##### 请求方式
* POST

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| page_number | 否 | int | 页码 - 默认1 |
| page_size | 否 | int | 数量 - 默认5条 |

#### 请求示例
```
{
  "token" : "a7698d6771ea4f967ee4f177881f78ff384b1b92790d815831828c94ea7bb030"
}
```

#### 返回示例

```
{
  "state": 1,
  "result": [
    {
      "user_id": 32,
      "word": "test", # 用户搜索词
      "username": "dod001"
    }
  ]
}
```

##### 返回参数说明
| 参数 | 类型 | 说明 |
| --- | --- | --- |
| user_id | int | 用户ID |
| word | string | 搜索关键词 | 
| username | string | 用户名 | 

##### 抛出异常
* 无

---

### 获取系统搜索词

#### 简要描述
* 获取系统搜索词

#### 请求URL
* /api/userSearch/hot_keywords

##### 请求方式
* POST

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| page_number | 否 | int | 页码 - 默认1 |
| page_size | 否 | int | 数量 - 默认10条 |

#### 请求示例
```
{
  "page_number" : 1,
  "page_size" : 10
}
```

#### 返回示例

```
[
    {
        "id": 1,
        "word": "test",
        "nums": 5
    }
]
```

##### 返回参数说明
| 参数 | 类型 | 说明 |
| --- | --- | --- |
| id | int | 关键词ID |
| word | string | 关键词 | 
| nums | ing | 搜索次数 | 

##### 抛出异常
* 无

---


## WinxinController 微信控制器

### 微信推送模板消息

#### 简要描述
* 推送微信模板消息接口

#### 请求URL
* /api/weixin/pushMsg

##### 请求方式
* POST

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| url | 是 | string | 链接,点开消息详情打开 |
| openid | 是 | string | 用户微信openid | 
| template_id | 是 | string | 模板消息,在服务号中设置获取 |
| data | 是 | array|  消息对应数据 | 

#### 发送参数示例
```
{
  "openid": "og0yav4BnkdQSPFh5nH3WZzcVG7o",
  "template_id": "QaoDI5k6wDdvyIx4tkV7Sh4auKKswULtIjCHENnVnu8",
  "url": "http://www.google.com",
  "data": {
    "a": {
      "value": "this a",    // 内容
      "color": "#173177"    // 这是字体颜色
    },
    "b": {
      "value": "this b",
      "color": "#173177"
    },
    "c": {
      "value": "this c",
      "color": "#173177"
    }
  }
}
```

#### 公众号设置示例

```
这是内容A：{{a.DATA}}
这是内容B：{{b.DATA}}
这是内容C：{{c.DATA}}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 小程序登录

#### 简要描述
* 根据小程序的code请求微信
* 返回openip、session_key
* 这里操作请求微信返回openid和判断openid是否注册过

#### 请求URL
* /api/weixin/appLogin

##### 请求方式
* POST

#### 请求示例
```
{
	"code":"test"
}
```

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| code | 是 | string | 小程序从微信请求回来 |

#### 返回示例
```
{
	"openid":"openid",
	"session_key":"session_key",
	"user":"user"  // 用户对象数据，如果是空数组说明用户没注册过
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

---

### 小程序注册

#### 简要描述
* 小程序请求微信获取用户信息
* 如果用户拒绝，则随机生成用户名

#### 请求URL
* /api/weixin/appRegister

##### 请求方式
* POST

#### 请求示例
```
{
	"openid":"openid",
	"unionid":"unionid", 
	"username":"username",
	"mobile":"mobile",
	"email":"email",
	"avatar":"avatar"
}
```

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| openid | 是 | string | 小程序openid，不是公众号openid |
| unionid | 是 | string | 开放平台unionid，可关联公众号、小程序 |
| username | 否 | string | 微信用户名 |
| email | 否 | string | 邮箱 |
| mobile | 否 | string | 手机 |
| avatar | 否 | string | 头像 |
| province | 否 | string | 省份 |
| city | 否 | string | 城市 |

#### 返回示例
```
{
	"id":"id",
	"username":"username",
	"avatar":"avatar",
	"token":"token",
	"openid":"openid",
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

---


## UserTrackController 用户轨迹

### 记录用户轨迹

#### 简要描述
* 记录用户轨迹
* 用户浏览、用户收藏、用户下载、用户搜索 这几个事件已经有记录轨迹
* 如果还需另外记录轨迹则调用该API

#### 请求URL
* /api/userTrack/saveUserTrack

##### 请求方式
* POST

#### 请求示例
```
```

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 否 | string | 如果没有token则默认uid=0，即匿名用户 |
| action | 是 | string | 事件 |
| obj_id | 是| string | 对象ID | 
| obj_table | 是 | string | 对象表，用于后台展示对象的内容 |
| q | 否 | string| 参数 |
| user_temporary_id | 否 | string| 临时用户ID |

#### 返回示例
```
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

---

## QuestionMasterController 问题控制器

```
· 问题相关操作
```

### 新增问题

#### 简要描述
* 新增问题、问题标签、轨迹记录

#### 请求URL
* /api/questionMaster/doAddQuestion

##### 请求方式
* POST

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| title | 是 | string | 问题标题 |
| content | 否 | string | 问题内容 |
| tags | 否 | string | 问题标签 |
| is_anonymity | 否 | int | 是否匿名 |

#### 请求示例
```
{
	"content":"内容",
	"title":"标题",
	"tags":[
		"标签一",
		"标签二"
	]
}
```

##### 请求参数


#### 返回示例
```
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 更新问题

#### 简要描述
* 更新问题及相关操作

#### 请求URL
* /api/questionMaster/doUpdateQuestion

##### 请求方式
* POST

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| question_id | 问题ID | 必填 |
| title | 问题标题 | 必填 |
| content | 问题内容 | 选填 |
| tags | 问题标签 | 选填 |

#### 请求示例
```
{
    "question_id":"1",
	"content":"内容",
	"title":"标题",
	"tags":[
		"标签一",
		"标签二"
	]
}
```

##### 请求参数

#### 返回示例
```
```

##### 返回参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 关注问题

#### 简要描述
* 关注问题、取消关注

#### 请求URL
* /api/questionMaster/followQuestion

##### 请求方式
* POST

#### 请求示例
```
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| question_id | 问题ID | 必填 |
| type | 类型 | 必填；1：关注、2：取消关注 |

#### 返回示例
```
```

##### 返回参数 
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 问题列表

#### 简要描述
* 获取问题列表

#### 请求URL
* /api/questionMaster/questionList

##### 请求方式
* POST

#### 请求示例
```
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| page_number | 页码 | 必填，默认1 |
| page_size | 每页数量 | 必填，默认20 |

#### 返回示例
```
{
  "page_number": 1, // 当前页码
  "page_size": 20, // 当前每页数量
  "count": 3, // 总数据
  "list": [   // 问题列表
    {
      "question_id": 6,
      "question_user_id": 11,
      "question_title": "这是问题二的标题之修改版",
      "question_content": "这是问题二的内容之修改版",
      "question_tags": "修改,更新",
      "is_anonymity": false,
      "question_time_add": "2017-06-15T03:47:14+0000",
      "is_top": true,
      "time_top": "2017-06-21T09:16:39+0000",
      "question_cnt_follow": 1,
      "question_cnt_answer": 7,
      "question_cnt_share": 2,
      "question_author_username": "方块七",
      "question_author_avatar": "http://wx.qlogo.cn/mmopen/xMwtEJibGa8aUicIudlGAYh0wuq0ty3Jy3QFLeFIUnB0SWHPzxfibcdaOgVbma0Kibtec8k7axGaxaCSoqnib9Ribic7EqHsMzHqk0r/0"
    }
  ]
}
```

##### 返回参数说明


##### 抛出异常
* 无

---

### 用户提问列表

#### 简要描述
* 获取用户提问列表

#### 请求URL
* /api/questionMaster/userQuestionList

##### 请求方式
* POST

#### 请求示例
```
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| page_number | 页码 | 必填，默认1 |
| page_size | 每页数量 | 必填，默认20 |

#### 返回示例
```
{
  "page_number": 1, // 当前页码
  "page_size": 20, // 当前每页数量
  "count": 3, // 总数据
  "list": [   // 问题列表
    {
      "question_id": 16,
      "question_user_id": 11,
      "question_title": "测试问题",
      "question_content": "",
      "question_tags": "",
      "is_anonymity": false,
      "question_cnt_follow": 1,
      "question_cnt_answer": 7,
      "question_cnt_share": 2,
      "question_time_add": "2017-06-29T09:31:29+0000",
      "question_author_username": "方块七",
      "question_avatar": "http://wx.qlogo.cn/mmopen/xMwtEJibGa8aUicIudlGAYh0wuq0ty3Jy3QFLeFIUnB0SWHPzxfibcdaOgVbma0Kibtec8k7axGaxaCSoqnib9Ribic7EqHsMzHqk0r/0"
    },
  ]
}
```

##### 返回参数说明


##### 抛出异常
* 无

---

### 用户关注的问题

#### 简要描述
* 获取用户关注的问题列表

#### 请求URL
* /api/questionMaster/userFollowQuestionList

##### 请求方式
* POST

#### 请求示例
```
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| page_number | 页码 | 选填，默认1 |
| page_size | 每页数量 | 选填，默认20 |

#### 返回示例
```
{
  "page_number": 1, // 当前页码
  "page_size": 20, // 当前每页数量
  "count": 3, // 总数据
  "list": [   // 问题列表
    {
      "follow_time": "2017-06-15T05:28:09+0000",
      "question_id": 5,
      "question_user_id": 11,
      "question_title": "这是问题一的标题",
      "question_content": "这是问题一的内容",
      "question_tags": "测试,问题",
      "is_anonymity": false,
      "question_time_add": "2017-06-15T03:36:51+0000",
      "question_cnt_follow": 1,
      "question_cnt_answer": 7,
      "question_cnt_share": 2,
      "question_author_username": "方块七",
      "question_author_avatar": "http://wx.qlogo.cn/mmopen/xMwtEJibGa8aUicIudlGAYh0wuq0ty3Jy3QFLeFIUnB0SWHPzxfibcdaOgVbma0Kibtec8k7axGaxaCSoqnib9Ribic7EqHsMzHqk0r/0"
    }
  ]
}
```

##### 返回参数说明


##### 抛出异常
* 无

---

### 问题详情

#### 简要描述
* 获取问题详情

#### 请求URL
* /api/questionMaster/getQuestion

##### 请求方式
* POST

#### 请求示例
```
{
	"token":"test_ccy_token",
	"question_id":5
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 |
| --- | --- | --- | --- |
| question_id | 是 | int | 问题id | 

#### 返回示例
```
{
  "state": 1,
  "question": {
    "id": 9,
    "user_id": 11,
    "title": "fang88美国地产",    // 问题标签
    "content": "美国房地产数据专家",   // 问题内容
    "tags": "纽约,西雅图",   // 问题标签
    "time_add": "2017-06-16T07:30:53+0000", // 提问时间
    "time_upd": "2017-06-16T07:30:53+0000", // 更新时间
    "cnt_hits": 5, // 阅读数
    "cnt_follow": 1, // 关注人数
    "cnt_share": 1, // 分享数
    "cnt_answer": 1,  // 回答数
    "seo_title": "seo title", // seo标题
    "seo_description": "seo desc", // seo描述
    "seo_keywords": "seo keywords",  // seo关键词
    "is_anonymity": false,
    "deleted": false
  },
  "author": {
    "id": 11,
    "username": "方块七",   // 提问者用户名
    "avatar": "http://wx.qlogo.cn/mmopen/xMwtEJibGa8aUicIudlGAYh0wuq0ty3Jy3QFLeFIUnB0SWHPzxfibcdaOgVbma0Kibtec8k7axGaxaCSoqnib9Ribic7EqHsMzHqk0r/0"   // 提问者头像
  }
}
```

##### 返回参数说明


##### 抛出异常
* GENERAL_101 - Question id is empty 问题ID不能为空
* GENERAL_101 - Question not exist 问题不存在
* Question is deleted 问题已删除

---

### 热门问题

#### 简要描述
* 关注度最多的问题

#### 请求URL
* /api/questionMaster/followQuestionList

##### 请求方式
* POST

#### 请求示例
```
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| page_number | 页码 | 必填，默认1 |
| page_size | 每页数量 | 必填，默认20 |

#### 返回示例
```
{
  "page_number": 1,
  "page_size": 20,
  "count": 8,
  "list": [
    {
      "question_id": 9,
      "question_user_id": 11,
      "question_title": "fang88美国地产",
      "question_content": "美国房地产数据专家",
      "question_tags": "纽约,西雅图",
      "is_anonymity": false,
      "question_time_add": "2017-06-16T07:30:53+0000",
      "is_top": false,
      "question_cnt_hits": 5,
      "question_follow": 1,
      "question_cnt_answer": 1,
      "question_cnt_share": 1,
      "question_author_username": "方块七",
      "question_author_avatar": "http://wx.qlogo.cn/mmopen/xMwtEJibGa8aUicIudlGAYh0wuq0ty3Jy3QFLeFIUnB0SWHPzxfibcdaOgVbma0Kibtec8k7axGaxaCSoqnib9Ribic7EqHsMzHqk0r/0"
    }
  ]
}
```

##### 返回参数说明


##### 抛出异常
* 无

---

### 搜索问题

#### 简要描述
* 搜索问题

#### 请求URL
* /api/questionMaster/searchQuestion

##### 请求方式
* POST

#### 请求示例
```
{
	"kw":"测试",
	"question_id":16
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| kw | 是 | string | 搜索关键词 |
| question_id | 否 | int | 当前问题id |

#### 返回示例
```
{
  "state": 1,
  "result": [
    {
      "id": "9",
      "user_id": 11,
      "title": "fang88美国地产",
      "content": "美国房地产数据专家",
      "tags": "纽约,西雅图",
      "time_add": "2017-06-16T07:30:53+0000",
      "time_upd": "2017-06-16T07:30:53+0000",
      "cnt_hits": 5,
      "cnt_follow": 1,
      "cnt_share": 1,
      "cnt_answer": 1,
      "seo_title": "seo title",
      "seo_description": "seo desc",
      "seo_keywords": "seo keywords",
      "is_top": false,
      "is_anonymity": false,
      "deleted": false
    }
  ]
}
```

##### 返回参数说明
| 参数 | 类型 | 说明 |
| --- | --- | --- |
| id | int | 问题id |
| user_id | int | 用户ID |
| title | string | 问题标题 |
| content | string | 问题内容 |
| tags | string | 问题标签,以「,」号分隔 |
| time_add | datetime | 添加时间 |
| time_upd | datetime | 更新时间 |
| time_top | datetime | 置顶时间 |
| cnt_hits | int | 浏览数 |
| cnt_follow | int | 关注数 |
| cnt_share | int | 分享数 |
| cnt_answer | int | 回答数 |
| seo_title | string | seo title |
| seo_description | string | seo description |
| seo_keywords | string | seo keywords |
| is_top | boolean | 是否置顶 |
| is_anonymity | boolean | 是否匿名 |
| deleted | boolean | 删除标识 | 


##### 抛出异常
* 无

---

### 举报问题

#### 简要描述
* 举报问题

#### 请求URL
* /api/questionMaster/doReport

##### 请求方式
* POST

#### 请求示例
```
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| question_id | 问题ID | 必填 |
| type | 举报类型 | 必填 |
| reason | 举报原因 | 选填 |

#### 返回示例
```
```

#### 返回参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 推荐房源

#### 简要描述
* 针对某个问题推荐相关房源

#### 请求URL
* /api/questionMaster/getRecommendHome

##### 请求方式
* POST

#### 请求示例
```
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| question_id | 问题ID | 必填 |

#### 返回示例
```
{
  "state": 1,
  "result": [
    {
      "id": 4,
      "question_id": 6,
      "home_type": 2,
      "home_url": "http://fang88.me/app/listingDetail?lid=BDX_46062_112006&isNewHouse=true",
      "home_id": "BDX_46062_112006",
      "time_add": "2017-06-27T16:48:22+0000",
      "deleted": false,
      "obj": {
        "id": 1917796,
        "address": "2105 100th St.",
        "amenity": "",
        "appendix": "null",
        "area": "Lubbock",
        "builder": " Addison Homes",
        "bdx_id": "112006",
        "bdx_website": "http://www.newhomesourceprofessional.com/communitydetail/builder-46062/community-112006",
        "builder_website": "http://addisonhomestx.com/available-homes/",
        "city": "Lubbock",
        "country": "USA",
        "email": "cassier@addisonhomestx.com",
        "english_description": "Begin the journey of creating your dream home at Fox Ridge in Lubbock, Texas. Begin with a lot of land and customize everything from the ground up.\n\nFox Ridge has no competitors when it comes to its stellar location. Located within the Cooper School District, Fox Ridge puts you just steps away from giving your children a bright education for the future. Love to enjoy life? Fox Ridge is mere minutes away from some of the best shopping and restaurants Lubbock has to offer. And you can’t beat the convenience with easy access to downtown, I-27, and Texas Tech University.",
        "english_name": "Fox Ridge",
        "location_latitude": "33.5030340",
        "location_longitude": "-101.8617010",
        "photos": [],
        "photo_json": [
          {
            "path": "b815f6c839c892db9f76408587b5b611.jpg"
          },
          {
            "path": "ecfcd6fd6ef6850f38cd288ae30fbc1e.jpg"
          },
          {
            "path": "c7064f2d885babf0198911be84e6398e.jpg"
          }
        ],
        "plans": {
          "BDX_PLAN_1403322": {
            "appendix": "null",
            "bathrooms": "2.00",
            "bdx_id": "1403322",
            "bedrooms": "3.0",
            "current_list_price": 0,
            "english_description": "Our 1600 sq ft plan offers 3 bedrooms and 2 bathrooms in an open concept floor plan.. Your family and friends will enjoy gathering in the spacious great room with room to spare. The master suite completes this plan with a double vanity, separate walk-in shower, luxurious garden tub and a large master closet.",
            "english_name": "Plan 1600",
            "min_price": 0,
            "photos": [],
            "photo_json": "[{\"path\":\"93eee0c94e465ec3d7a1c71375024cce.jpg\"},{\"path\":\"9a578cc1186263f6d0b5f520e43bf79d.jpg\"},{\"path\":\"efa9ec05c3f22bd9baa3d5923de9b65e.jpg\"},{\"path\":\"25a952ff3bf19b93571ebcbc7e363e60.jpg\"}]",
            "property_type": "RESI",
            "source": "BDX",
            "status": "A",
            "unique_id": "BDX_PLAN_1403322",
            "updated_at": "2017-07-03T18:21:41+0800",
            "fav_users": []
          }
        },
        "property_type": "RESI",
        "schools": [
          {
            "district_name": "",
            "grade_range": "PK-8",
            "id": 20103,
            "lat": "33.5015560",
            "lon": "-101.8845500",
            "name": "All Saints Episcopal School",
            "overview_link": "http://www.greatschools.org/texas/lubbock/7526-All-Saints-Episcopal-School/?s_cid=gsapi",
            "type": "private",
            "unique_id": "01327502"
          }
        ],
        "school_score": 9,
        "source": "BDX",
        "state": "TX",
        "unique_id": "BDX_46062_112006",
        "updated_at": "2017-07-03T18:21:41+0800",
        "zip": "79423",
        "plans_count": 2,
        "plan_bathrooms_max": "2.00",
        "plan_bathrooms_min": "2.00",
        "plan_bedrooms_max": "3.0",
        "plan_bedrooms_min": "3.0",
        "plan_current_list_price_max": 0,
        "plan_current_list_price_min": 0,
        "total_visit_count": 13,
        "fix_top": 0
      }
    }
    }
  ]
}
```

##### 返回参数说明
| 参数名 | 类型 | 说明 |
| --- | --- | --- | 
| area | string | 所属城市圈 |
| address | string | 街道地址 |
| appendix | string | 额外数据 |
| bathrooms | float | 浴室数 |
| bedrooms | int | 卧室数 |
| city | string | 城市 |
| close_price | int | 成交价格 |
| current_list_price | int | 挂牌价格 |
| description | string | 房源描述 |
| estimated_monthly_rent | int | 预计月租金 |
| estimated_yearly_return | float | 预计年回报率 |
| garage | int | 车库数 |
| hoa | int | 物业费 |
| listing_company | string | 挂牌公司 |
| listing_name | string | 挂牌中介名字 |
| listing_email | string | 挂牌中介邮件 |
| listing_phone | string | 挂牌中介电话 |
| list_date | datetime | 挂牌日期, UTC时间 |
| location_latitude | float | 纬度 |
| location_longitude | float | 经度 |
| lot_sqft | int | 占地面积 |
| mls_number | string | MLS号码 |
| openhouses | array | 开放日 |
| photo_json | string | 图片JSON |
| property_type | string | 房产类型 |
| schools | array | 学校 |
| school_score | int | 学校分数 |
| sqft | int | 平方英尺数 |
| sqft_price | int | 单位面积价格 |
| source | string | 来源 |
| state | string | 州 |
| status | string | 状态 |
| stories | int | 楼层数 |
| unique_id | string | 唯一ID |
| updated_at | datetime | 更新时间, UTC时间 |
| year_built | int | 建筑时间 |
| zip | string | 邮编 |

##### 抛出异常
* 无

---

### 保存图片

#### 简要描述
* 保存文本框中的图片

#### 请求URL
* /api/questionMaster/saveImage

##### 请求方式
* POST

#### 请求示例
```
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| image | 图片base64格式数据 | 必填 |

#### 返回示例
```
{
  "name": "7bf07a7ddf3917c505b0d0554d699e68.jpeg",
  "file": "http://images-cn.fang88.com/7bf07a7ddf3917c505b0d0554d699e68.jpeg"
}
```

##### 返回参数说明


##### 抛出异常
* 无

---

### 删除问题

#### 简要描述
* 前台删除问题

#### 请求URL
* /api/questionMaster/doDel

##### 请求方式
* POST

#### 请求示例
```
{
	"token":"test_ccy_token",
	"question_id":5
}
```

##### 请求参数
| 参数 | 必填 | 含义 | 说明 |
| --- | --- | --- | --- |
| token | 是| 用户token |  |
| question_id | 是 | 问题ID |  |

#### 返回示例
```
{
  "state": 1,
  "msg": "deleted question success",
  "msg_desc": "删除问题成功"
}
```

##### 返回参数说明


##### 抛出异常
* 无

---

## QuestionAnswerController 回答控制器

```
· 回答相关操作
```

### 回答问题

#### 简要描述
* 保存回答

#### 请求URL
* /api/questionAnswer/saveAnswer

##### 请求方式
* POST

#### 请求示例
```
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| question_id | 问题ID | 必填 |
| content | 问题内容 | 必填 |

#### 返回示例
```
```

##### 返回参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 赞回答

#### 简要描述
* 赞回答

#### 请求URL
* /api/questionAnswer/upAnswer

##### 请求方式
* POST

#### 请求示例
```
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| answer_id | 问题ID | 必填 |
| type | 类型 | 选填，默认1。（1：赞、2：取消赞） |

#### 返回示例
```
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 踩回答

#### 简要描述
* 踩回答

#### 请求URL
* /api/questionAnswer/downAnswer

##### 请求方式
* POST

#### 请求示例

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| answer_id | 问题ID | 必填 |

#### 返回示例


##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 收藏回答

#### 简要描述
* 收藏回答

#### 请求URL
* /api/questionAnswer/favAnswer

##### 请求方式
* POST

#### 请求示例

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| answer_id | 问题ID | 必填 |
| type | 类型 | 必填；1：关注、2：取消关注 |

#### 返回示例

##### 返回参数说明 
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 分享回答

#### 简要描述
* 分享回答

#### 请求URL
* /api/questionAnswer/shareAnswer

##### 请求方式
* POST

#### 请求示例

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| answer_id | 问题ID | 必填 |

#### 返回示例

##### 返回参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 评论回答

#### 简要描述
* 评论回答

#### 请求URL
* /api/questionAnswer/commentAnswer

##### 请求方式
* POST

##### 请求示例


##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| answer_id | 问题ID | 必填 |
| content | 内容 | 必填 |
| reply_pid | 回复评论的ID | 选填 |

##### 返回示例


##### 返回参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 用户收藏的回答

#### 简要描述
* 用户收藏的回答

#### 请求URL
* /api/questionAnswer/userFavAnswer

##### 请求方式
* POST

####请求示例


##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| page_number | 页码 | 选填，默认1 |
| page_size | 每页数量 | 选填，默认20 |

#### 返回示例
```
{
  "page_number": 1,
  "page_size": 20,
  "count": 1,
  "list": [
    {
      "fav_time": "2017-06-18T16:01:48+0000",
      "answer_id": 1,
      "question_id": 6,
      "answer_content": "这是问题ID=6的回答一",
      "answer_author_username": "方块七",
      "answer_author_avatar": "http://wx.qlogo.cn/mmopen/xMwtEJibGa8aUicIudlGAYh0wuq0ty3Jy3QFLeFIUnB0SWHPzxfibcdaOgVbma0Kibtec8k7axGaxaCSoqnib9Ribic7EqHsMzHqk0r/0",
      "question_user_id": 11,
      "question_title": "这是问题二的标题之修改版",
      "question_content": "这是问题二的内容之修改版",
      "question_tags": "修改,更新",
      "question_time_add": "2017-06-15T03:47:14+0000",
      "question_up": 1,
      "question_cnt_answer": 1,
      "question_author_username": "方块七",
      "question_author_avatar": "http://wx.qlogo.cn/mmopen/xMwtEJibGa8aUicIudlGAYh0wuq0ty3Jy3QFLeFIUnB0SWHPzxfibcdaOgVbma0Kibtec8k7axGaxaCSoqnib9Ribic7EqHsMzHqk0r/0"
    }
  ]
}
```

##### 返回参数说明


##### 抛出异常
* 无

---

### 获取问题回答

#### 简要描述
* 获取问题回答

#### 请求URL
* /api/questionAnswer/getQuestionAnswer

##### 请求方式
* POST

#### 请求示例

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| question_id | 问题ID | 必填 |
| page_number | 页码 | 必填，默认1 |
| page_size | 每页数量 | 必填，默认20 |

#### 返回示例
```
{
  "question": {
    "id": 6,
    "user_id": 11,
    "title": "这是问题二的标题之修改版",
    "content": "这是问题二的内容之修改版",
    "tags": "修改,更新",
    "time_add": "2017-06-15T03:47:14+0000",
    "time_upd": "2017-06-15T03:57:46+0000",
    "cnt_follow": 1, // 关注问题人数
    "cnt_share": 2, // 分享问题人数
    "cnt_hits": 2, // 查看问题人数
    "cnt_answer": 2, // 回答问题人数
    "is_anonymity": false,
    "deleted": false
  },
  "page_number": 1,
  "page_size": 20,
  "count": 1,
  "answer_list": [
    {
      "content": "回答内容",
      "time_add": "2017-06-18T06:07:31+0000",
      "cnt_comment": 2,
      "cnt_up": 2,
      "cnt_down": 1,
      "cnt_fav": 3,
      "author_username": "方块七",
      "author_avatar": "http://wx.qlogo.cn/mmopen/xMwtEJibGa8aUicIudlGAYh0wuq0ty3Jy3QFLeFIUnB0SWHPzxfibcdaOgVbma0Kibtec8k7axGaxaCSoqnib9Ribic7EqHsMzHqk0r/0"
    }
  ]
}
```

##### 返回参数说明


##### 抛出异常
* 无

---

### 获取答案评论

#### 简要描述
* 获取答案评论

#### 请求URL
* /api/questionAnswer/getAnswerComment

##### 请求方式
* POST

#### 请求示例

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| answer_id | 回答ID | 必填 |
| page_number | 页码 | 必填，默认1 |
| page_size | 每页数量 | 必填，默认20 |

#### 返回示例
```
{
  "answer": {
    "id": 1,
    "user_id": 11,
    "question_id": 6,
    "content": "回答内容",
    "time_add": "2017-06-18T06:07:31+0000",
    "time_upd": "2017-06-18T06:07:31+0000",
    "cnt_comment": 2,
    "cnt_fav": 3,
    "cnt_share": 1,
    "cnt_up": 2,
    "cnt_down": 1,
    "deleted": false
  },
  "page_number": 1,
  "page_size": 20,
  "count": 2,
  "comment_list": [   // 评论列表
    {
      "content": "回答内容",   // 评论内容
      "time_add": "2017-06-18T16:57:17+0000",  // 评论时间
      "comment_username": "方块七",  // 评论用户名
      "comment_avatar": "http://wx.qlogo.cn/mmopen/xMwtEJibGa8aUicIudlGAYh0wuq0ty3Jy3QFLeFIUnB0SWHPzxfibcdaOgVbma0Kibtec8k7axGaxaCSoqnib9Ribic7EqHsMzHqk0r/0",  // 评论用户头像
      "reply_user_name": "方块七",   // 被回复者的用户名
      "reply_user_avatar": "http://wx.qlogo.cn/mmopen/xMwtEJibGa8aUicIudlGAYh0wuq0ty3Jy3QFLeFIUnB0SWHPzxfibcdaOgVbma0Kibtec8k7axGaxaCSoqnib9Ribic7EqHsMzHqk0r/0"  // 被回复者的头像
    },
    {
      "content": "回答内容",
      "time_add": "2017-06-18T16:51:37+0000",
      "comment_username": "方块七",
      "comment_avatar": "http://wx.qlogo.cn/mmopen/xMwtEJibGa8aUicIudlGAYh0wuq0ty3Jy3QFLeFIUnB0SWHPzxfibcdaOgVbma0Kibtec8k7axGaxaCSoqnib9Ribic7EqHsMzHqk0r/0"
    }
  ]
}
```

##### 返回参数说明

##### 抛出异常
* 无

---

### 举报答案

#### 简要描述
* 举报答案

#### 请求URL
* /api/questionAnswer/doReport

##### 请求方式
* POST

#### 请求示例


##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| answer_id | 答案ID | 必填 |
| type | 举报类型 | 必填 |
| reason | 举报原因 | 选填 |

#### 返回示例


##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---

### 用户回答的答案

#### 简要描述
* 用户回答的答案

#### 请求URL
* /api/questionAnswer/userAnswer

##### 请求方式
* POST

#### 请求示例

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| page_number | 页码 | 必填，默认1 |
| page_size | 每页数量 | 必填，默认20 |

#### 返回示例
```
{
  "page_number": 1,
  "page_size": 20,
  "count": 7,
  "list": [
    {
      "id": 6,
      "answer_content": "美国西雅图管理公司222",
      "answer_time_add": "2017-06-19T07:30:44+0000",
      "question_id": 5,
      "question_user_id": 11,
      "question_title": "这是问题一的标题",
      "question_content": "这是问题一的内容",
      "question_tags": "测试,问题",
      "question_time_add": "2017-06-15T03:36:51+0000",
      "question_follow": 1,
      "question_cnt_answer": 7,
      "question_cnt_share": 2,
      "question_author_username": "方块七",
      "question_author_avatar": "http://wx.qlogo.cn/mmopen/xMwtEJibGa8aUicIudlGAYh0wuq0ty3Jy3QFLeFIUnB0SWHPzxfibcdaOgVbma0Kibtec8k7axGaxaCSoqnib9Ribic7EqHsMzHqk0r/0"
    }
]
}
```

##### 返回参数说明

##### 抛出异常
* 无

---

### 举报评论

#### 简要描述
* 举报评论

#### 请求URL
* /api/questionAnswer/reportComment

##### 请求方式
* POST

#### 请求示例

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| comment_id | 答案ID | 必填 |
| type | 举报类型 | 必填 |
| reason | 举报原因 | 选填 |

#### 返回示例

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* 无

---
 
### 用户赞过的答案

#### 简要描述
* 用户赞过的答案

#### 请求URL
* /api/questionAnswer/userUpAnswer

##### 请求方式
* POST

#### 请求示例


##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| question_id | 问题ID | 必填 |

#### 返回示例
```
{
  "state": 1,
  "result": [
    {
      "answer_id": 1,
      "question_id": 6,
      "user_id": 11
    }
  ]
}
```

##### 返回参数说明


##### 抛出异常
* 无

---

### 更新答案内容

#### 简要描述
* 更新答案内容

#### 请求URL
* /api/questionAnswer/doUpdateAnswer

##### 请求方式
* POST

#### 请求示例
```
{
	"token":"test_ccy_token",
	"answer_id":3,
	"content":"测试一下修改内容。"
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| answer_id | 是 | int | 答案id |
| content | 是 | string | 答案内容 |

#### 返回示例
```
{
  "state": 1,
  "msg": "answer success",
  "msg_desc": "回答成功"
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* GENERAL_101 - User not login （用户未登录）
* GENERAL_101 - answer id is empty（回答id未传）
* GENERAL_101 - answer content is empty（回答内容不能为空）
* GENERAL_101 - Answer not exist（回答不存在,数据库中找不到该回答数据）
* GENERAL_101 - can't edit this answer（无法编辑该回答,原因是当前登录的用户与回答作者ID不同）

---

### 更新评论

#### 简要描述
* 更新问题回答的评论

#### 请求URL
* /api/questionAnswer/doUpdateComment

##### 请求方式
* POST

#### 请求示例
```
{
	"token":"test_ccy_token",
	"comment_id":3,
	"content":"测试一下修改内容。"
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 是 | string | 用户token |
| comment_id | 是 | int | 评论id |
| content | 是 | string | 评论内容 |

#### 返回示例
```
{
  "state": 1,
  "msg": "answer success",
  "msg_desc": "回答成功"
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

##### 抛出异常
* GENERAL_101 - User not login （用户未登录）
* GENERAL_101 - comment id is empty（评论id未传）
* GENERAL_101 - comment content is empty（回答内容不能为空）
* GENERAL_101 - comment not exist（评论不存在,数据库中找不到该评论数据）
* GENERAL_101 - can't edit this comment（无法编辑该评论,原因是当前登录的用户与评论作者ID不同）

---

### 删除答案

#### 简要描述
* 前台删除答案

#### 请求URL
* /api/questionMaster/doDelAnswer

##### 请求方式
* POST

#### 请求示例
```
{
	"token":"test_token",
	"answer_id":3
}
```

##### 请求参数
| 参数 | 必填 | 含义 | 说明 |
| --- | --- | --- | --- |
| token | 是| 用户token |  |
| answer_id | 是 | 答案ID |  |

#### 返回示例
```
{
  "state": 1,
  "msg": "deleted answer success",
  "msg_desc": "删除答案成功"
}
```

##### 返回参数说明


##### 抛出异常
* 无

---

### 删除评论

#### 简要描述
* 前台删除评论

#### 请求URL
* /api/questionMaster/doDelComment

##### 请求方式
* POST

#### 请求示例
```
{
	"token":"test_token",
	"comment_id":3
}
```

##### 请求参数
| 参数 | 必填 | 含义 | 说明 |
| --- | --- | --- | --- |
| token | 是| 用户token |  |
| comment_id | 是 | 评论ID |  |

#### 返回示例
```
{
  "state": 1,
  "msg": "deleted comment success",
  "msg_desc": "删除评论成功"
}
```

##### 返回参数说明


##### 抛出异常
* 无

---

### 获取用户评论的id

#### 简要描述
* 获取用户评论的id

#### 请求URL
* /api/questionMaster/getUserComment

##### 请求方式
* POST

#### 请求示例
```
{
	"token":"test_token",
	"answer_id":2
}
```

##### 请求参数
| 参数 | 必填 | 含义 | 说明 |
| --- | --- | --- | --- |
| token | 是| 用户token |  |
| answer_id | 是 | 回答ID |  |

#### 返回示例
```
{
  "page_number": 1,
  "page_size": 20,
  "count": 7,
  "list": [
    4,
    5,
    6
  ]
}
```

##### 返回参数说明


##### 抛出异常
* 无

---

## SpecialHouseController 主题购房

### 获取主题列表

#### 简要描述
* 获取主题列表

#### 请求URL
* ~~/api/specialHouse/getList~~ (废弃)
* /api/special_house/get_special_house (优化方法及新增返回数据)

##### 请求方式
* POST

#### 请求示例
```
{
  "page_number": 1,
  "page_size": 20,
}
```

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| page_number | 否 | 页码 | 默认1 |
| page_size | 否 | 每页数量 | 默认20 |

#### 返回示例
```
{
  "page_number": 1,
  "page_size": 20,
  "count": 2,
  "list": [
    {
      "title": "测试参数",  // 主题标题
      "cover": "http://images-cn.fang88.com/e71478ef8e8da2995f33f313909b8f8d.jpeg",  // 主题图片
      "info": "说明",   // 主题说明
      "params": {   // 参数，跟列表页请求的参数名一致
        "sqft_filter_min": "750",    // 居住面积
        "property_type_candidate_array": "COND",  // 房源类型
        "price_filter_min": "300000",  // 最低价格
        "price_filter_max": "400000",  // 最高价格
        "order": "roi",   // 排序方式
        "school_score_filter_on": true,   // 是否学区房
        "year_built_filter_min": "2005",  // 建筑时间
        "bedrooms_filter_min": "3",   // 卧室数量
        "roi_filter_min": "0.06",   // 回报率
        "area_candidate_array": "Boston",   // 区域
        "city_candidate_array": "Alford", // 城市
        "sqft_filter_on": true,  // 居住面积过滤
        "property_type_candidate_array_on": true,   // 房源类型过滤
        "price_filter_on": true,   // 价格过滤
        "roi_orderBy_on": true,   // 回报率排序
        "roi_orderBy_order": "DESC",  // 回报率排序方式
        "year_built_filter_on": true,  // 建筑时间过滤
        "bedrooms_filter_on": true,  // 卧室数量过滤
        "roi_filter_on": true,  // 投资回报率过滤
        "area_candidate_array_on": true,  // 区域过滤
        "state_candidate_array": "MA",  // 州
        "state_candidate_array_on": true,  // 州过滤
        "city_candidate_array_on": true  // 城市过滤
        "zipcode": 000111 // 邮编
      },
      "order_id": 1,  // 排序
      "time_add": "2017-08-02T19:09:20+0000"  // 添加时间
      "house_last_updated_at": "2018-02-05T08:16:46+0800",  // 最新更新时间DateTime型
      "house_last_updated_int": 1517789806          // 最新更新时间int型
    }
  ]
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

---

### 获取主题详情

#### 简要描述
* 获取主题详情

#### 请求URL
* /api/specialHouse/getInfo

##### 请求方式
* POST

#### 请求示例
```
{
  "id":2
}
```

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| id | 是 | int |  |

#### 返回示例
```
{
    "id": 2,
    "title": "测试参数",
    "cover": "http://images-cn.fang88.com/e71478ef8e8da2995f33f313909b8f8d.jpeg",
    "info": "测试更新",
    "params": {
        "sqft_filter_min": "750",
        "property_type_candidate_array": "0",
        "price_filter_min": "300000",
        "price_filter_max": "400000",
        "order": "roi",
        "school_score_filter_on": true,
        "year_built_filter_min": "2005",
        "bedrooms_filter_min": "3",
        "roi_filter_min": "0.06",
        "area_candidate_array": "Los Angeles",
        "city_candidate_array": [
            "29 Palms, CA",
            "Adelanto, CA"
        ],
        "sqft_filter_on": true,
        "price_filter_on": true,
        "roi_orderBy_on": true,
        "roi_orderBy_order": "DESC",
        "year_built_filter_on": true,
        "bedrooms_filter_on": true,
        "roi_filter_on": true,
        "area_candidate_array_on": true,
        "state_candidate_array_on": true,
        "city_candidate_array_on": true
    },
    "order_id": 4,
    "time_add": "2017-08-02T19:09:20+0000",
    "deleted": false
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

---

## SchoolController 学校数据

### 学校列表

#### 简要描述
* 根据经纬度获取学校列表

#### 请求URL
* /api/school/getSchoolListByBoundary

##### 请求方式
* POST

#### 请求示例
```
{
	"lng":"-120.7321",
	"lat":"46.3794"
}
```

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| lng | 是 | int | 经度 |
| lat | 是 | int | 纬度 |

#### 返回示例
```
[
    {
        "district_name": "Mount Adams School District",
        "district_nces_id": "5305280",
        "gs_rating": 1,
        "grade_range": "PK-6",
        "id": 207818,
        "lat": "46.4067000",
        "lon": "-120.5436000",
        "name": "Harrah Elementary School",
        "overview_link": "https://www.greatschools.org/washington/harrah/1080-Harrah-Elementary-School/?s_cid=gsapi",
        "type": "public",
        "unique_id": "WA_1080"
    },
    {
        "district_name": "Mount Adams School District",
        "district_nces_id": "5305280",
        "grade_range": "9-12",
        "id": 207780,
        "lat": "46.3794000",
        "lon": "-120.7321000",
        "name": "White Swan High School",
        "overview_link": "https://www.greatschools.org/washington/white-swan/1081-White-Swan-High-School/?s_cid=gsapi",
        "type": "public",
        "unique_id": "WA_1081"
    },
    {
        "district_name": "Mount Adams School District",
        "district_nces_id": "5305280",
        "gs_rating": 1,
        "grade_range": "6-8",
        "id": 207735,
        "lat": "46.3781000",
        "lon": "-120.7314000",
        "name": "Mount Adams Middle School",
        "overview_link": "https://www.greatschools.org/washington/white-swan/1082-Mount-Adams-Middle-School/?s_cid=gsapi",
        "type": "public",
        "unique_id": "WA_1082"
    }
]
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

---


## CityController 城市数据

### 城市详情数据

#### 简要描述
* 获取城市详情数据

#### 请求URL
* /api/city/getInfo

##### 请求方式
* POST

#### 请求示例
```
{
	"city":"West Manheim Township"
	"state":"Nevada"
}
```

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| city | 是 | string | 城市名称 |
| state | 是 | string | 州名称 |

#### 返回示例
```
{
    "id": 1,
    "entity_name": "West Manheim Township",
    "belong_to_town": "Town in Pennsylvania",
    "rankings_statement_str": "B",
    "rankings_statement_info": "[]",
    "people_number": 8064,
    "town_name": "",
    "town_info": "[]",
    "room_avg_buy_price": "$229300",
    "room_avg_lease_price": "$1159",
    "place_desc": "Suburban",
    "lease_self_info": [
        {
            "rank": "15%",
            "info": "Rent"
        },
        {
            "rank": "85%",
            "info": "Own"
        }
    ],
    "sort_info": "#",
    "crime_rank": "B+",
    "crime_force_info": [
        {
            "name": "Assault",
            "value": "36",
            "national": "0"
        },
        {
            "name": "Murder",
            "value": "0",
            "national": "0"
        },
        {
            "name": "Rape",
            "value": "48",
            "national": "41"
        },
        {
            "name": "Robbery",
            "value": "12",
            "national": "0"
        }
    ],
    "crime_property_info": [
        {
            "name": "Burglary",
            "value": "97",
            "national": "1"
        },
        {
            "name": "Theft",
            "value": "1,618",
            "national": "2,081"
        },
        {
            "name": "Motor Vehicle Theft",
            "value": "36",
            "national": "0"
        }
    ],
    "crime_safe_info": "",
    "crime_police_info": "",
    "people_rank_info": "C+",
    "people_rank_str_info": [
        {
            "rank": "52%",
            "info": "Male"
        },
        {
            "rank": "48%",
            "info": "Female"
        }
    ],
    "home_avg_income": 0,
    "home_avg_info": [
        {
            "rank": "13%",
            "info": "<$25k"
        },
        {
            "rank": "8%",
            "info": "$25-$44k"
        },
        {
            "rank": "22%",
            "info": "$45-$74k"
        },
        {
            "rank": "47%",
            "info": "$75-$149k"
        },
        {
            "rank": "10%",
            "info": "$150k+"
        }
    ],
    "one_avg_info": "$35,434",
    "personal_rank_info": [
        {
            "rank": "22%",
            "info": "<$15k"
        },
        {
            "rank": "27%",
            "info": "$15-$34k"
        },
        {
            "rank": "27%",
            "info": "$35-$64k"
        },
        {
            "rank": "23%",
            "info": "$65k+"
        }
    ],
    "children_rank": 24,
    "education_rank_info": "[]",
    "sex_rank_info": [
        {
            "rank": "13%",
            "info": "<$25k"
        },
        {
            "rank": "8%",
            "info": "$25-$44k"
        },
        {
            "rank": "22%",
            "info": "$45-$74k"
        },
        {
            "rank": "47%",
            "info": "$75-$149k"
        },
        {
            "rank": "10%",
            "info": "$150k+"
        }
    ],
    "race_rank_info": "[]",
    "old_rank_info": "[]",
    "community_str_info": [
        {
            "rank": "2",
            "info": "Excellent"
        },
        {
            "rank": "8",
            "info": "Very Good"
        },
        {
            "rank": "16",
            "info": "Average"
        },
        {
            "rank": "2",
            "info": "Poor"
        },
        {
            "rank": "1",
            "info": "Terrible"
        }
    ],
    "public_school_info": [
        {
            "name": "South Western Senior High School",
            "href": "https://www.niche.com/k12/south-western-senior-high-school-hanover-pa/"
        },
        {
            "name": "Baresville Elementary School",
            "href": "https://www.niche.com/k12/baresville-elementary-school-hanover-pa/"
        },
        {
            "name": "Emory H. Markle Intermediate School",
            "href": "https://www.niche.com/k12/emory-h-markle-intermediate-school-hanover-pa/"
        },
        {
            "name": "West Manheim Elementary School",
            "href": "https://www.niche.com/k12/west-manheim-elementary-school-hanover-pa/"
        },
        {
            "name": "Park Hills Elementary School",
            "href": "https://www.niche.com/k12/park-hills-elementary-school-hanover-pa/"
        }
    ],
    "private_school_info": [],
    "comment_rank_info": "",
    "url": "https://www.niche.com/places-to-live/west-manheim-township-york-pa/",
    "linkmd5id": "b3e37dc8fa4e43ecbaebfb6f017a3c1e"
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |
| msg | 英文消息 |  |
| msg_desc | 中文消息 | |

---

### 城市邮编

#### 简要描述
* 获取城市邮编

#### 请求URL
* /api/city/getZipCode

##### 请求方式
* POST

#### 请求示例
```
{
	"city":"West Manheim Township"
	"state":"Nevada"
}
```

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| city | 是 | string | 城市名称 |
| state | 是 | string | 州名称 |

#### 返回示例
```

"82718 / 82732"

```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |

---

### 城市房源涨幅

#### 简要描述
* 获取城市房价/租金涨幅

#### 请求URL
* <del>/api/city/getCityPriceRange</del>
* /api/city/get_city_price_range

##### 请求方式
* POST

#### 请求示例
```
{
	"type":"rent_all_year",
	"limit":10
}
```

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| type | 是 | string | 数据类型（price_year 房价涨幅；rent_all_year 租金涨幅） |
| limit | 否 | int | 数据条数，默认5 |

#### 返回示例
```
[
    {
        "city_en": "San Diego",  // 城市英文名
        "city_cn": "圣迭戈",      // 城市中文名
        "state": "CA",           // 州名
        "data": "4.80"           // 涨幅
        "house": "1000"          // 房源数
        "price_avg": 1480926,    // 成交均价
        "price_middle": 1325000, // 成交中位数
        "monthly_rent_avg": 2000 // 月租金
    }
]
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |

---

### 城市所有房源价格趋势

#### 简要描述
* 所有城市所有房源价格趋势

#### 请求URL
* /api/city/getCityCurrentPriceByCity

##### 请求方式
* POST

#### 请求示例
```
{
	"city":"29 Palms, CA"
}
```

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| city | 是 | string | 城市,州 |

#### 返回示例
```
[
    {
        "city": "29 Palms, CA",
        "property_type": "Lot/Land",
        "sqft_price": [
            0.024063797941101448,
            49.75124378109453,
            74.25742574257426,
            142.5
        ],
        "price": [
            5000,
            5500,
            6500,
            6900,
            100000,
            150000,
            250000,
            650000
        ],
        "count": 54,
        "price_avg": 37276.87037037037,
        "price_median": 15000,
        "sqft_price_avg": 66.63318333040246,
        "sqft_price_median": 49.75124378109453,
        "timestamp": 1512832450961
    },
]
```

---

### 城市某类房源价格趋势

#### 简要描述
* 当所城市某类房源价格趋势

#### 请求URL
* /api/city/getCityCurrentPriceByCityAndPropertyType

##### 请求方式
* POST

#### 请求示例
```
{
	"city":"29 Palms, CA",
   "type":"Lot/Land"
}
```

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| city | 是 | string | 城市,州 |
| type | 是 | string | 房源类型 |

#### 返回示例
```
{
    "city": "29 Palms, CA",
    "property_type": "Lot/Land",
    "sqft_price": [
        0.024063797941101448,
        49.75124378109453,
        74.25742574257426,
        142.5
    ],
    "price": [
        5000,
        150000,
        250000,
        650000
    ],
    "count": 54,
    "price_avg": 37276.87037037037,
    "price_median": 15000,
    "sqft_price_avg": 66.63318333040246,
    "sqft_price_median": 49.75124378109453,
    "timestamp": 1512832450961
}
```

---

### 首页热门城市数据

#### 简要描述
* 获取首页热门城市数据，房源数据是计划任务实时更新

#### 请求URL
* /api/city/get_hot_cities

##### 请求方式
* POST

#### 请求示例
* 无

##### 请求参数 
* 无

#### 返回示例
```
{
    "west": {
        "city_la": {
            "hrefCity": "Los Angeles",
            "imgUrl": "city_la.jpg",
            "citycircleName": "洛杉矶",
            "houseNum": "23317",
            "introWord": "洛杉矶是全美第二大城市，也是美国华人最多的城市之一。洛杉矶在影视、娱乐和音乐方面占据重要国际地位。众人熟知的好莱坞就坐落在洛杉矶，每年都会迎接众多来自世界各地的游客。"
        },
        "city_san_diego": {
            "hrefCity": "San Diego",
            "imgUrl": "city_san_diego.jpg",
            "citycircleName": "圣地亚哥",
            "houseNum": "6486",
            "introWord": "圣地亚哥位于加州南部，是一座美丽的海滨城市。圣地亚哥气候温暖景色秀丽，旅游业非常发达。圣地亚哥的科技产业也处于全美领先水平，经济仅次于洛杉矶和旧金山排名加州第三。"
        }
    },
    "east": {
        "city_ny": {
            "hrefCity": "New York",
            "imgUrl": "city_ny.jpg",
            "citycircleName": "纽约",
            "houseNum": "2959",
            "introWord": "纽约是全美第一大城市，也是全球经济，商业，文化、科技、金融中心，被称为“世界文化之都”。纽约也是联合国总部所在地，著名的时代广场、自由女神像、百老汇等著名景点也坐落于此。"
        }
    }
}
```

---


## SystemRecommendHouseController 系统推荐房源

### 保存推荐房源

#### 简要描述
* 保存推荐房源

#### 请求URL
* /api/system_recommend_house/save

##### 请求方式
* POST

#### 请求示例
```
{
	"user_id":1,
	"obj_id":1064892,
	"obj_type":2
}
```

##### 请求参数 
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| user_id | 是 | int | 用户ID |
| obj_type | 是 | int | 房源类型 |
| obj_id | 是 | int | 房源ID |

#### 返回示例
```
{
    "state": 1,
    "msg": "save recommend record success"
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |

---

## WeArticleController 文章

### 文章列表v1

#### 简要描述
* 文章列表，老版本
* 暂不删除，与房多多合作使用到

#### 请求URL
* /api/we_article/get_all_audited_we_article_list

##### 请求方式
* POST

#### 请求示例
```
{
   "page_number":1,
   "page_size":20,
   "publish_time_orderBy_on":true,
   "publish_time_orderBy_order":"DESC",
   "total_visit_count_orderBy_on":true,
   "total_visit_count_orderBy_order":"DESC"
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| page_number | 否 | int | 搜索页数 |
| page_size | 否 | int | 每页数量 |
| publish_time_orderBy_on | 否 | boolean| 是否按发布时间排序 |
| publish_time_orderBy_order | 否 | string | 排序类型 | 
| total_visit_count_orderBy_on | 否 | boolean | 是否按浏览数排序 |
| total_visit_count_orderBy_order | 否 | string | 排序类型 |

#### 返回示例
```
[
    {
        "unique_id": "d77ee64551919ab414c55537352d59c9",
        "fix_top": 0,
        "cover_image_path": "44a1d7c9fe7b2bbbceeaac0c5163182d.jpeg",
        "title": "去美国购房投资，这几张图你一定要牢牢记在脑子里！",
        "abstract": "纯干货分享！美国购房必备知识，一定要牢牢记在脑子里",
        "source": "房88美国房产",
        "publish_time": "2017-09-27T11:08:55+0800",
        "is_audit_success": true,
        "total_visit_count": 2371,
        "total_share_count": 0,
        "tag_xinwen": true,
        "tag_fangchan": true,
        "tag_jiaoyu": false,
        "tag_yimin": false,
        "tag_shenghuo": false,
        "tag_touzi": true,
        "tag_yule": false,
        "tag_gonglue": false
    }
]    
```

##### 返回参数说明
| 参数 | 类型 | 说明 |
| --- | --- | --- |
| unique_id | string | 文章唯一ID |
| cover_image_path | string | 文章封面,加 http://img.fang88.com/ 来访问 |
| title | string | 文章标题 |
| abstract | string | 文章简介 |
| source | string | 文章来源 |
| publish_time | datetime | 发布时间 |
| total_visit_count | int | 访问数 |
| total_share_count | int | 分享数 |
| tag_xinwen | boolean | 新闻标签 |
| tag_fangchan | boolean | 房产标签 |
| tag_jiaoyu | boolean | 教育标签 |
| tag_yimin | boolean | 移民标签 |
| tag_shenghuo | boolean | 生活标签 |
| tag_touzi | boolean | 投资标签 |
| tag_yule | boolean | 娱乐标签 |
| tag_gonglue | boolean | 攻略标签 |

##### 抛出异常
* 无

---

### 文章详情

#### 简要描述
* 文章详情

#### 请求URL
* /api/we_article/get_one_we_article_by_unique_id

##### 请求方式
* POST

#### 请求示例
```
{
   "unique_id":"unique_id"
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| unique_id | 是 | string | 唯一ID |

#### 返回示例
```
{
    "unique_id": "d77ee64551919ab414c55537352d59c9",
    "fix_top": 0,
    "cover_image_path": "44a1d7c9fe7b2bbbceeaac0c5163182d.jpeg",
    "title": "去美国购房投资，这几张图你一定要牢牢记在脑子里！",
    "abstract": "纯干货分享！美国购房必备知识，一定要牢牢记在脑子里",
    "source": "房88美国房产",
    "content": "content",
    "publish_time": "2017-09-27T11:08:55+0800",
    "is_audit_success": true,
    "total_visit_count": 2371,
    "total_share_count": 0,
    "total_support_count": 10,
    "tag_xinwen": true,
    "tag_fangchan": true,
    "tag_jiaoyu": false,
    "tag_yimin": false,
    "tag_shenghuo": false,
    "tag_touzi": true,
    "tag_yule": false,
    "tag_gonglue": false
}
```

##### 返回参数说明
| 参数 | 类型 | 说明 |
| --- | --- | --- |
| unique_id | string | 文章唯一ID |
| cover_image_path | string | 文章封面,加 http://img.fang88.com/ 来访问 |
| title | string | 文章标题 |
| abstract | string | 文章简介 |
| content | string | 内容 |
| source | string | 文章来源 |
| publish_time | datetime | 发布时间 |
| total_visit_count | int | 访问数 |
| total_share_count | int | 分享数 |
| total_support_count | int | 点赞数 |
| tag_xinwen | boolean | 新闻标签 |
| tag_fangchan | boolean | 房产标签 |
| tag_jiaoyu | boolean | 教育标签 |
| tag_yimin | boolean | 移民标签 |
| tag_shenghuo | boolean | 生活标签 |
| tag_touzi | boolean | 投资标签 |
| tag_yule | boolean | 娱乐标签 |
| tag_gonglue | boolean | 攻略标签 |

##### 抛出异常
* 无

---

### 搜索文章v1

#### 简要描述
* 搜索文章

#### 请求URL
* /api/we_article/search_article

##### 请求方式
* POST

#### 请求示例
```
{
	"kw":"测试",
   "page_number":1,
   "page_size":20
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| kw | 是 | string | 搜索关键词 |
| page_number | 否 | int | 搜索页数 |
| page_size | 否 | int | 每页数量 |

#### 返回示例
```
{
    "page_number": 1,
    "page_size": 20,
    "count": 65,
    "list": [
        {
            "id": "5030",
            "unique_id": "d37475954fa9fe2deb8d7f1",  // unique id
            "fix_top": 0,
            "cover_image_path": "b200f96755dcf7743c2e7d618051867ec.jpg",  // 封图
            "title": "美国房产交易费用到底有多贵？专家告诉你如何才能够省去房产交易费",  // 标题
            "abstract": "美国房地产行业成熟监管力度大，主要得益于严格的制度和专业的服务。",  // 摘要
            "source": "Fang88",  // 来源
            "content": "",  // 内容
            "publish_time": "2017-06-29T13:03:27+0000",  // 发布时间
            "is_audit_success": true,
            "total_visit_count": 6734,  // 浏览数
            "total_visit_count_actual": 167,  // 实际浏览数
            "total_share_count": 0,   // 分享数
            "we_article_filters": [],
            "fav_by_we_article_filters": [],
            "tag_xinwen": false,  // 新闻标签
            "tag_fangchan": true,  // 房产标签
            "tag_jiaoyu": false,  // 教育标签
            "tag_yimin": false,  // 移民标签
            "tag_shenghuo": false,  // 生活标签
            "tag_touzi": true,  // 投资标签
            "tag_yule": false,  // 娱乐标签
            "tag_gonglue": true,  // 攻略标签
            "deleted": false  // 是否删除
        }
   ]
}
```

##### 返回参数说明
| 参数 | 类型 | 说明 |
| --- | --- | --- |

##### 抛出异常
* 无

---


### 文章列表v2

#### 简要描述
* 文章列表，新版本

#### 请求URL
* /api/we_article/get_article_list

##### 请求方式
* POST

#### 请求示例
```
{
   "page_number":1,
   "page_size":20
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| page_number | 否 | int | 搜索页数 |
| page_size | 否 | int | 每页数量 |

#### 返回示例
```
[
    {
        "unique_id": "78b00595a38c92a5a5c7a77",
        "fix_top": 1,
        "cover_image_path": "bd6395aa78e67d6d4e60d15710d8fb4cb.jpg",
        "file_path": "https://www.youtube.com/embed/5OSympqLBDc",
        "title": "庆祝独立日，川普出席“自由集会”演讲，称“人权神授，自由来于造物主”",
        "abstract": "美国总统川普于7月1日晚来到肯尼迪艺术中心（Kennedy Center），出席“自由集会（Celebrate Freedom）”并演讲，庆祝即将到来的美国独立日。川普登上集会讲台后，在场观众报以热烈的掌声。",
        "publish_time": "2017-12-08T05:28:49+0000",
        "total_visit_count": 0,
        "tags": [
            "投资",
            "新闻",
            "生活"
        ]
    }
]
```

##### 返回参数说明
| 参数 | 类型 | 说明 |
| --- | --- | --- |
| unique_id | string | 文章唯一ID |
| cover_image_path | string | 文章封面,加 http://img.fang88.com/ 来访问 |
| title | string | 文章标题 |
| file_path | string | 视频链接 |
| abstract | string | 文章简介 |
| publish_time | datetime | 发布时间 |
| total_visit_count | int | 访问数 |
| tags | array | 标签 |

##### 抛出异常
* 无

---

### 搜索文章v2

#### 简要描述
* 搜索文章

#### 请求URL
* /api/we_article/v2/search_article

##### 请求方式
* POST

#### 请求示例
```
{
	"kw":"测试",
   "page_number":1,
   "page_size":20
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| kw | 是 | string | 搜索关键词 |
| page_number | 否 | int | 搜索页数 |
| page_size | 否 | int | 每页数量 |

#### 返回示例
```
{
    "page_number": 1,
    "page_size": 20,
    "count": 65,
    "list": [
        {
            "unique_id": "3f74f5963706bee10bffc5b",
            "fix_top": 0,
            "cover_image_path": "b0bf69f36b3067b52b9b32b7b31d667df.jpg",
            "file_path": "",
            "title": "吃货帝国的福音？美国牛肉时隔14年卷土重来",
            "abstract": "近日，美国商务部宣布，中国同意开放美国牛肉进口。自2003年中国禁止进口美国牛肉以来，美国牛肉被中国市场隔绝已长达14年之久。此前，美国一直都是中国最大的牛肉进口国，约占总进口量的66%。2003年美国爆发疯牛病疫情，中国政府随即颁布针对美国牛肉的禁令。但随着特朗普担任新一届美国总统，致力于解决中美贸易失衡问题的他推动了中美贸易谈判，此番解禁美国牛肉进口正是成果之一。",
            "publish_time": "2017-07-10T12:17:47+0000",
            "total_visit_count": 5561,
            "tags": []
        }
   ]
}
```

##### 返回参数说明
| 参数 | 类型 | 说明 |
| --- | --- | --- |

##### 抛出异常
* 无

---

### 收藏文章

#### 请求URL
* /api/we_article/doFav

##### 请求方式
* POST

#### 请求示例
```
{
	"token":"test",
	"obj_id":"e3c565954f74473aa2868f2",
	"type":1
}
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| obj_id | 文章ID | 必填 |
| type | 类型 | 必填，1收藏、2取消收藏 |

#### 返回示例
```
{
    "state": 1,
    "msg": "fav success",
    "msg_desc": "收藏成功"
}
```

---

### 分享文章

#### 请求URL
* /api/we_article/doShare

##### 请求方式
* POST

#### 请求示例
```
{
	"token":"test",
	"obj_id":"e3c565954f74473aa2868f2",
}
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| obj_id | 文章ID | 必填 |

#### 返回示例
```
{
    "state": 1,
    "msg": "share success",
    "msg_desc": "分享成功"
}
```

---

### 点赞文章

#### 简要描述
* 用户点赞文章

#### 请求URL
* /api/we_article/doSupport

##### 请求方式
* POST

#### 请求示例
```
{
	"token":"test",
	"obj_id":"e3c565954f74473aa2868f2",
}
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| token | 用户token | 必填 |
| obj_id | 文章ID | 必填 |

#### 返回示例
```
{
    "state": 1,
    "msg": "support success",
    "msg_desc": "点赞成功"
}
```

---

### 标签文章

#### 简要描述
* 获取某一标签的文章

#### 请求URL
* /api/we_article/getArticleListByTag

##### 请求方式
* POST

#### 请求示例
```
{
	"tag":"房产",
	"page_number":1,
	"page_size":20
}
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| tag | 标签 | 必填 |
| page_number | 页码 | 非必填 |
| page_size | 每页数量 | 非必填 |

#### 返回示例
```
[
    {
        "id": 5034,
        "unique_id": "c4c7b59563f997f73d40bea",
        "fix_top": 1,
        "cover_image_path": "bc500613d4b8e9c0bb455db2c6351ac72.jpg",
        "file_path": "",
        "title": "全美6月房价深度解析：市场需求远大于新建房屋数量，高端房产市场火爆带动全美房价继续升高",
        "abstract": "美新建房屋售价中位数为$345,800，成为近10年以来的最高值",
        "publish_time": "2017-09-06T23:03:53+0000",
        "total_visit_count": 0,
        "tags": [
            "新闻",
            "房产",
            "攻略"
        ]
    }
]
```

---

### 相关文章

#### 简要描述
* 获取某一标签的文章

#### 请求URL
* /api/we_article/getRelationArticle

##### 请求方式
* POST

#### 请求示例
```
{
	"unique_id":"8eaf0595cd688e58bcec712"
}
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| unique_id | 文章ID | 必填 |

#### 返回示例
```
[
    {
        "title": "在美国参加婚礼如何送礼物？这些东西最糟糕！",       // 标题
        "unique_id": "e3c565954f74473aa2868f2",         // unique_id
        "cover_image_path": "bff997f452637358f2ed4e667e0c68d06.jpg",    // 封面
        "total_support_count": 1,               // 点赞数
        "total_fav_count": 2,                   // 收藏数
        "total_share_count": 3                  // 分享数
    },
]
```

---

### 相关百科

#### 简要描述
* 获取跟文章相关的百科

#### 请求URL
* /api/we_article/getRelationWikiInfo

##### 请求方式
* POST

#### 请求示例
```
{
	"unique_id":"8eaf0595cd688e58bcec712"
}
```

##### 请求参数
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| unique_id | 文章ID | 必填 |

#### 返回示例
```
{
    "id": 1,
    "unique_id": "a8f93141afdde4adbd775e39238b9a30",
    "menu_id": 1,
    "title": "旧金山1",
    "abstract": "旧金山（San Francisco），又译“三藩市”、“圣弗朗西斯科”，美国加利福尼亚州太平洋沿岸港口城市，是世界著名旅游胜地、加州人口第四大城市。旧金山临近世界著名高新技术产业区硅谷，是世界最重要的高新技术研发基地和美国西部最重要的金融中心[1]  ，也是联合国的诞生地（1945年《联合国宪章》）",
    "time_add": "2017-12-07T09:37:24+0000",
    "time_upd": "2017-12-13T08:05:30+0000",
    "total_visit_count": 7,
    "total_share_count": 0,
    "total_support_count": 0,
    "total_fav_count": 0,
    "tags": [
        "旧金山",
        "测试3",
        "教育"
    ]
}
```

---

### 置顶文章列表

#### 简要描述
* 文章列表，只取置顶文章

#### 请求URL
* /api/we_article/get_top_article_list

##### 请求方式
* POST

#### 请求示例
```
{
   "page_number":1,
   "page_size":3
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| page_number | 否 | int | 搜索页数 |
| page_size | 否 | int | 每页数量 |

#### 返回示例
```
[
    {
        "id": 5300,
        "unique_id": "797a80bd43827282b35b222be0a72543",
        "fix_top": 0,
        "cover_image_path": "ce582a72ee74a24b27dff3db4a8e99a5.jpeg",
        "file_path": "",
        "title": "test001",
        "abstract": "test001",
        "publish_time": "2017-12-26T14:16:19+0000",
        "total_visit_count": 2,
        "tags": [
            "浿以",
            "若肋"
        ]
    }
]
```

##### 返回参数说明
| 参数 | 类型 | 说明 |
| --- | --- | --- |
| id | int | 文章ID |
| unique_id | string | 文章唯一ID |
| cover_image_path | string | 文章封面,加 http://img.fang88.com/ 来访问 |
| title | string | 文章标题 |
| file_path | string | 视频链接 |
| abstract | string | 文章简介 |
| publish_time | datetime | 发布时间 |
| total_visit_count | int | 访问数 |
| tags | array | 标签 |

##### 抛出异常
* 无

---

### 正常文章列表

#### 简要描述
* 文章列表，按发布时间排序，不区分是否置顶

#### 请求URL
* /api/we_article/get_article_list_by_time

##### 请求方式
* POST

#### 请求示例
```
{
   "page_number":1,
   "page_size":20
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| page_number | 否 | int | 搜索页数 |
| page_size | 否 | int | 每页数量 |

#### 返回示例
```
[
    {
        "id": 5300,
        "unique_id": "797a80bd43827282b35b222be0a72543",
        "fix_top": 0,
        "cover_image_path": "ce582a72ee74a24b27dff3db4a8e99a5.jpeg",
        "file_path": "",
        "title": "test001",
        "abstract": "test001",
        "publish_time": "2017-12-26T14:16:19+0000",
        "total_visit_count": 2,
        "tags": [
            "浿以",
            "若肋"
        ]
    }
]
```

##### 返回参数说明
| 参数 | 类型 | 说明 |
| --- | --- | --- |
| id | int | 文章ID |
| unique_id | string | 文章唯一ID |
| cover_image_path | string | 文章封面,加 http://img.fang88.com/ 来访问 |
| title | string | 文章标题 |
| file_path | string | 视频链接 |
| abstract | string | 文章简介 |
| publish_time | datetime | 发布时间 |
| total_visit_count | int | 访问数 |
| tags | array | 标签 |

##### 抛出异常
* 无

---


## DataExchangeRateController 汇率控制器

### 获取汇率信息

#### 简要描述
* 汇率信息

#### 请求URL
* /api/exchange_rate/getInfoByCode

##### 请求方式
* POST

#### 请求示例
```
{
	"code":"USD"
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| code | 是 | string | 货币代码 |

#### 返回示例
```
{
    "id": 49,
    "currency": "美元",
    "refe_price": "666.720",
    "code": "USD",
    "time_update": "2017-09-28T15:05:06+0800"
}
```

##### 返回参数说明
| 参数 | 类型 | 说明 |
| --- | --- | --- | --- |
| currency | string | 货币中文名 |
| refe_price | string | 汇率 |
| code | string | 货币代码 |
| time_update | datetime | 更新时间 |

##### 抛出异常
* 无

---

## UserLeaveWordController 用户留言控制器

### 保存用户留言

#### 简要描述
* 保存用户留言

#### 请求URL
* /api/userLeaveWord/save

##### 请求方式
* POST

#### 请求示例
```
{
	"username":"陈川尧",
	"mobile":"15801351819",
	"email":"ccy034106@163.com",
	"city":"北京",
	"content":"test"
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| username | 是 | string | 姓名 |
| mobile | 是 | string | 电话 |
| email | 是 | string | 手机 |
| city | 否 | string | 城市 |
| content | 否 | string | 留言内容 |

#### 返回示例
```
{
    "state": 1,
    "msg": "leave word success"
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
| state | 状态 | 0：失败、1：成功 |

##### 抛出异常
* 无

---

## PageRecommendHouseController 手动推荐房源

### 获取房源

#### 简要描述
* 获取手机推荐的房源

#### 请求URL
* /api/page_recommend_house/getList

##### 请求方式
* POST

#### 请求示例
```
{
   "page_number":1,
   "page_size":20
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| page_number | 否 | int | 搜索页数 |
| page_size | 否 | int | 每页数量 |


#### 返回示例
```
[
    {
        "area": "奥兰多城市圈",
        "address": "3566 Creswick Cir",
        "fav_users_num": 0,
        "bathrooms": "3.00",
        "bedrooms": "4.0",
        "city": "Orlando",
        "current_list_price": 294900,
        "estimated_monthly_rent": 1750,
        "estimated_yearly_return": "0.1378655",
        "id": 13236116,
        "list_date": "2017-10-19T04:00:00+0800",
        "location_latitude": "28.5007690",
        "location_longitude": "-81.2414000",
        "openhouses": [],
        "photo_json": "[{\"path\":\"d68be0eda8e5eb5f11cbc40c80b4e638.jpg\"},{\"path\":\"ae3fe92bc70049b4063a874d98504e4e.jpg\"},{\"path\":\"cea25d4d236ed8078d52aabf30e0dbd5.jpg\"},{\"path\":\"17d00f721757af4ed26d617d8adf39e6.jpg\"},{\"path\":\"22903c90962a9afc839def5985589e14.jpg\"},{\"path\":\"115416789fe39e8b55fd026b4f93ddbf.jpg\"},{\"path\":\"a7f01c120e3244ea2e29dbd8f1fbdfca.jpg\"},{\"path\":\"535bab767fbfdde0fe036e39ec2f226b.jpg\"},{\"path\":\"ab6159e9e00cdd10bcc06cff13eb83d9.jpg\"},{\"path\":\"0706e954ed2bde41059a2e8f716d4733.jpg\"},{\"path\":\"1f482deb80b7b594f5c2c80c76b0106b.jpg\"},{\"path\":\"181bf57783f1b83ee74cdd30bb627d3c.jpg\"},{\"path\":\"13012d4ccf818104b0656bed8ea82a94.jpg\"},{\"path\":\"75960bcbcffe3df17fa38da00d6c922e.jpg\"},{\"path\":\"a979cbac2b0df4775f926069f37e79b7.jpg\"},{\"path\":\"76282b22dd64bc38052b956bf0bd17d2.jpg\"},{\"path\":\"a1db5c70d60d44095e34dbf94c441943.jpg\"},{\"path\":\"55d83c8c1b28e5b23b5ef16896c89273.jpg\"},{\"path\":\"4acbe4068f1be7f2c19fb29469d9873f.jpg\"},{\"path\":\"96750d1d52ce48ad09ede66da471f823.jpg\"},{\"path\":\"9d53baa9e24b673090f05751eadac742.jpg\"},{\"path\":\"ba391cdc59acf9196382ac248b39b43a.jpg\"},{\"path\":\"03a30023c79cdc23b9a57823b23abe7b.jpg\"},{\"path\":\"3b416e29431ceeedeb49fb88cb5a34f9.jpg\"},{\"path\":\"726983a185ad60111e67905b3b90a418.jpg\"}]",
        "property_type": "RESI",
        "school_score": 8,
        "sqft": 2217,
        "source": "MatrixMFR",
        "state": "FL",
        "status": "A",
        "tags": [],
        "unique_id": "MatrixMFR_211401391",
        "updated_at": "2017-10-28T12:16:43+0800",
        "year_built": 2012,
        "zip": "32829"
    }
]
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
|  |  |  

##### 抛出异常
* 无

---

## MortgageController 贷款控制器

### 保存贷款资料

#### 简要描述
* 保存贷款资料
* 2018-03-12 @ 更新，不需要强制登录；取消email, is_american, has_broker, visa_type

#### 请求URL
* /api/mortgage/save

##### 请求方式
* POST

#### 请求示例
```
{
	"token":"962eb627e31cd729c0390fc5c41805438a22622104b0ced8b1bb6c4f7b5422d6",
	"city":"北海",
	"down_payments":"10000",
	"down_payments_percentage":"40",
	"is_american":1,
	"has_earning":1
	"earning_type":1,
	"earning_amount":50000,
	"has_broker":0,
	"username":"方块七",
	"mobile":"1234567890",
	"email":"ccy034106@163.com",
	"visa_type":1
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 否 | string | token |
| city | 是 | string | 城市 |
| down_payments | 否 | int | 贷款金额 |
| down_payments_percentage | 否 | int | 贷款比例 |
| is_american | 否 | boolean | 是否美国公民 |
| has_earning | 是 | boolean | 是否有收入 |
| earning_type | 否 | int | 收入类型 |
| earning_amount | 否 | int | 收入，has_earning=true时必填 |
| has_broker | 否 | boolean | 是否有经纪人 |
| username | 是 | string | 姓名 |
| mobile | 是 | string | 电话 |
| email | 是 | string | 邮箱 |
| visa_type | 否 | int | 签证类型 |

#### 返回示例
```
{
    "state": 1,                                 // 保存成功
    "msg": "update mortgage info success",      // 信息
    "is_american": true,                        // 是否美国公民
    "has_earning": true,                        // 是否有收
    "amount": 106501                            // 能贷款的金额
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
|  |  |  

##### 抛出异常
* 无

---

### 获取贷款常见问题

#### 请求URL
* /api/mortgage/getQuestionList

#### 请求方式
* POST

#### 请求示例
```
{
	"page_number":1,
	"page_size":10
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| page_number | 否 | int | 页数 |
| page_size | 否 | int | 每页数量 |

#### 返回示例
```
[
    {
        "id": 2,
        "type": 2,
        "icon": "http://img.fang88.com/e38c6acb147ac2a6457abdd5ff24ea5a.jpeg",      // 常见问题图标，移动端用到
        "question": "贷款问题一",                                                     // 问题
        "answer": "问题一答案",                                                       // 答案
        "order_id": 1,
        "time_upd": "2017-11-17T06:42:04+0000",
        "deleted": false
    },
    {
        "id": 3,
        "type": 2,
        "icon": "http://img.fang88.com/111caa280adaf6d28cf4bcf2de120914.jpeg",
        "question": "贷款问题二",
        "answer": "问题二答案",
        "order_id": 2,
        "time_upd": "2017-11-17T06:42:41+0000",
        "deleted": false
    }
]
```


##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
|  |  |  

##### 抛出异常
* 无

---

### 获取贷款相关资料

#### 请求URL
* /api/mortgage/getNewsList

#### 注
* 请求参数与返回内容与 /api/we_article/get_all_audited_we_article_list 一样

---

### 获取用户贷款信息

#### 请求URL
* /api/mortgage/get

#### 请求方式
* POST

#### 请求示例
```
{
	"token":"token",
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| token | 是 | string | token |

#### 返回示例
```
{
    "id": 1,
    "user_id": 1932,
    "city": "北海",
    "down_payments": "10000.00",
    "down_payments_percentage": "40.00",
    "is_american": true,
    "visa_type": 0,
    "earning_amount": "50000.00",
    "earning_type": true,
    "has_earning": true,
    "has_broker": false,
    "username": "方块七",
    "mobile": "1234567890",
    "email": "ccy034106@163.com",
    "is_reply": false
}
```


##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
|  |  | 

##### 抛出异常
* 无

---

## WikiArticleController 百科文章

### 随机获取百科

#### 简要描述
* 随机获取百科

#### 请求URL
* /api/wikiArticle/getOneByRandom

##### 请求方式
* POST

##### 请求参数
* 无


#### 返回示例
```
{
    "id": 6,
    "unique_id": "a8f93141afdde4adbd775e39238b9a305",
    "menu_id": 7,
    "title": "旧金山4",
    "abstract": "旧金山（San Francisco），又译“三藩市”、“圣弗朗西斯科”，美国加利福尼亚州太平洋沿岸港口城市，是世界著名旅游胜地、加州人口第四大城市。旧金山临近世界著名高新技术产业区硅谷，是世界最重要的高新技术研发基地和美国西部最重要的金融中心[1]  ，也是联合国的诞生地（1945年《联合国宪章》）",
    "time_add": "2017-12-07T09:37:24+0000",
    "time_upd": "2017-12-07T09:47:38+0000",
    "total_visit_count": 0,
    "total_share_count": 0,
    "total_support_count": 0,
    "total_fav_count": 0,
    "tags": [
        "旧金山",
        "测试3"
    ]
}
```

##### 抛出异常
* 无

---

### 百科详情

#### 简要描述
* 获取百科内容

#### 请求URL
* /api/wikiArticle/getArticleInfo

##### 请求方式
* POST

#### 请求示例
```
{
	"unique_id":"unique_id"
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| unique_id | 是 | string | 文章id |

#### 返回示例
```
{
    "article": {
        "id": 1,
        "unique_id": "a8f93141afdde4adbd775e39238b9a30",
        "menu_id": 1,
        "title": "旧金山1",
        "abstract": "旧金山（San Francisco），又译“三藩市”、“圣弗朗西斯科”，美国加利福尼亚州太平洋沿岸港口城市，是世界著名旅游胜地、加州人口第四大城市。旧金山临近世界著名高新技术产业区硅谷，是世界最重要的高新技术研发基地和美国西部最重要的金融中心[1]  ，也是联合国的诞生地（1945年《联合国宪章》）",
        "content": "content",
        "time_add": "2017-12-07T09:37:24+0000",
        "time_upd": "2017-12-13T08:05:30+0000",
        "total_visit_count": 8,
        "total_share_count": 0,
        "total_support_count": 0,
        "total_fav_count": 0,
        "tags": [
            "旧金山",
            "测试3",
            "教育"
        ],
        "house_relation_condition": "{\"community\":false,\"sqft_filter_min\":\"750\",\"property_type_candidate_array\":[\"COND\"],\"order\":\"0\",\"school_score_filter_on\":\"0\",\"year_built_filter_min\":\"0\",\"bedrooms_filter_min\":\"0\",\"roi_filter_min\":\"0\",\"area_candidate_array\":\"0\",\"sqft_filter_on\":true,\"property_type_candidate_array_on\":true}",
        "article_relation_condition": [
            "旧金山",
            "测试2"
        ],
        "lecture_relation_condition": [
            "旧金山",
            "测试1"
        ],
        "is_del": false
    },
    "menu_list": {
        "1": {
            "info": {
                "id": 1,
                "parent_id": 0,
                "title": "购房区域"
            },
            "sub": [
                {
                    "id": 7,
                    "parent_id": 1,
                    "title": "选择地区和城市"
                },
                {
                    "id": 10,
                    "parent_id": 1,
                    "title": "选择学校"
                },
                {
                    "id": 11,
                    "parent_id": 1,
                    "title": "选择房源"
                }
            ]
        },
        "2": {
            "info": {
                "id": 2,
                "parent_id": 0,
                "title": "选房看房"
            }
        },
        "3": {
            "info": {
                "id": 3,
                "parent_id": 0,
                "title": "财务准备"
            }
        },
        "4": {
            "info": {
                "id": 4,
                "parent_id": 0,
                "title": "签约订房"
            }
        },
        "5": {
            "info": {
                "id": 5,
                "parent_id": 0,
                "title": "交接过户"
            }
        },
        "6": {
            "info": {
                "id": 6,
                "parent_id": 0,
                "title": "房屋托管"
            },
            "sub": [
                {
                    "id": 12,
                    "parent_id": 6,
                    "title": "房屋保险"
                },
                {
                    "id": 14,
                    "parent_id": 6,
                    "title": "产权保险"
                },
                {
                    "id": 13,
                    "parent_id": 6,
                    "title": "房室过户"
                }
            ]
        }
    },
    "menu_info": {
        "id": 7,
        "parent_id": 1,
        "parent_str": "/1/",
        "title": "选择地区和城市",
        "order_id": 1,
        "deleted": false,
        "is_relation_news": false,
        "is_relation_house": true,
        "is_relation_lecture": true,
        "is_relation_loan": true
    }
}
```

##### 抛出异常
* 无

---

### 相关资讯

#### 简要描述
* 获取跟百科相关的资讯

#### 请求URL
* /api/wikiArticle/getRelationWeArticle

##### 请求方式
* POST

##### 请求参数
```
{
	"unique_id":"a8f93141afdde4adbd775e39238b9a30"
}
```


#### 返回示例
```
[
    {
        "title": "名校之路不只千军万马独木桥，还有眼前的这份“双”保险！",
        "unique_id": "00fa3595b86e0e643d9b35d",
        "abstract": "莫让成绩宣判人生，踏出国门打开一扇全新的大门。不单以成绩论英雄，不让分数变成门槛，换个思路，跨出这一步，条条大路通美国！",
        "cover_image_path": "bc8fbf9c12f8a1115a0b53d1ba1f9ccf1.jpg"
    },
    {
        "title": "家有留学生，身为父母该不该做美国房产投资？",
        "unique_id": "f927a59636b2f0a356003c0",
        "abstract": "美国法律规定，任何孩子包括父母是偷渡者的孩子，只要是居住在这个学区内，都享有免费教育的权利。公立学校（包括1年幼儿园）到高中毕业是全部免费的。下面我们就来了解一下美国的学区房。",
        "cover_image_path": "b6f7f6c957c191e641bca0d29516a38e0.jpg"
    },
    {
        "title": "如果你是一个勤奋的自学者，别错过这些线上学习平台",
        "unique_id": "16e2359636f7b5eb550b92f",
        "abstract": "活到老，学到老，你是否是这个口号的贯彻执行者呢？如果你是一个勤奋的自学者，那么不妨来看看帮你准备的这些线上教育网站，这些网站上有可供你免费查找的资料哦~原来自学，也可以如此轻松~",
        "cover_image_path": "b41f09868fcb7f8f36f5da20e134469ee.jpg"
    },
    {
        "title": "以房养学：免费留学还能赚钱的方式你知道吗？",
        "unique_id": "8a1e759661a25399a256fcf",
        "abstract": "很多人都有一个疑问，国内买家到底应该着重考虑投资哪些国家的房产？业内人士表示：依据以上置业目的不同，选择国家也有所差别。",
        "cover_image_path": "bbfda2ccc59873755b838a52a8e5449a3.jpg"
    }
]
```

##### 抛出异常
* 无

---

## WikiMenuController 百科目录

### 获取百科目录

#### 请求URL
* /api/wikiMenu/getAllList

##### 请求方式
* POST

#### 请求示例
```
{
	"menu_id":1
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| menu_id | 是 | int | 菜单id |


#### 返回示例
```
{
    "1": {
        "info": {
            "id": 1,  // 一级目录ID
            "parent_id": 0,
            "title": "购房区域"  // 一级目录名称
        },
        "sub": [
            {   
                "id": 7,   // 子目录id
                "parent_id": 1,
                "title": "选择地区和城市",  // 子目录名称
                "article_list": [
                    {   // 子目录文章列表
                        "unique_id": "a8f93141afdde4adbd775e39238b9a30",
                        "title": "旧金山1"
                    }
                ]
            },
            {
                "id": 10,
                "parent_id": 1,
                "title": "选择学校",
                "article_list": []
            },
            {
                "id": 11,
                "parent_id": 1,
                "title": "选择房源",
                "article_list": []
            }
        ]
    }
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
|  |  |  |

##### 抛出异常
* 无

---

## AdsController 广告推荐图

### 获取头条首页讲座推广图

#### 请求URL
* /api/ads/get_one_lecture

##### 请求方式
* POST

#### 请求示例
```
{
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| | | | |


#### 返回示例
```
{
    "id": 1,
    "type": 1,
    "image_path": "http://img.fang88.com/a00f5d4a418ac430072e10db15085c0b.png",  // 图片
    "url": "http://fang88.me",                                                   // 链接
    "title": "test01",                                                           // 标题
    "abstract": "test01"                                                         // 简介
}
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
|  |  |  |

##### 抛出异常
* 无

---

### 首页banner广告位

#### 请求URL
* /api/ads/get_index_banner_list

##### 请求方式
* POST

#### 请求示例
```
{
    page_number:1,
    page_size:5,
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| page_number | 否 | int | 页码 |
| page_size | 否 | int | 每页数量 |



#### 返回示例
```
[
    {
        "id": 2,
        "type": 2,
        "image_path": "http://img.fang88.com/6db7e8259f10753ea314ab6d7e1c7dae.jpeg",  // 图片地址
        "url": "http://fang88.me",          // 链接
        "title": "test02",                  // 标题
        "abstract": "链家投放"               // 简介
    }
]
```

##### 抛出异常
* 无

---

### 推荐城市

#### 请求URL
* /api/ads/get_recommend_city

##### 请求方式
* POST

#### 请求示例
```
{
    page_number:1,
    page_size:5,
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| page_number | 否 | int | 页码 |
| page_size | 否 | int | 每页数量 |



#### 返回示例
```
[
    {
        "url": "http://fang88.me/profile/ask",  // 链接
        "title": "西雅图"                        // 城市
    }
]
```

##### 抛出异常
* 无

---


## DataResourceController 资源

### 获取音频资源

#### 请求URL
* /api/dataResource/getAudioList

##### 请求方式
* POST

#### 请求示例1
```
{
	"page_number":1,
	"page_size":4
}
```

##### 请求参数
| 参数 | 必选 | 类型 | 说明 | 
| --- | --- | --- | --- |
| page_number | false | int | 页码 |
| page_size | false | int | 每页数 |

#### 返回示例
```
[
    {
        "unique_id": "4639d42dca303ed13d42aa305f7059a4",
        "type": 3,
        "cover": "http://img.fang88.com/d09e43f245c9b7ae54449ba4c01ef7e4.jpeg",  // 封面
        "title": "test02", // 标题
        "abstract": "test02",  // 简介
        "file_path": "http://img.fang88.com/2fb6cc307dd8e8a2d0be6d8bfbcaee5c.png",  // 链接
        "time_upd": "2017-12-07T13:32:33+0000",   // 更新时间
        "total_visit_count": 0, // 浏览数
        "total_share_count": 0, // 分享数
        "tags": [   
            "test"    // 标签
        ]
    }
]
```

##### 返回参数说明
| 参数 | 含义 | 说明 |
| --- | --- | --- |
|  |  |  |

##### 抛出异常
* 无

---

