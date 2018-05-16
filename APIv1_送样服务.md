# 用户信息

* [获取单个送样](#user-content-获取单个送样)
* [获取多个送样](#user-content-获取多个送样)
* [添加送样](#user-content-添加送样)
* [修改送样](#user-content-修改送样)
* [删除送样](#user-content-删除送样)

> 请及时更新文档 任何人发现文档和接口不符请及时通知团队维护者 

## 获取单个送样

通用获取单个送样接口

```
GET /sample/:id
```

### 响应

``` javascript
Status: 200 OK
-
{
  "id": 1, // 送样ID
  "user": 1, // 送样者的Yiqikong-User ID
  "operator": 1, // 操作者的Yiqikong-User ID
  "equipment": "93724601f8c10f4953face21c4e9a472ef43cc46", // 送样的目标仪器UUID
  "start_time": "2018-01-01", // 测样开始时间
  "end_time": "2018-01-01", // 测样结束时间
  "submit_time": "2018-01-01", // 送样时间
  "pickup_time": "2018-01-01", // 取样时间
  "status": 0, // 送样状态
  "samples": 5, // 送样数
  "success_samples": 3, // 送样成功数
  "note": "备注", // 备注
  "description": "氯化钠 300ml", // 描述
  "source_name": 'swu', // 来源
  "source_id": 1,
  "mtime": "2018-01-01", // 修改时间
  "ctime": "2018-01-01", // 创建时间
}
```

``` javascript
Status: 404 Not Found
-
"没有找到对应的送样信息"
```

## 获取多个送样

通用获取多送样接口

```
GET /sample
```

### 参数

``` javascript
{
  "equipment": "93724601f8c10f4953face21c4e9a472ef43cc46", // 送样的目标仪器UUID
  "user": 1, // 送样者ID
  "operator": 1, // 操作人ID
  "start_time": ["gt", "2018-01-01"], // 测样开始时间 
  "end_time": ["lt", "2018-01-01"], // 测样结束时间 
  "submit_time": ["bt", "2018-01-01"], // 送样时间
  "pickup_time": ["le", "2018-01-01"], // 取样时间
  "status": ['in', 0, 1, 2, 3], // 状态
  "sortby": "name", // 排序字段
  "order": "desc", // 排序方式
  "limit": [0, 20], // 分页筛选
}
```

### 响应

``` javascript
Status: 200 OK
-
{}
  "total": 100,
  "data": [
    {
      "id": 1, // 送样ID
      "user": 1, // 送样者的Yiqikong-User ID
      "operator": 1, // 操作者的Yiqikong-User ID
      "equipment": "93724601f8c10f4953face21c4e9a472ef43cc46", // 送样的目标仪器UUID
      "start_time": "2018-01-01", // 测样开始时间
      "end_time": "2018-01-01", // 测样结束时间
      "submit_time": "2018-01-01", // 送样时间
      "pickup_time": "2018-01-01", // 取样时间
      "status": 0, // 送样状态
      "samples": 5, // 送样数
      "success_samples": 3, // 送样成功数
      "note": "备注", // 备注
      "description": "氯化钠 300ml", // 描述
      "source_name": 'swu', // 来源
      "source_id": 1,
      "mtime": "2018-01-01", // 修改时间
      "ctime": "2018-01-01", // 创建时间
    },
    ...
  ]
}
```

## 添加送样

通用添加送样接口

```
POST /sample
```

### 参数

``` javascript
{
  "id": 1, // 送样仪器控ID
  "user": 1, // 送样者的Yiqikong-User ID
  "operator": 1, // 操作者的Yiqikong-User ID
  "equipment": "93724601f8c10f4953face21c4e9a472ef43cc46", // 送样的目标仪器UUID
  "start_time": "2018-01-01", // 测样开始时间
  "end_time": "2018-01-01", // 测样结束时间
  "submit_time": "2018-01-01", // 送样时间
  "pickup_time": "2018-01-01", // 取样时间
  "status": 0, // 送样状态
  "samples": 5, // 送样数
  "success_samples": 3, // 送样成功数
  "note": "备注", // 备注
  "description": "氯化钠 300ml", // 描述
  "source_name": 'swu', // 来源
  "source_id": 1,
  "mtime": "2018-01-01", // 修改时间
  "ctime": "2018-01-01", // 创建时间
}
```

### 响应

``` javascript
Status: 200 OK
-
{
  "id": 1, // 送样ID
  "user": 1, // 送样者的Yiqikong-User ID
  "operator": 1, // 操作者的Yiqikong-User ID
  "equipment": "93724601f8c10f4953face21c4e9a472ef43cc46", // 送样的目标仪器UUID
  "start_time": "2018-01-01", // 测样开始时间
  "end_time": "2018-01-01", // 测样结束时间
  "submit_time": "2018-01-01", // 送样时间
  "pickup_time": "2018-01-01", // 取样时间
  "status": 0, // 送样状态
  "samples": 5, // 送样数
  "success_samples": 3, // 送样成功数
  "note": "备注", // 备注
  "description": "氯化钠 300ml", // 描述
  "source_name": 'swu', // 来源
  "source_id": 1,
  "mtime": "2018-01-01", // 修改时间
  "ctime": "2018-01-01", // 创建时间
}
```

``` javascript
Status: 400 Bad Request
-
"参数错误"
```

``` javascript
Status: 500 Server Error
-
"服务器异常"
```

## 修改送样

通用修改送样接口

```
PUT /sample/:id // 利用ctrl id定位
PUT /sample {"source_name": "swu", "source_id": 1} // 利用source定位
PUT /sample {"id": 1} // 利用yiqikong_id 定位
```

### 参数

``` javascript
{
  "id": 1, // 送样仪器控ID
  "user": 1, // 送样者的Yiqikong-User ID
  "operator": 1, // 操作者的Yiqikong-User ID
  "equipment": "93724601f8c10f4953face21c4e9a472ef43cc46", // 送样的目标仪器UUID
  "start_time": "2018-01-01", // 测样开始时间
  "end_time": "2018-01-01", // 测样结束时间
  "submit_time": "2018-01-01", // 送样时间
  "pickup_time": "2018-01-01", // 取样时间
  "status": 0, // 送样状态
  "samples": 5, // 送样数
  "success_samples": 3, // 送样成功数
  "note": "备注", // 备注
  "description": "氯化钠 300ml", // 描述
  "source_name": 'swu', // 来源
  "source_id": 1,
  "mtime": "2018-01-01", // 修改时间
  "ctime": "2018-01-01", // 创建时间
}
```

### 响应

``` javascript
Status: 200 OK
-
{
  "id": 1, // 送样ID
  "user": 1, // 送样者的Yiqikong-User ID
  "operator": 1, // 操作者的Yiqikong-User ID
  "equipment": "93724601f8c10f4953face21c4e9a472ef43cc46", // 送样的目标仪器UUID
  "start_time": "2018-01-01", // 测样开始时间
  "end_time": "2018-01-01", // 测样结束时间
  "submit_time": "2018-01-01", // 送样时间
  "pickup_time": "2018-01-01", // 取样时间
  "status": 0, // 送样状态
  "samples": 5, // 送样数
  "success_samples": 3, // 送样成功数
  "note": "备注", // 备注
  "description": "氯化钠 300ml", // 描述
  "source_name": 'swu', // 来源
  "source_id": 1,
  "mtime": "2018-01-01", // 修改时间
  "ctime": "2018-01-01", // 创建时间
}
```

``` javascript
Status: 400 Bad Request
-
"参数错误"
```

``` javascript
Status: 500 Server Error
-
"服务器异常"
```

## 删除送样

通用修改送样接口

```
DELETE /sample/:id // 利用ctrl id定位
DELETE /sample {"source_name": "swu", "source_id": 1} // 利用source定位
DELETE /sample {"id": 1} // 利用yiqikong_id 定位
```

### 响应

``` javascript
Status: 200 OK
-
{
  "id": 1, // 送样ID
  "source_name": 'swu', // 来源
  "source_id": 1, // ID
}
```

``` javascript
Status: 500 Server Error
-
"服务器异常"
```
