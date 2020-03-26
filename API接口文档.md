## API接口

### 1. 规则

- 服务端API地址：http://teach.yiibook.top/api/v1
- 进行接口调用时，在URI地址前增加服务端API地址，文档中对该地址进行省略。
- POST方式传递参数时，请传递JSON格式，GET方式参数传递时，可以将参数放到URL地址后面。
- 返回参数状态status说明：200成功 400错误 401未授权 500服务器错误

### 2. 接口

#### 2.1 用户登录

- 接口地址：/user/login
- 请求方式：POST
- Request

```json
{
	"username": "yiibook",
	"password": "123456"
}
```

- Response

```json
{
    "status": 200,
    "message": "登录成功",
    "data": {
        "id": 40, # 用户ID
        "username": "yiibook",
        "realname": "许文龙" # 真实姓名
    },
    "timestamp": 1583885795
}
```

#### 2.2 获取任务列表

- 接口地址：/info/lists
- 请求方式：GET
- Request：/info/lists?user_id=XX
- Response:

```json
{
    "status": 200,
    "message": "获取成功",
    "data": [
        {
            "id": 5, # 任务ID
            "title": "今天19级程序设计语言上课", # 任务标题
            "is_complete": 0  # 状态 1 已完成 0 未完成
        },
        {
            "id": 3,
            "title": "生产服务器测试",
            "is_complete": 0
        }
    ],
    "timestamp": 1583887362
}
```

#### 2.3 创建任务

- 接口地址：/info/create
- 请求方式：POST
- Request：

```json
{
	"user_id": 40, # 用户ID，用于授权认证，实际开发中大多数采用token认证方式
	"title": "写接口文档" # 任务标题
}
```

- Response:

```json
{
    "status": 200,
    "message": "创建成功",
    "data": null,
    "timestamp": 1583887652
}
```

#### 2.4 修改任务状态

- 接口地址：/info/change
- 请求方式：POST
- Request：

```json
{
	"user_id": 40,
	"note_id": 3 # 任务ID
}
```

- Response：

```json
{
    "status": 200,
    "message": "任务状态设置成功",
    "data": null,
    "timestamp": 1583887905
}
```

#### 2.5 删除任务

- 接口地址：/info/delete
- 请求方式：POST
- Request：

```json
{
	"user_id": 40,
	"note_id": 3
}
```

- Response:

```json
{
    "status": 200,
    "message": "任务删除成功",
    "data": null,
    "timestamp": 1583888034
}
```

#### 2.6 清空任务

- 接口地址：/info/clear
- 请求方式：POST
- Request：

```json
{
	"user_id": 40
}
```

- Response:

```json
{
    "status": 200,
    "message": "任务清空成功",
    "data": null,
    "timestamp": 1583888158
}
```

