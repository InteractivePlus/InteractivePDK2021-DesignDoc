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
    - [0.5 UserEntity定义](#05-userentity定义)
    - [0.6 `LoginFailedReason`登陆失败原因](#06-loginfailedreason登陆失败原因)
    - [0.7 服务端格式同步](#07-服务端格式同步)
  - [1.0 用户系统](#10-用户系统)
    - [1.1 注册用户](#11-注册用户)
      - [1.1.1 请求方式](#111-请求方式)
      - [1.1.2 参数](#112-参数)
      - [1.1.3 返回值](#113-返回值)
    - [1.2 验证邮箱](#12-验证邮箱)
      - [1.2.1 请求方式](#121-请求方式)
      - [1.2.2 参数](#122-参数)
      - [1.2.3 返回值](#123-返回值)
    - [1.3 验证手机](#13-验证手机)
      - [1.3.1 请求方式](#131-请求方式)
      - [1.3.2 参数](#132-参数)
      - [1.3.3 返回值](#133-返回值)
    - [1.4 请求邮箱验证重发](#14-请求邮箱验证重发)
      - [1.4.1 请求方式](#141-请求方式)
      - [1.4.2 参数](#142-参数)
      - [1.4.3 返回值](#143-返回值)
    - [1.5 请求手机验证重发](#15-请求手机验证重发)
      - [1.5.1 请求方式](#151-请求方式)
      - [1.5.2 参数](#152-参数)
      - [1.5.3 返回值](#153-返回值)
    - [1.6 登录](#16-登录)
      - [1.6.1 请求方式](#161-请求方式)
      - [1.6.2 参数](#162-参数)
      - [1.6.3 返回值](#163-返回值)
        - [1.6.3.1 失败时定义](#1631-失败时定义)
        - [1.6.3.2 成功时定义](#1632-成功时定义)
    - [1.7 验证token](#17-验证token)
      - [1.7.1 请求方式](#171-请求方式)
      - [1.7.2 参数](#172-参数)
      - [1.7.3 返回值](#173-返回值)
    - [1.8 刷新登录凭据](#18-刷新登录凭据)
      - [1.8.1 请求方式](#181-请求方式)
      - [1.8.2 参数](#182-参数)
      - [1.8.3 返回值](#183-返回值)
    - [1.9 登出](#19-登出)
      - [1.9.1 请求方式](#191-请求方式)
      - [1.9.2 参数](#192-参数)
      - [1.9.3 返回值](#193-返回值)
    - [1.10 请求一个新的更改密保邮箱的验证码](#110-请求一个新的更改密保邮箱的验证码)
      - [1.10.1 请求方式](#1101-请求方式)
      - [1.10.2 参数](#1102-参数)
      - [1.10.3 返回值](#1103-返回值)
    - [1.11 请求一个新的更改密保手机的验证码](#111-请求一个新的更改密保手机的验证码)
      - [1.11.1 请求方式](#1111-请求方式)
      - [1.11.2 参数](#1112-参数)
      - [1.11.3 返回值](#1113-返回值)
    - [1.12 更改/添加密保邮箱](#112-更改添加密保邮箱)
      - [1.12.1 请求方式](#1121-请求方式)
      - [1.12.2 参数](#1122-参数)
        - [1.12.2.1 添加密保邮箱时参数](#11221-添加密保邮箱时参数)
        - [1.12.2.2 更改密保邮箱时参数](#11222-更改密保邮箱时参数)
      - [1.12.3 返回值](#1123-返回值)
    - [1.13 更改/添加密保手机](#113-更改添加密保手机)
      - [1.13.1 请求方式](#1131-请求方式)
      - [1.13.2 参数](#1132-参数)
        - [1.13.2.1 添加密保手机时参数](#11321-添加密保手机时参数)
        - [1.13.2.2 更改密保手机时参数](#11322-更改密保手机时参数)
      - [1.13.3 返回值](#1133-返回值)
    - [1.14 请求一个更改密码/忘记密码的验证码](#114-请求一个更改密码忘记密码的验证码)
      - [1.14.1 请求方式](#1141-请求方式)
      - [1.14.2 参数](#1142-参数)
        - [1.14.2.1 更改密码参数](#11421-更改密码参数)
        - [1.14.2.2 重设密码参数](#11422-重设密码参数)
      - [1.14.3 返回值](#1143-返回值)
    - [1.15 更改密码/重设密码](#115-更改密码重设密码)
      - [1.15.1 请求方式](#1151-请求方式)
      - [1.15.2 参数](#1152-参数)
        - [1.15.2.1 更改密码参数](#11521-更改密码参数)
        - [1.15.2.2 重设密码参数](#11522-重设密码参数)
      - [1.15.3 返回值](#1153-返回值)

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

### 0.5 UserEntity定义

UserEntity经常在API中作为一个数据类型被返回, 实际UserEntity也是一个JSON Object, 具体格式如下:

```json
{
    "uid": 0,
    "username": "User Username",
    "nickname": "User Nickname",
    "signature": "User Signature",
    "email": "Email Address",
    "phone": "Phone Number in E164 Format",
    "emailVerified": true,
    "phoneVerified": true,
    "accountFrozen": false
}
```

看完例子来看一下UserEntity的数据定义吧

|键值|类型|可选|注释|
|-|-|-|-|
|uid|int|-|用户uid|
|username|string|-|用户名|
|nickname|?string|-|用户昵称(如果为空, 则null)|
|signature|?string|-|用户签名(如果为空, 则null)|
|email|?string|-|用户邮箱(如果没有绑定, 则null)|
|phone|?string|-|用户手机, E164格式(如果没有绑定, 则null)|
|emailVerified|bool|-|用户邮箱是否已验证|
|phoneVerified|bool|-|用户手机是否已验证|
|accountFrozen|bool|-|用户是否冻结|

---
**还是不懂?**   
如果一个API返回了UserEntity, 如[登录功能](#1632-成功时定义), 则API返回值会如下所示(以登录功能为例)

```json
{
    "errorCode": 0,
    "data": {
        "access_token": "xxxx",
        "refresh_token": "xxx",
        "access_expire": 11283901,
        "refresh_expire": 12319890,
        "user": {
            "uid": 1,
            "username": "toiletcommander",
            "nickname": "老秋风",
            "signature": "哇我爱糖糖, 糖糖怎么那么好看, 声音又好听",
            "email": "windy@philosophysoftware.org",
            "phone": "+86xxxxxxxxxxx",
            "emailVerified": true,
            "phoneVerified": true,
            "accountFrozen": false
        }
    }
}
```

### 0.6 `LoginFailedReason`登陆失败原因
见[PDK-2021CoreLib中LoginFailedReasons.php](https://github.com/InteractivePlus/PDK2021-CoreLib/blob/main/src/User/Login/LoginFailedReasons.php)

|FAILED_REASON|登陆失败原因|id|
|-|-|-|
|EMAIL_NOT_VERIFIED|邮箱未验证|1|
|PHONE_NOT_VERIFIED|手机未验证|2|
|EITHER_NOT_VERIFIED|同时绑定了邮箱和手机, 没有任何一个验证了|3|
|ACCOUNT_FROZEN|用户被冻结|4|
|UNKNOWN|未知原因|5|

### 0.7 服务端格式同步
因为PDK2021的可配置性, 许多变量的格式在不同的部署实例中是不同的, 要了解具体什么需要配置, 请参照下面的链接.

**强烈建议在实现前端时将`UserSystemFormatSetting`写成一个可以更改的类文件**

- [VeriCodeFormat / 验证码格式定义, 定长32个字符(base16)](https://github.com/InteractivePlus/PDK2021-CoreLib/blob/main/src/Communication/VerificationCode/VeriCodeFormat.php)
  - 注: 手机验证码定长6个字符, 虽然字符数少了但是请求时需要带上`uid`
- [TokenFormat / 登录凭据和刷新凭据定义, 定长32个字符(base16)](https://github.com/InteractivePlus/PDK2021-CoreLib/blob/main/src/User/Formats/TokenFormat.php)
- [PasswordHash / 密码哈希, 定长64个字符(base16, SHA256)](https://github.com/InteractivePlus/PDK2021-CoreLib/blob/main/src/User/Formats/TokenFormat.php)
- [UserSystemFormatSetting / 用户系统可变定义](https://github.com/InteractivePlus/PDK2021-CoreLib/blob/main/src/User/UserSystemFormatSetting.php)
- [UserSystemFormatSetting / 用户系统可变定义服务端实现,见`USER_SYSTEM_CONSTRAINTS`](https://github.com/InteractivePlus/PDK2021-Wrapper/blob/main/src/Config_template.php)

## 1.0 用户系统

### 1.1 注册用户

这个API用来让没有形随意动账号的用户注册

---

#### 1.1.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|POST|/user|201 CREATED|

#### 1.1.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|username|string|-|用户名|YES|
|password|string|-|密码|YES|
|email|string|YES|邮箱|YES|
|phone|string|YES|手机号, 需要用E164格式化(+86xxxxxxxxxxx)|YES|

**注意**: email和phone必填一项

#### 1.1.3 返回值
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
|-|-|-|
|GET|/vericodes/verifyEmailResult/`{{veriCode}}`|200 OK|

#### 1.2.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|veriCode|string|-|请填入URL中|YES|

#### 1.2.3 返回值
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
|-|-|-|
|GET|/vericodes/verifyPhoneResult/`{{veriCode}}`|200 OK|

#### 1.3.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|新注册用户的uid([注册](#113-返回值) 登录失败时也会提供)|YES|
|veriCode|string|-|填入URL|YES|

#### 1.3.3 返回值
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
|-|-|-|
|POST|/vericodes/sendAnotherVerifyEmailRequest|201 CREATED|

#### 1.4.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|email|string|-|邮箱地址|YES|

#### 1.4.3 返回值
成功时`dataKey-data`定义: 空

成功时`rootKey-data`定义: 无特殊键值

### 1.5 请求手机验证重发
这个API用来让新注册用户/刚刚修改密保手机的用户重新发送验证手机的短消息/语音电话

---

#### 1.5.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|POST|/vericodes/sendAnotherVerifyPhoneRequest|201 CREATED|

#### 1.5.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|phone|string|-|手机号, E164格式|YES|
|preferred_send_method|int|YES|偏好发送方式(`SMS_MESSAGE`/`PHONE_CALL`)|YES|

#### 1.5.3 返回值
成功时`dataKey-data`定义: 

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|sent_method|int|-|验证码发送方式|YES|

成功时`rootKey-data`定义: 无特殊键值

### 1.6 登录

这个API用来让已验证用户登录并获取token

---

#### 1.6.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|POST|/user/token|201 CREATED|

#### 1.6.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|username|?string|YES|登录用户名|YES|
|email|?string|YES|登录邮箱|YES|
|phone|?string|YES|登录手机号, 格式E164|YES|
|password|string|-|密码|YES|

注: `username`,`email`,`phone`选一样填就行了, 有且只有一项可以填(不然会按优先级`username`>`email`>`phone`来选一项查找账号)

#### 1.6.3 返回值

##### 1.6.3.1 失败时定义

`dataKey-data`定义: 无特殊键值

`rootKey-data`定义: 

|键值|类型|可选|注释|
|-|-|-|-|
|errorReason|int|-|登录错误原因|

---

**特殊情况**: 用户没有验证邮箱/手机返回:

`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|email|?string|YES|用户邮箱(如果用户有邮箱且没有验证)|
|phone|?string|YES|用户手机(如果用户有手机且没有验证)|
|uid|?int|YES|用户uid(如果用户有手机且没有验证)|

`rootKey-data`定义: 继承[1.2.3.1 失败时定义](#1231-失败时定义)


##### 1.6.3.2 成功时定义

`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|access_token|string|-|用户登录凭据|
|refresh_token|string|-|刷新凭据|
|expire_time|int|-|登录凭据过期时间(UTC时间 Unix Timestamp)|
|refresh_expire|int|-|刷新凭据过期时间(UTC时间 Unix Timestamp)|
|user|[`UserEntity`](#05-userentity定义)|-|用户详细信息|

`rootKey-data`定义: 无特殊键值

### 1.7 验证token
这个API用来让已经登录的用户验证token是否可用

---

#### 1.7.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|GET|/user/{{uid}}/token/{{access_token}}/checkTokenResult|200 OK|

#### 1.7.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid, 填入URL|YES|
|access_token|string|-|登录凭据, 填入URL|YES|

#### 1.7.3 返回值
成功时`dataKey-data`定义: 空

成功时`rootKey-data`定义: 无特殊键值

### 1.8 刷新登录凭据
为了让用户无需重复登录, 刷新登录凭据API可以让用户通过刷新凭据来刷新登录凭据

---

#### 1.8.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|GET|/user/{{uid}}/token/refreshResult|201 CREATED|

#### 1.8.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid, 填入URL|YES|
|refresh_token|string|-|刷新凭据|YES|

#### 1.8.3 返回值
成功时`dataKey-data`定义: 

|键值|类型|可选|注释|
|-|-|-|-|
|access_token|string|-|新的用户登录凭据|
|refresh_token|string|-|新的刷新凭据|
|expire_time|int|-|新登录凭据过期时间(UTC时间 Unix Timestamp)|
|refresh_expire|int|-|新刷新凭据过期时间(UTC时间 Unix Timestamp)|
|user|[`UserEntity`](#05-userentity定义)|-|用户详细信息|

成功时`rootKey-data`定义: 无特殊键值

### 1.9 登出

普通网站的登出仅仅是删除本地Cookie, 而InterActivePDK为了增强安全, 设定登出API来禁用当前登录凭据.

**由于登出完全可在本地实现, 这里要求前端仅对此API进行调用, 无需处理返回值**

---

#### 1.9.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|DELETE|/user/{{uid}}/token/{{access_token}}|204 NO CONTENT|

#### 1.9.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid, 填入URL|YES|
|access_token_token|string|-|登录凭据, 填入URL|YES|

#### 1.9.3 返回值

**只有失败时才有返回值**, 如果成功返回值一定是空的

### 1.10 请求一个新的更改密保邮箱的验证码

这个API用来让已经绑定密保邮箱的用户更改密保邮箱

---

#### 1.10.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|POST|/vericodes/changeEmailAddrRequest|201 CREATED|

#### 1.10.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid|YES|
|access_token|string|-|登录凭据|YES|
|new_email|string|-|新邮件地址|YES|
|preferred_send_method|int|YES|偏好发送方式(`EMAIL`/`SMS_MESSAGE`/`PHONE_CALL`)|YES|

#### 1.10.3 返回值

注: 如果用户没有绑定邮箱, 则会返回错误代码`PERMISSION_DENIED`   

成功时`dataKey-data`定义: 

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|sent_method|int|-|验证码发送方式|YES|

成功时`rootKey-data`定义: 无特殊键值

### 1.11 请求一个新的更改密保手机的验证码

这个API用来让已经绑定密保手机的用户更改密保邮箱

---

#### 1.11.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|POST|/vericodes/changePhoneNumberRequest|201 CREATED|

#### 1.11.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid|YES|
|access_token|string|-|登录凭据|YES|
|new_phone|string|-|新手机号码, E164格式|YES|
|preferred_send_method|int|YES|偏好发送方式(`EMAIL`/`SMS_MESSAGE`/`PHONE_CALL`)|YES|

#### 1.11.3 返回值

注: 如果用户没有绑定手机, 则会返回错误代码`PERMISSION_DENIED`   

成功时`dataKey-data`定义: 

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|sent_method|int|-|验证码发送方式|YES|

成功时`rootKey-data`定义: 无特殊键值


### 1.12 更改/添加密保邮箱

这个API用来让已经绑定密保邮箱/没有绑定密保邮箱的用户更改/添加密保邮箱

---

#### 1.12.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|PATCH|/user/email|200 OK|

#### 1.12.2 参数

##### 1.12.2.1 添加密保邮箱时参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid|YES|
|access_token|string|-|登录凭据|YES|
|new_email|string|-|新邮件地址|YES|

##### 1.12.2.2 更改密保邮箱时参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|YES|用户uid, 使用手机短验证码时使用|YES|
|veriCode|string|-|验证码, 从[1.10](#110-请求一个新的更改密保邮箱的验证码)|YES|

#### 1.12.3 返回值
成功时`dataKey-data`定义: 无特殊键值

成功时`rootKey-data`定义: 无特殊键值

### 1.13 更改/添加密保手机

这个API用来让已经绑定密保手机/没有绑定密保手机的用户更改/添加密保手机

---
#### 1.13.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|PATCH|/user/phoneNum|200 OK|

#### 1.13.2 参数

##### 1.13.2.1 添加密保手机时参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid|YES|
|access_token|string|-|登录凭据|YES|
|new_phone|string|-|新手机号, E164格式|YES|

##### 1.13.2.2 更改密保手机时参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|YES|用户uid, 使用手机短验证码时使用|YES|
|veriCode|string|-|验证码, 从[1.11](#111-请求一个新的更改密保手机的验证码)获得|YES|

#### 1.13.3 返回值

成功时`dataKey-data`定义: 无特殊键值

成功时`rootKey-data`定义: 无特殊键值

### 1.14 请求一个更改密码/忘记密码的验证码
这个API用来让用户请求更改密码/重设密码

---

#### 1.14.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|POST|/vericodes/changePasswordRequest|201 CREATED|

#### 1.14.2 参数

##### 1.14.2.1 更改密码参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid|YES|
|access_token|string|-|登录凭据|YES|
|preferred_send_method|int|-|验证码发送偏好`EMAIL`/`SMS_MESSAGE`/`PHONE_CALL`|YES|

##### 1.14.2.2 重设密码参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|email|string|YES|申请密码重设的邮箱|YES|
|phone|string|YES|申请密码重设的手机, E164格式|YES|
|username|string|YES|申请密码重设的用户名|YES|
|preferred_send_method|int|-|验证码发送偏好`EMAIL`/`SMS_MESSAGE`/`PHONE_CALL`|YES|

注: `email`, `phone`, `username`其中必填且只能填一个.

#### 1.14.3 返回值

注: 如果用户没有验证账户或账户被冻结, 会返回`PERMISSION_DENIED`错误, 且`rootKey-data`会包含`errorReason`, 其值为[登录失败原因](#06-loginfailedreason登陆失败原因)之一.   

成功时`dataKey-data`定义: 

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|sent_method|int|-|验证码发送方式|YES|

成功时`rootKey-data`定义: 无特殊键值

### 1.15 更改密码/重设密码
这个API用来让用户更改密码/重设密码

---

#### 1.15.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|PATCH|/user/password|200 OK|

#### 1.15.2 参数

##### 1.15.2.1 更改密码参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|YES|用户uid, 使用手机验证码时填写|YES|
|veriCode|string|-|验证码|YES|
|new_password|string|-|新密码|YES|

##### 1.15.2.2 重设密码参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|username|string|YES|用户名|YES|
|email|string|YES|邮箱|YES|
|phone|string|YES|手机, E164格式|YES|
|veriCode|string|-|验证码|YES|
|new_password|string|-|新密码|YES|

注: 当使用手机验证码时,`email`, `phone`, `username`其中必填且只能填一个.

#### 1.15.3 返回值

成功时`dataKey-data`定义: 无特殊键值

成功时`rootKey-data`定义: 无特殊键值
