# API定义
 [返回](README.md)   
 此文档将定义InteractivePDK2021开发过程中前端和后端的交互流程

## 目录

- [API定义](#api定义)
  - [目录](#目录)
  - [0.0 公共常数及API约定](#00-公共常数及api约定)
    - [0.1 发送方式(SEND_METHOD)](#01-发送方式send_method)
    - [0.2 错误代码(errorCode)](#02-错误代码errorcode)
    - [0.3 通用返回格式](#03-通用返回格式)
    - [0.4 API参数发送方式](#04-api参数发送方式)
  - [1.0 用户系统](#10-用户系统)
    - [1.1 注册用户](#11-注册用户)
      - [1.1.1 请求方式](#111-请求方式)
      - [1.1.2 参数](#112-参数)
      - [1.1.3 返回值:](#113-返回值)
    - [1.2 验证邮箱](#12-验证邮箱)
      - [1.2.1 请求方式](#121-请求方式)
      - [1.2.2 参数](#122-参数)
      - [1.2.3 返回值:](#123-返回值)
    - [1.3 验证手机](#13-验证手机)
      - [1.3.1 请求方式](#131-请求方式)
      - [1.3.2 参数](#132-参数)
      - [1.3.3 返回值:](#133-返回值)
    - [1.4 请求邮箱验证重发](#14-请求邮箱验证重发)
      - [1.4.1 请求方式](#141-请求方式)
      - [1.4.2 参数](#142-参数)
      - [1.4.3 返回值:](#143-返回值)
    - [1.5 请求手机验证重发](#15-请求手机验证重发)
      - [1.5.1 请求方式](#151-请求方式)
      - [1.5.2 参数](#152-参数)
      - [1.5.3 返回值:](#153-返回值)

## 0.0 公共常数及API约定

### 0.1 发送方式(SEND_METHOD)
见[PDK2021-CoreLib中SentMethod.php](https://github.com/InteractivePlus/PDK2021-CoreLib/blob/main/src/Communication/CommunicationMethods/SentMethod.php)中的定义.

|METHOD_NAME|发送方式|发送id|
|-|-|-|
|NOT_SENT|没有发送|0|
|EMAIL|用邮箱发送|1|
|SMS_MESSAGE|用短信发送|2|
|PHONE_CALL|用电话语音发送|3|

### 0.2 错误代码(errorCode)
见[PDK2021-CoreLib中PDKErrCode.php](https://github.com/InteractivePlus/PDK2021-CoreLib/blob/main/src/Base/Exception/PDKErrCode.php)中的定义.

|ERROR_CODE_NAME|错误类型|错误代码|错误参数|
|-|-|-|-|
|NO_ERROR|没有错误|0|-|
|UNKNOWN_INNER_ERROR|未知内部错误|1|-|
|STORAGE_ENGINE_ERROR|储存系统(内部数据库)错误|2|-|
|INNER_ARGUMENT_ERROR|内部传参错误|3|errorParam|
|SENDER_SERVICE_ERROR|发件系统(邮件,短信,电话语音)错误|4|-|
|ITEM_NOT_FOUND_ERROR|没有在储存系统中找到指定的请求参数(Token不存在,用户不存在等等)|10|item|
|ITEM_ALREADY_EXIST_ERROR|储存系统中已经有指定请求参数(邮件重复, 电话号码重复等等)|11|item|
|ITEM_EXPIRED_OR_USED_ERROR|此请求参数已经被使用(token, 验证码等)|12|item|
|PERMISSION_DENIED|权限禁止|13|-|
|CREDENTIAL_NOT_MATCH|用户凭据不正确(密码错误, token错误等)|20|credential|

### 0.3 通用返回格式

先上JSON格式的数据, 所有请求的返回值都会是一个JSON字符串(除了成功的[HTTP DELETE](#04-api参数发送方式))

```json
{
    "errorCode": 0,
    "errorDescription": "这里真的没有错误!",
    "errorFile": "错误文件在哪里?",
    "errorLine": 0,
    "data": {
        "data1": "xxx",
        "data2": "xxxx",
        ...
    },
    "additional-error-params-1": "xxx",
    "additional-error-params-2": "xxx",
    ...,
    "user-defined-root-data-1": "value1",
    "user-defined-root-data-2": "value2",
    ...
}
```

在这里`additional-error-params`指的是[0.2 错误代码](#02-错误代码errorcode)中定义的`错误参数`名称.

---

在看完示例后我们再看看具体这个JSON格式的数据的键值在什么时候会出现

|键值(key)|数据类型|可选|注释|
|-|-|-|-|
|errorCode|int|-|-|
|errorDescription|?string|YES|只有在有错误的时候显示|
|errorFile|?string|YES|只有在有错误且后端开启错误详细信息显示时显示|
|errorLine|?int|YES|只有在有错误且后端开启错误详细信息显示时显示|
|data|?array|YES|只有后端返回数据时显示(见特定API定义, 如果API的`dataKey-data`定义表为空则此键为空)|
|errorParam|?string|YES|只有特定错误代码会包含, 见[0.2 错误代码](#02-错误代码errorcode)|
|item|?string|YES|只有特定错误代码会包含, 见[0.2 错误代码](#02-错误代码errorcode)|
|credential|?string|YES|只有特定错误代码会包含, 见[0.2 错误代码](#02-错误代码errorcode)|
|user-defined-root-data|mixed|YES|只有特定API会返回, 见特定API的`rootKey-data`定义表|

### 0.4 API参数发送方式

在执行API请求时, 不同的HTTP Method有不同的参数接收方式

|HTTP METHOD|参数发送方式|发送内容|注释|
|-|-|-|-|
|GET|URL?variable1=Val1&variable2=Val2|-|-|
|POST|Request Body|json_encode(param_array)|-|
|PATCH|Request Body|json_encode(param_array)|-|
|DELETE|Request Body|json_encode(param_array)|如果成功删除资源, 返回值会为空, 请用HTTP Code来判断成功|

注: 如果API定义的URL中有`{{variableName}}`则用变量值替代`{{variableName}}`, 且请求体中无需再次包含变量.

## 1.0 用户系统

### 1.1 注册用户

这个API用来让没有形随意动账号的用户注册

---

#### 1.1.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|-|
|POST|/user|201 CREATED|

#### 1.1.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|username|string|-|用户名|YES|
|password|string|-|密码|YES|
|email|string|YES|邮箱|YES|
|phone|string|YES|手机号, 需要用E164格式化(+86xxxxxxxxxxx)|YES|

**注意**: email和phone必填一项

#### 1.1.3 返回值:
成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|uid|int|-|新注册的用户的uid|
|username|string|-|新注册的用户的用户名|
|email|?string|YES|新注册的用户邮箱(如果注册时提供了)|
|phone|?string|YES|新注册的手机号(如果注册时提供了), E164格式|
|phoneVerificationSentMethod|int|NO|手机验证码发送方式(如果注册时提供了), 如果没有提供, 值为`NOT_SENT`|

成功时`rootKey-data`定义: 无特殊键值

### 1.2 验证邮箱

这个API用来让新注册用户/刚刚修改密保邮箱的用户验证新邮箱地址

---

#### 1.2.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|-|
|GET|/vericodes/verifyEmailResult/`{{veriCode}}`|200 OK|

#### 1.2.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|veriCode|string|-|请填入URL中|YES|

#### 1.2.3 返回值:
成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|username|string|-|已验证的用户的用户名|
|nickname|?string|YES|已验证的用户的昵称(如果为空, 则键值为null, 键仍存在)|
|email|string|-|已验证的用户邮箱|

成功时`rootKey-data`定义: 无特殊键值

### 1.3 验证手机

这个API用来让新注册用户/刚刚修改密保手机的用户验证手机号码

---

#### 1.3.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|-|
|GET|/vericodes/verifyPhoneResult/`{{veriCode}}`|200 OK|

#### 1.3.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|新注册用户的uid([注册](#113-返回值) 登录失败时也会提供)|YES|
|veriCode|string|-|填入URL|YES|

#### 1.3.3 返回值:
成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|username|string|-|已验证的用户的用户名|
|nickname|?string|YES|已验证的用户的昵称(如果为空, 则键值为null, 键仍存在)|
|phone|string|-|已验证的用户手机, E164格式|

成功时`rootKey-data`定义: 无特殊键值

### 1.4 请求邮箱验证重发
这个API用来让新注册用户/刚刚修改密保邮箱的用户重新发送验证邮箱的邮件

---

#### 1.4.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|-|
|POST|/vericodes/sendAnotherVerifyEmailRequest|201 CREATED|

#### 1.4.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|email|string|-|邮箱地址|YES|

#### 1.4.3 返回值:
成功时`dataKey-data`定义: 空

成功时`rootKey-data`定义: 无特殊键值

### 1.5 请求手机验证重发
这个API用来让新注册用户/刚刚修改密保手机的用户重新发送验证手机的短消息/语音电话

---

#### 1.5.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|-|
|POST|/vericodes/sendAnotherVerifyPhoneRequest|201 CREATED|

#### 1.5.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|phone|string|-|手机号, E164格式|YES|
|preferred_send_method|int|YES|偏好发送方式(`SMS_MESSAGE`/`PHONE_CALL`)|YES|

#### 1.5.3 返回值:
成功时`dataKey-data`定义: 空

成功时`rootKey-data`定义: 无特殊键值