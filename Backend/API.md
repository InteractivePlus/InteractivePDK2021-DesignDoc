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
    - [0.6 LoginFailedReason登陆失败原因定义](#06-loginfailedreason登陆失败原因定义)
    - [0.7 服务端格式同步](#07-服务端格式同步)
    - [0.8 验证码系统](#08-验证码系统)
    - [0.9 APP类型定义](#09-app类型定义)
    - [0.10 APPEntity定义](#010-appentity定义)
    - [0.11 MaskID定义](#011-maskid定义)
    - [0.12 UserSettingEntity定义](#012-usersettingentity定义)
    - [0.13 OAuthScope定义](#013-oauthscope定义)
    - [0.14 OAuthToken定义](#014-oauthtoken定义)
    - [0.15 OAuthUserInfo定义](#015-oauthuserinfo定义)
    - [0.16 TicketResponse定义](#016-ticketresponse定义)
    - [0.17 TicketEntity定义](#017-ticketentity定义)
    - [0.18 MultipleResult定义](#018-multipleresult定义)
    - [0.19 UserPermissionEntity定义(提案阶段)](#019-userpermissionentity定义提案阶段)
    - [0.20 APPPermissionEntity数据类型定义](#020-apppermissionentity数据类型定义)
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
    - [1.16 更改用户信息](#116-更改用户信息)
      - [1.16.1 请求方式](#1161-请求方式)
      - [1.16.2 参数](#1162-参数)
        - [1.16.2.1 更改密码参数](#11621-更改密码参数)
      - [1.16.3 返回值](#1163-返回值)
    - [1.17 列出已有面具](#117-列出已有面具)
      - [1.17.1 请求方式](#1171-请求方式)
      - [1.17.2 参数](#1172-参数)
      - [1.17.3 返回值](#1173-返回值)
    - [1.18 添加面具](#118-添加面具)
      - [1.18.1 请求方式](#1181-请求方式)
      - [1.18.2 参数](#1182-参数)
      - [1.18.3 返回值](#1183-返回值)
    - [1.19 修改面具信息](#119-修改面具信息)
      - [1.19.1 请求方式](#1191-请求方式)
      - [1.19.2 参数](#1192-参数)
      - [1.19.3 返回值](#1193-返回值)
    - [1.20 删除面具](#120-删除面具)
      - [1.20.1 请求方式](#1201-请求方式)
      - [1.20.2 参数](#1202-参数)
      - [1.20.3 返回值](#1203-返回值)
  - [2.0 第三方OAuth APP系统](#20-第三方oauth-app系统)
    - [2.1 注册APP](#21-注册app)
      - [2.1.1 请求方式](#211-请求方式)
      - [2.1.2 参数](#212-参数)
      - [2.1.3 返回值](#213-返回值)
    - [2.2 列出已有APP](#22-列出已有app)
      - [2.2.1 请求方式](#221-请求方式)
      - [2.2.2 参数](#222-参数)
      - [2.2.3 返回值](#223-返回值)
    - [2.3 请求删除APP验证码](#23-请求删除app验证码)
      - [2.3.1 请求方式](#231-请求方式)
      - [2.3.2 参数](#232-参数)
      - [2.3.3 返回值](#233-返回值)
    - [2.4 删除已有APP](#24-删除已有app)
      - [2.4.1 请求方式](#241-请求方式)
      - [2.4.2 参数](#242-参数)
      - [2.4.3 返回值](#243-返回值)
    - [2.5 请求APP重要操作验证码](#25-请求app重要操作验证码)
      - [2.5.1 请求方式](#251-请求方式)
      - [2.5.2 参数](#252-参数)
      - [2.5.3 返回值](#253-返回值)
    - [2.6 修改APP信息](#26-修改app信息)
      - [2.6.1 请求方式](#261-请求方式)
      - [2.6.2 参数](#262-参数)
      - [2.6.3 返回值](#263-返回值)
  - [3.0 OAuth前端用API](#30-oauth前端用api)
    - [3.1 获取Auth_Code](#31-获取auth_code)
      - [3.1.1 请求方式](#311-请求方式)
      - [3.1.2 参数](#312-参数)
      - [3.1.3 返回值](#313-返回值)
  - [4.0 OAuth APP用API](#40-oauth-app用api)
    - [4.1 获取访问令牌APPToken / access_token](#41-获取访问令牌apptoken--access_token)
      - [4.1.1 请求方式](#411-请求方式)
      - [4.1.2 参数](#412-参数)
      - [4.1.3 返回值](#413-返回值)
    - [4.2 验证访问令牌](#42-验证访问令牌)
      - [4.2.1 请求方式](#421-请求方式)
      - [4.2.2 参数](#422-参数)
      - [4.2.3 返回值](#423-返回值)
    - [4.3 刷新访问令牌](#43-刷新访问令牌)
      - [4.3.1 请求方式](#431-请求方式)
      - [4.3.2 参数](#432-参数)
      - [4.3.3 返回值](#433-返回值)
    - [4.4 获取用户基础信息](#44-获取用户基础信息)
      - [4.4.1 请求方式](#441-请求方式)
      - [4.4.2 参数](#442-参数)
      - [4.4.3 返回值](#443-返回值)
    - [4.5 发送提醒/营销信息](#45-发送提醒营销信息)
      - [4.5.1 请求方式](#451-请求方式)
      - [4.5.2 参数](#452-参数)
      - [4.5.3 返回值](#453-返回值)
  - [5.0 工单系统API](#50-工单系统api)
    - [5.1 新建工单](#51-新建工单)
      - [5.1.1 请求方式](#511-请求方式)
      - [5.1.2 参数](#512-参数)
      - [5.1.3 返回值](#513-返回值)
    - [5.2 用户列出工单](#52-用户列出工单)
      - [5.2.1 请求方式](#521-请求方式)
      - [5.2.2 参数](#522-参数)
      - [5.2.3 返回值](#523-返回值)
    - [5.3 回复工单](#53-回复工单)
      - [5.3.1 请求方式](#531-请求方式)
      - [5.3.2 参数](#532-参数)
        - [5.3.2.1 用户请求时参数](#5321-用户请求时参数)
        - [5.3.2.2 APP请求时参数](#5322-app请求时参数)
      - [5.3.3 返回值](#533-返回值)
    - [5.4 查询工单信息](#54-查询工单信息)
      - [5.4.1 请求方式](#541-请求方式)
      - [5.4.2 参数](#542-参数)
        - [5.4.2.1 用户请求时参数](#5421-用户请求时参数)
        - [5.4.2.2 APP请求时参数](#5422-app请求时参数)
      - [5.4.3 返回值](#543-返回值)
    - [5.5 APP查询拥有的工单数量](#55-app查询拥有的工单数量)
      - [5.5.1 请求方式](#551-请求方式)
      - [5.5.2 参数](#552-参数)
      - [5.5.3 返回值](#553-返回值)
    - [5.6 APP列出已有工单](#56-app列出已有工单)
      - [5.6.1 请求方式](#561-请求方式)
      - [5.6.2 参数](#562-参数)
      - [5.6.3 返回值](#563-返回值)
    - [5.7 更改已有工单状态](#57-更改已有工单状态)
      - [5.7.1 请求方式](#571-请求方式)
      - [5.7.2 参数](#572-参数)
        - [5.7.2.1 用户请求时参数](#5721-用户请求时参数)
        - [5.7.2.2 APP请求时参数](#5722-app请求时参数)
      - [5.7.3 返回值](#573-返回值)

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
|CREDENTIAL_NOT_MATCH|用户凭据不正确(密码错误, token错误等)|14|credential|
|REQUEST_PARAM_FORMAT_ERROR|此请求参数格式错误|20|errorParam|

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
|DELETE|Request Body|同GET|如果成功删除资源, 返回值会为空, 请用HTTP Code来判断成功|

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
    "accountFrozen": false,
    "settings": {
      "allowEmailNotifications": 2,
      "allowSaleEmail": 2,
      "allowSMSNotifications": 2,
      "allowSaleEmail": 2,
      "allowCallNotifications": 2,
      "allowSaleCall": 2
    }
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
|settings|[UserSettingEntity](#012-usersettingentity定义)|-|用户设置, 上一级为系统默认设置|

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
            "accountFrozen": false,
            "settings": {
              "allowEmailNotifications": 2,
              "allowSaleEmail": 2,
              "allowSMSNotifications": 2,
              "allowSaleEmail": 2,
              "allowCallNotifications": 2,
              "allowSaleCall": 2
            }
        }
    }
}
```

### 0.6 LoginFailedReason登陆失败原因定义
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
- [APPFormat / APP系统定义, client_id, client_secret定长40个字符, access_token, refresh_token, auth_code定长32个字符, code_challenge(s256)定长64字符](https://github.com/InteractivePlus/PDK2021-CoreLib/blob/main/src/APP/Formats/APPFormat.php)
- [MaskIDFormat / MaskID定义, mask_id定长32个字符, display_name定长<=20个字符](https://github.com/InteractivePlus/PDK2021-CoreLib/blob/main/src/APP/Formats/APPFormat.php)
- [APPSystemFormatSetting / APP系统可变定义](https://github.com/InteractivePlus/PDK2021-CoreLib/blob/main/src/APP/APPSystemFormatSetting.php)
- [APPSystemFormatSetting / APP系统可变定义服务端实现,见`APP_SYSTEM_FORMAT_CONSTRAINTS`](https://github.com/InteractivePlus/PDK2021-Wrapper/blob/main/src/Config_template.php)
- [OAuthTicketFormatSetting / 工单系统可变定义](https://github.com/InteractivePlus/PDK2021-CoreLib/blob/main/src/EXT_Ticket/OAuthTicketFormatSetting.php)
- [OAuthTicketFormatSetting / 工单系统可变定义服务端实现, 见`OAUTH_TICKET_SYSTEM_FORMAT_CONSTRAINTS`](https://github.com/InteractivePlus/PDK2021-Wrapper/blob/main/src/Config_template.php)

### 0.8 验证码系统

验证码系统后端设计时已尽量减少耦合, 下面是验证码系统的交互逻辑

1. 前端从验证码API申请一个验证码,获取`captcha_id`, `captcha_data`和`expire_time`, 其中`captcha_id`是一个定长为32个字符的随机字符串, `captcha_data`是和验证码系统后端实现有关的提供给前端的验证码数据(图片, 或极验id等等), `expire_time`是验证码过期时间, 代表用户需要提交表单的时间(UTC)
2. 前端在用户填写完验证码后调用验证码验证API, 此API用来检查用户输入的验证码是否正确, 如果正确, 则API会将验证码标记为已验证
3. 前端在用户填写完表单后调用特定表单API, 附上验证码的captcha_id, 后端验证验证码是否已经过期以及验证码是否已被标记为已验证

不同的验证码系统拥有不同的API, 如果您想使用内置的SimpleCaptcha, 您可以[参阅文档](SimpleCaptchaAPI.md)

### 0.9 APP类型定义
见[PDK-2021CoreLib中PDKAPPType.php](https://github.com/InteractivePlus/PDK2021-CoreLib/blob/main/src/APP/APPInfo/PDKAPPType.php)

|APP_TYPE|APP类型|id|
|-|-|-|
|HAS_BACKEND|有后端(申请OAuth Access_Token时需要提供APPSecret, 无需PKCE)|1|
|NO_BACKEND|无后端(申请OAuth Access_Token时不用提供APPSecret, 需要PKCE)|2|
|EITHER|两者混合(可以选择有后端或无后端模式进行交互)|3|

### 0.10 APPEntity定义
APPEntity经常在API中作为一个数据类型被返回, 实际APPEntity也是一个JSON Object, 具体格式如下:

```json
{
    "appuid": 0,
    "display_name": "APP Display Name",
    "client_id": "APP Client ID",
    "client_secret": "APP Client Secret",
    "client_type": 1,
    "redirectURI": "https://localhost/",
    "create_time": 0,
    "owner_uid": 0
}
```

看完例子来看一下APPEntity的数据定义吧

|键值|类型|可选|注释|
|-|-|-|-|
|appuid|int|-|APP的uid|
|display_name|string|-|APP展示名称|
|client_id|string|-|APP OAuth client_id|
|client_secret|string|-|APP OAuth client_secret|
|client_type|int|-|APP类型,见[0.9 APP类型定义](#09-app类型定义)|
|redirectURI|string|-|OAuth授权成功回调地址|
|create_time|int|-|创建时间|
|owner_uid|int|-|APP拥有者用户uid|
|permission|[`APPPermissionEntity`](#020-apppermissionentity数据类型定义)|-|APP权限|

---
**还是不懂?**   
如果一个API返回了APPEntity, 如[创建APP](#21-注册app), 则API返回值会如下所示(以登录功能为例)

```json
{
    "errorCode": 0,
    "data": {
        "app": {
            "appuid": 0,
            "display_name": "Readin",
            "client_id": "WJIISMJWIJIJDSIWJIDJIWJI(40 Chars)",
            "client_secret": "JWIMZNWBDJWHSMDBWJSMWJDGZTYWUDMDGWBS(40 Chars)",
            "client_type": 1,
            "redirectURI": "https://localhost/",
            "create_time": 1159000,
            "owner_uid": 2
        }
    }
}
```

### 0.11 MaskID定义
MaskID是用户在OAuth授权第三方APP时创建的面具, 可以视为一个用户拥有的多个第三方APP账户. 在API返回MaskID实例数据时将以JSON格式返回, 具体格式如下:

```json
{
    "mask_id": "xxxx",
    "client_id": "xxxxxxxxxxxx",
    "uid": 32,
    "display_name": "形影",
    "createTime": 128930189023,
    "settings": {
      "allowEmailNotifications": 2,
      "allowSaleEmail": 2,
      "allowSMSNotifications": 2,
      "allowSaleEmail": 2,
      "allowCallNotifications": 2,
      "allowSaleCall": 2
    }
}
```

看完例子来看一下MaskID的数据定义吧

|键值|类型|可选|注释|
|-|-|-|-|
|mask_id|string|-|唯一的mask_id, 用于区分不同的面具|
|client_id|string|-|APP OAuth client_id|
|uid|int|-|用户uid|
|display_name|string|-|面具提供给APP的用户昵称, 非唯一|
|create_time|int|-|创建时间(EPOCH时间戳)|
|settings|[UserSettingEntity](#012-usersettingentity定义)|-|面具设置(上一级为用户设置)|

### 0.12 UserSettingEntity定义
UserSettingEntity是用户设置数据的抽象化实例. API通常在返回UserEntity和MaskIDEntity时返回UserSettingEntity, 在API返回UserSettingEntity实例数据时将以JSON格式返回, 具体格式如下:   

**[SettingBoolean.php](https://github.com/InteractivePlus/PDK2021-CoreLib/blob/main/src/User/Setting/SettingBoolean.php)** 我们首先定义, 在本JSON中所有键值皆为int, 且范围限定`SettingBoolean`如下:   

|名称|整数值|含义|
|-|-|-|
|SET_YES|1|布尔值 True|
|SET_NO|0|布尔值 False|
|SET_INHERIT|2|继承上层/默认|

```json
{
    "allowEmailNotifications": 2,
    "allowSaleEmail": 2,
    "allowSMSNotifications": 2,
    "allowSaleEmail": 2,
    "allowCallNotifications": 2,
    "allowSaleCall": 2
}
```

看完例子来看一下UserSettingEntity的数据定义吧

|键值|类型|可选|注释|
|-|-|-|-|
|allowEmailNotifications|`SettingBoolean`|-|是否允许发送邮件通知|
|allowSaleEmail|`SettingBoolean`|-|是否允许发送营销邮件|
|allowSMSNotifications|`SettingBoolean`|-|是否允许发送短信通知|
|allowSaleSMS|`SettingBoolean`|-|是否允许发送营销短信|
|allowCallNotifications|`SettingBoolean`|-|是否允许电话语音通知|
|allowSaleCall|`SettingBoolean`|-|是否允许营销电话|

### 0.13 OAuthScope定义
OAuthScope是第三方APP在申请用户授权时指定的授权范围(也是用户选择授权时可以指定的授权范围). 具体格式如下:   

**[OAuthScope.php](https://github.com/InteractivePlus/PDK2021-Wrapper/blob/main/src/OAuth/OAuthScopes.php)**


|Scope|解释|授权范围|
|-|-|-|
|info|User Info|获取用户面具昵称, 和用户面具设置|
|notifications|Send Notifications|给用户通过API发送提醒消息(可触达邮箱,SMS,手机电话)|
|contact_sales|Send Sale Messages|给用户通过API发送营销信息(可触达邮箱, SMS, 手机电话)|

### 0.14 OAuthToken定义
OAuthScope是第三方APP在申请访问令牌时获取到的访问令牌, 具体格式如下:   

|键值|类型|可选|注释|
|-|-|-|-|
|access_token|string|-|访问令牌字符串|
|refresh_token|string|YES|刷新令牌, 用于在过期之前刷新访问令牌|
|client_id|string|-|访问令牌所属APP client_id|
|obtained_method|int|-|访问令牌获取方式, 0 = Server, 1 = PKCE|
|issued|int|-|令牌创建时间(UTC)|
|expires|int|-|令牌过期时间(UTC)|
|last_renewed|int|-|令牌最后更新时间(UTC)|
|refresh_expires|int|-|刷新令牌过期时间(UTC)|
|mask_id|string|-|令牌所属面具id|
|scope|array\[string\]|-|令牌授权范围|

### 0.15 OAuthUserInfo定义

OAuthUserInfo是在第三方请求用户信息时提供, 是一个[`MaskIDEntity`](#011-maskid定义)的缩减版:      


|键值|类型|可选|注释|
|-|-|-|-|
|mask_id|string|-|唯一的mask_id, 用于区分不同的面具|
|display_name|string|-|面具提供给APP的用户昵称, 非唯一|
|settings|[UserSettingEntity](#012-usersettingentity定义)|-|面具设置(上一级为用户设置)|

### 0.16 TicketResponse定义

TicketResponse是作为工单拓展系统中使用的一个工单上的一条回复:      


|键值|类型|可选|注释|
|-|-|-|-|
|is_creator_content|bool|-|此条回复是否是工单创建者的回复|
|responder_name|string|-|回复者姓名, 如果是工单创建者的话此条为空|
|responded|int|-|回复时间|
|last_edited|int|-|回复修改时间|
|content|string|-|回复内容|

### 0.17 TicketEntity定义

TicketEntity是作为工单拓展系统中的工单结构体:   

|键值|类型|可选|注释|
|-|-|-|-|
|title|string|-|工单标题|
|content_listing|array(`TicketResponse`)|-|一条一条的回复|
|ticket_id|string|-|工单ID|
|client_id|string|YES|APP对应的client_id, 如果提交对象为PDK, 则client_id为空, appuid为0|
|appuid|int|YES|只有当client_id为空时APPUID固定为0, 其余时间不提供appuid|
|uid|int|YES|只有当client_id为空时才有|
|mask_id|string|YES|当client_id为空则mask_id为空|
|access_token|string|YES|当client_id为空则access_token为空, 此项目是提交工单用的OAuth access_token, 回复工单用的token不会被记录|
|is_urgent|bool|-|工单是否紧急|
|created|int|-|工单创建时间|
|last_updated|int|-|工单最后修改/回复时间|
|is_resolved|bool|-|工单是否已经解决|
|is_closed|bool|-|工单是否已经关闭|

### 0.18 MultipleResult定义

MultipleResult&lt;`T`&gt;作为一个搜索结果被返回, 是一个模板数据格式:   

|键值|类型|可选|注释|
|-|-|-|-|
|offset|int|-|本数据数据从服务端的第几条数据开始(默认0)|
|count|int|-|本数据包含几条记录|
|total_count|int|-|服务端上有几条记录|
|result|array(`T`)|-|数据|

### 0.19 UserPermissionEntity定义(提案阶段)
UserPermissionEntity是用户权限数据的抽象化实例. UserPermission, 在API返回UserSettingEntity实例数据时将以JSON格式返回, 具体格式如下:   

UserPermission取值为`SettingBoolean`,在True/False基础上增加了INHERIT(继承),见[UserSettingEntity](#012-usersettingentity定义)中对`SettingBoolean`的定义   


```json
{
  "isSuperAdmin": SettingBoolean::SET_YES,
  "isNormalAdmin": SettingBoolean::SET_YES,
  "UserModPerm": {
    "AllGrant": SettingBoolean::SET_YES,
    "AddUser": SettingBoolean::SET_YES,
    "DelUser": SettingBoolean::SET_YES,
    "GetUserInfo": SettingBoolean::SET_YES,
    "ModifyUser":SettingBoolean::SET_YES
  },
  ...
}
```

isSuperAdmin代表该用户是否是超级管理员，若为超级管理员，授予该用户所有板块的权限，忽略下列所有板块参数
isNormalAdmin代表该用户是否是管理员，若为管理员，授予该用户特定板块权限的权限，若须指定该用户权限，只需填写指定权限json即可
AllGrant为所有权限列表中的固定变量，若该参数为true，则忽略下列参数，授予该用户在该板块中所有权限

普通管理员所拥有的权限如下
|键值|类型|默认值|注释|
|-|-|-|-|
|UserModPerm|UserModPermEntity|-|赋予所有用户管理板块的权限|
|TicketModPerm|TicketModPermEntity|-|赋予所有工单板块权限|
|APPModPerm|APPModPermEntity|-|赋予所有APP板块权限|


UserModPermEntity权限列表有如下参数

---

|键值|类型|可选|注释|
|-|-|-|-|
|AllGrant|SettingBoolean|-|AllGrant为所有权限列表中的固定变量，若该参数为true，则忽略下列参数，授予该用户在该板块中所有权限|
|AddUser|SettingBoolean|-|是否赋予该用户添加用户权限|
|DelUser|SettingBoolean|-|是否赋予该用户删除用户权限|
|GetUserInfo|SettingBoolean|-|是否赋予该用户查看所有用户权限|
|ModifyUser|SettingBoolean|-|是否赋予该用户修改普通用户权限|
|ModifyAdminUser|SettingBoolean|-|是否赋予该用户修改管理员用户权限|

---

TicketModPermEntity权限列表有如下参数

---

|键值|类型|可选|注释|
|-|-|-|-|
|AllGrant|SettingBoolean|-|AllGrant为所有权限列表中的固定变量，若该参数为true，则忽略下列参数，授予该用户在该板块中所有权限|
|ReplyTicket|SettingBoolean|-|是否赋予该用户回复工单权限|
|CloseNormalTicket|SettingBoolean|-|是否赋予该用户关闭普通用户工单权限|
|DelNormalTicket|SettingBoolean|-|是否赋予该用户删除普通用户工单权限|
|CloseAdminTicket|SettingBoolean|-|是否赋予该用户关闭管理员工单权限|
|ViewAdminTicket|SettingBoolean|-|是否赋予该用户查看管理员工单权限|

---


APPModPermEntity权限列表有如下参数

---

|键值|类型|可选|注释|
|-|-|-|-|
|AllGrant|SettingBoolean|-|AllGrant为所有权限列表中的固定变量，若该参数为true，则忽略下列参数，授予该用户在该板块中所有权限|
|AddAPP|SettingBoolean|-|是否赋予用户添加APP权限|
|maxAPPPerm|APPPermissionEntity|-|创建/修改的APP最大的Permission|
|ViewAPP|SettingBoolean|-|是否赋予用户查看APP权限|
|EditAPP|SettingBoolean|-|是否赋予用户修改APP权限|
|EditAdminAPP|SettingBoolean|-|是否赋予用户修改管理员APP权限|

### 0.20 APPPermissionEntity数据类型定义

TicketEntity是作为APP系统中返回的APP权限结构体:   

|键值|类型|可选|注释|
|-|-|-|-|
|maxRecursionLevel|int|-|存储数据的最大叠加层数(数组中套数组)|
|maxCompressedLen|int|-|储存数据的最大压缩后大小(bytes/每个用户), 默认256|
|maxUncompressedLen|int|-|存储数据的最大压缩前大小(bytes/每个用户), 默认512|
|maxDataRecordNum|int|-|储存数据的最大用户数,默认1000|
|scopes|PDKAuthScope\[\]|-|允许授权范围,默认\['info','store_data'\]|
|canReadUserRealData|boolean|-|可否读取用户真实数据(邮箱地址, 手机号等等), 一般形随意动APP设为true|
|isOfficial|boolean|-|是否为形随意动官方APP|

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
|captcha_id|string|-|验证码ID|YES|

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
|captcha_id|string|-|验证码ID|YES|

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
|preferred_send_method|`SENT_METHOD`|YES|偏好发送方式(`SMS_MESSAGE`/`PHONE_CALL`)|YES|
|captcha_id|string|-|验证码ID|YES|

#### 1.5.3 返回值
成功时`dataKey-data`定义: 

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|sent_method|`SENT_METHOD`|-|验证码发送方式|YES|

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
|captcha_id|string|-|验证码ID|YES|

注: `username`,`email`,`phone`选一样填就行了, 有且只有一项可以填(不然会按优先级`username`>`email`>`phone`来选一项查找账号)

#### 1.6.3 返回值

##### 1.6.3.1 失败时定义

`dataKey-data`定义: 

|键值|类型|可选|注释|
|-|-|-|-|
|errorReason|`LoginFailedReason`|-|登录错误原因|


`rootKey-data`定义: 无特殊键值

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
|access_token|string|-|登录凭据, 填入URL|YES|

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
|preferred_send_method|`SENT_METHOD`|YES|偏好发送方式(`EMAIL`/`SMS_MESSAGE`/`PHONE_CALL`)|YES|

#### 1.10.3 返回值

注: 如果用户没有绑定邮箱, 则会返回错误代码`PERMISSION_DENIED`   

成功时`dataKey-data`定义: 

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|sent_method|`SENT_METHOD`|-|验证码发送方式|YES|

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
|preferred_send_method|`SENT_METHOD`|YES|偏好发送方式(`EMAIL`/`SMS_MESSAGE`/`PHONE_CALL`)|YES|

#### 1.11.3 返回值

注: 如果用户没有绑定手机, 则会返回错误代码`PERMISSION_DENIED`   

成功时`dataKey-data`定义: 

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|sent_method|`SENT_METHOD`|-|验证码发送方式|YES|

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
|preferred_send_method|`SENT_METHOD`|-|验证码发送偏好`EMAIL`/`SMS_MESSAGE`/`PHONE_CALL`|YES|

##### 1.14.2.2 重设密码参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|email|string|YES|申请密码重设的邮箱|YES|
|phone|string|YES|申请密码重设的手机, E164格式|YES|
|username|string|YES|申请密码重设的用户名|YES|
|preferred_send_method|`SENT_METHOD`|-|验证码发送偏好`EMAIL`/`SMS_MESSAGE`/`PHONE_CALL`|YES|
|captcha_id|string|-|验证码ID|YES|

注: `email`, `phone`, `username`其中必填且只能填一个.

#### 1.14.3 返回值

注: 如果用户没有验证账户或账户被冻结, 会返回`PERMISSION_DENIED`错误, 且`rootKey-data`会包含`errorReason`, 其值为[登录失败原因](#06-loginfailedreason登陆失败原因)之一.   

成功时`dataKey-data`定义: 

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|sent_method|`SENT_METHOD`|-|验证码发送方式|YES|

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

### 1.16 更改用户信息
这个API用来让用户更改昵称/签名

---

#### 1.16.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|PATCH|/user/userInfo|200 OK|

#### 1.16.2 参数

##### 1.16.2.1 更改密码参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid|YES|
|access_token|string|-|登录凭据|YES|
|nickname|?string|YES|新昵称|YES|
|signature|?string|YES|新签名|YES|
|settings|`UserSettingEntity`|YES|新设置(部分)|YES|

注: `nickname`,`signature`,和`settings`中必填一项, 可同时填写

#### 1.16.3 返回值

成功时`dataKey-data`定义: 

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|user|`UserEntity`|-|用户信息|YES|

成功时`rootKey-data`定义: 无特殊键值

### 1.17 列出已有面具

这个API用来让已登录形随意动用户, 列出他们所拥有的指定(或所有)APP的面具.

---

#### 1.17.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|GET|/masks/{client_id}|200 OK|
|GET|/masks|200 OK|

#### 1.17.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid,填入GET参数|-|
|access_token|string|-|用户登录凭据, 填入GET参数|YES|
|client_id|string|YES|指定APP的client_id, 如果不指定则列出所有面具|YES|


#### 1.17.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|masks|Array([`MaskIDEntity`](#011-maskid定义))|-|搜索到的所有面具信息的数组|

成功时`rootKey-data`定义: 无特殊键值


### 1.18 添加面具

这个API用来让已登录形随意动用户, 对一个APPID添加面具.

---

#### 1.18.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|POST|/masks/{client_id}|201 CREATED|

#### 1.18.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid,填入GET参数|-|
|access_token|string|-|用户登录凭据, 填入GET参数|YES|
|client_id|string|-|指定APP的client_id|YES|
|display_name|string|-|新的面具展示名称|YES|
|settings|`UserSettingEntity`(partial)|-|新的设置(可以只设置部分键值, 其他会默认继承用户设置)|YES|


#### 1.18.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|mask|[`MaskIDEntity`](#011-maskid定义)|-|新建的面具的信息|

### 1.19 修改面具信息

这个API用来让已登录形随意动用户, 对一个面具进行修改.

---

#### 1.19.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|PATCH|/masks/{mask_id}|200 OK|

#### 1.19.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid,填入GET参数|-|
|access_token|string|-|用户登录凭据, 填入GET参数|YES|
|client_id|string|-|指定APP的client_id|YES|
|display_name|string|YES|新的面具展示名称|YES|
|settings|`UserSettingEntity`(partial)|YES|新的设置(可以只设置部分键值, 其他会默认继承原本设置)|YES|

注: 当`display_name`项为空(指在JSON数据中无此键值), 或`display_name`项键值为null, 则不更改原本的`display_name`, 但如果`display_name`为''或不为空, 则覆盖原本的展示名称

#### 1.19.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|mask|[`MaskIDEntity`](#011-maskid定义)|-|修改后的面具的信息|

成功时`rootKey-data`定义: 无特殊键值

### 1.20 删除面具

此API用于让已登录用户删除自己持有的面具.

---

#### 1.20.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|DELETE|/masks/{mask_id}|204 NO CONTENT|

#### 1.20.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|mask_id|string|-|需要删除的面具ID, 填入URL|YES|
|uid|int|-|用户uid|YES|
|access_token|string|-|登录凭据|YES|

注: DELETE方法的参数用JSON封装在请求体Request Body内

#### 1.20.3 返回值

**只有失败时才有返回值**, 如果成功返回值一定是空的

## 2.0 第三方OAuth APP系统

### 2.1 注册APP

这个API用来让已登录形随意动用户注册APP

---

#### 2.1.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|POST|/apps/{display_name}|201 CREATED|

#### 2.1.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid|-|
|access_token|string|-|用户登录凭据|YES|
|display_name|string|-|APP展示名称, 填入URL|YES|
|client_type|int|-|APP类型, 见[0.9 APP类型定义](#09-app类型定义)|YES|

#### 2.1.3 返回值
成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|app|[APPEntity](#010-appentity定义)|-|所有关于新建APP的信息|

成功时`rootKey-data`定义: 无特殊键值

### 2.2 列出已有APP

这个API用来让已登录形随意动用户列出自己已有的APP

---

#### 2.2.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|GET|/user/{uid}/apps|200 OK|

#### 2.2.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid, 填入URL|-|
|access_token|string|-|用户登录凭据|YES|

#### 2.2.3 返回值
成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|apps|Array([APPEntity](#010-appentity定义))|-|所有APP的信息的列表|

正常返回例子:

```json
{
    "errorCode": 0,
    "data": {
        "apps": [
            {
                "appuid": 1,
                "display_name": "测试程序1",
                "client_id": "b41169f3c1c058863a1f3223ebbc898423f5b827",
                "client_secret": "a03c3e054bd79ad1a2a58d7421f0fbaa953e5c7d",
                "client_type": 3,
                "redirectURI": "",
                "create_time": 1613896746,
                "owner_uid": 23
            },
            {
                "appuid": 2,
                "display_name": "测试程序2",
                "client_id": "b41169f3c1c058863a1f3223ebbc898423f5b827",
                "client_secret": "a03c3e054bd79ad1a2a58d7421f0fbaa953e5c7d",
                "client_type": 3,
                "redirectURI": "",
                "create_time": 1613896746,
                "owner_uid": 23
            }
        ]
    }
}
```

成功时`rootKey-data`定义: 无特殊键值

### 2.3 请求删除APP验证码

这个API用来让已登录形随意动用户请求一个可以删除自己已有APP的验证码

---

#### 2.3.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|POST|/vericodes/deleteAPPRequest|201 CREATED|

#### 2.3.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid|-|
|access_token|string|-|用户登录凭据|YES|
|preferred_send_method|`SEND_METHOD`|YES|偏好发送方式|YES|

#### 2.3.3 返回值
成功时`dataKey-data`定义: 无特殊键值

成功时`rootKey-data`定义: 无特殊键值

### 2.4 删除已有APP

这个API用来让已登录形随意动用户, 且已经发送验证码, 删除自己已有的APP

---

#### 2.4.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|DELETE|/apps/{appuid}|204 NO CONTENT|

#### 2.4.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid|-|
|access_token|string|-|用户登录凭据|YES|
|appuid|int|-|APPUID,填入URL|-|
|veriCode|string|-|验证码|YES|

#### 2.4.3 返回值

成功时返回空数据, 请注意检查HTTP返回码.

### 2.5 请求APP重要操作验证码

这个API用来让已登录形随意动用户请求一个可以进行APP重要操作的验证码(修改信息)

---

#### 2.5.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|POST|/vericodes/appImportantInformationRequest|201 CREATED|

#### 2.5.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid|-|
|access_token|string|-|用户登录凭据|YES|
|preferred_send_method|`SEND_METHOD`|YES|偏好发送方式|YES|

#### 2.5.3 返回值
成功时`dataKey-data`定义: 无特殊键值

成功时`rootKey-data`定义: 无特殊键值

### 2.6 修改APP信息

这个API用来让已登录形随意动用户, 且已经发送重要操作验证码, 修改自己已有的APP信息

---

#### 2.6.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|PATCH|/apps/{appuid}|200 OK|

#### 2.6.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid,填入GET参数|-|
|access_token|string|-|用户登录凭据, 填入GET参数|YES|
|appuid|int|-|APPUID,填入URL|-|
|veriCode|string|-|验证码,填入GET参数|YES|
|display_name|string|YES|新APP展示名|YES|
|client_secret|string|YES|是否要进行client_secret重置, 重置则此键值需为"reroll"|-|
|client_type|int|YES|APP类型|YES|
|redirectURI|?string|YES|回调地址, 如果没有此键则表示不更改, 如果此键为null表示清空redirectURI, 如果不为空则设为此键的值|-|


#### 2.6.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|app|[APPEntity](#010-appentity定义)|-|APP的信息|

正常返回例子:

```json
{
  "errorCode": 0,
  "data": {
    "app": {
      "appuid": 1,
      "display_name": "测试程序1",
      "client_id": "b41169f3c1c058863a1f3223ebbc898423f5b827",
      "client_secret": "a03c3e054bd79ad1a2a58d7421f0fbaa953e5c7d",
      "client_type": 3,
      "redirectURI": "",
      "create_time": 1613896746,
      "owner_uid": 23
    }
  }
}
```

成功时`rootKey-data`定义: 无特殊键值

## 3.0 OAuth前端用API
### 3.1 获取Auth_Code

此API用于在APP申请Auth Code, 网页跳转到PDK用户系统前端, 用户选择授权的范围并点击授权后, PDK用户系统前端沟通后端发放AuthCode. 所有的重定向都在前端完成.

---

#### 3.1.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|GET|/authcode|200 OK|

#### 3.1.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|-|用户uid|-|
|access_token|string|-|用户登录凭据|YES|
|mask_id|string|-|用户想要使用的面具id|YES|
|client_id|string|-|当前授权的应用client_id|YES|
|code_challenge|string|YES|当code_challenge_type不为NONE的时候可以填入|YES|
|code_challenge_type|string|-|NONE \| SHA256 \| S256 \| PLAIN|YES|
|scope|`OAuthScope`|-|必须有info|YES|
|redirect_uri|string|-|回调地址, 需要和APP设置中符合. 回调时会在redirect_uri后填入`code=xxx&state=xxx`参数|-|
|state|string|YES|CSRF保护参数, 回调时会原封不动返回|-|

注: 
后端会直接拼接参数列表到回调地址, 如果`redirect_uri`为`http://http://localhost:8080/?`, 则后端返回的`redirect`参数为`http://localhost:8080/?code=xxx&state=xxx`

#### 3.1.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|redirect|string|-|回调地址, 前端可以直接将网页跳转到这个地址|
|expires|int|-|UTC UNIX Timestamp过期时间, 其实没什么用|

成功时`rootKey-data`定义: 无特殊键值

## 4.0 OAuth APP用API
### 4.1 获取访问令牌APPToken / access_token

此API用于在APP申请Auth Code后, 与后端申请获得access_token用

---

#### 4.1.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|POST|/oauth_token|201 CREATED|

#### 4.1.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|code|string|-|APP获取到的Authorization Code|YES|
|client_id|string|-|APP的client_id|YES|
|client_secret|string|YES|APP的client_secret,如果使用PKCE授权, 则此项会被忽略, 可不填写|YES|
|code_verifier|string|YES|只有PKCE时需要填写|-|

#### 4.1.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|token|`OAuthToken`|-|分配到的访问令牌|

成功时`rootKey-data`定义: 无特殊键值

### 4.2 验证访问令牌

此API用于在APP申请Access Token后, 与后端沟通验证access_token可用性

---

#### 4.2.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|GET|/oauth_token/verified_status|200 OK|

#### 4.2.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|access_token|string|-|访问令牌|YES|
|client_id|string|-|APP的client_id|YES|
|client_secret|string|YES|APP的client_secret, 仅当令牌使用SERVER方式授权获得的情况下需要提供|YES|
|mask_id|string|YES|用户面具的mask_id|YES|

#### 4.2.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|token|`OAuthToken`|-|当前访问令牌|

成功时`rootKey-data`定义: 无特殊键值

### 4.3 刷新访问令牌

此API用于在APP的Access Token即将过期或已经过期(但刷新令牌没有过期), 与后端沟通刷新access_token

---

#### 4.3.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|GET|/oauth_token/refresh_result|200 OK|

#### 4.3.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|refresh_token|string|-|刷新令牌|YES|
|client_id|string|-|APP的client_id|YES|
|client_secret|string|YES|APP的client_secret, 仅当access_token以SERVER grant形式获取时需要|YES|

#### 4.3.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|token|`OAuthToken`|-|新的访问令牌|

成功时`rootKey-data`定义: 无特殊键值

### 4.4 获取用户基础信息

此API用于在APP拥有Access Token时与后端交互获取用户信息

---

#### 4.4.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|GET|/oauth_ability/user_info|200 OK|

#### 4.4.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|access_token|string|-|APP的OAuth访问令牌|YES|

#### 4.4.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|info|`OAuthUserInfo`|-|用户信息|

成功时`rootKey-data`定义: 无特殊键值

### 4.5 发送提醒/营销信息

此API用于在APP拥有Access Token时与后端交互向用户推送信息

---

#### 4.5.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|POST|/oauth_ability/notifications|201 CREATED|

#### 4.5.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|access_token|string|-|APP的OAuth访问令牌|YES|
|title|string|-|发送消息标题, 有字数限制|YES|
|content|string|-|发送消息内容, 有字数限制|YES|
|is_sales|bool|YES|是否是营销信息(true),不填或false则发送提醒消息|-|
|preferred_send_methods|`SENT_METHOD`|YES|`EMAIL` \| `SMS_MESSAGE` \| `PHONE_CALL`|YES|

#### 4.5.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|sent_method|`SENT_METHOD`|-|发送方式|

成功时`rootKey-data`定义: 无特殊键值

## 5.0 工单系统API

### 5.1 新建工单

此API让用户/OAuth用户对特定APP(包括PDK)提交工单

---

#### 5.1.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|POST|/tickets|201 CREATED|

#### 5.1.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|title|string|-|工单标题|YES|
|content|string|-|工单第一条回复内容|YES|
|uid|int|YES|用户UID, 对PDK提交工单时提供|-|
|access_token|string|-|前端/OAuth 登录凭证, 当给PDK提交工单时请使用前端登陆凭证|-|
|is_frontend_token|boolean|-|登陆凭证是否是前端的?|-|
|captcha_id|string|-|验证码ID|YES|


#### 5.1.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|ticket|`TicketEntity`|-|新工单|

成功时`rootKey-data`定义: 无特殊键值


### 5.2 用户列出工单

此API让用户/OAuth用户列出自己所拥有的工单

---

#### 5.2.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|GET|/tickets|200 OK|

#### 5.2.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|uid|int|YES|用户uid, 使用前端token时使用|-|
|access_token|string|-|前端/OAuth 登录凭据|-|
|is_frontend_token|boolean|-|是否是前端token, 由于GET参数接受不到boolean值, 如果为OAuth Token可以考虑不带本参数|-|
|mask_id|string|YES|使用前端token时的可选参数, 可指定列出特定面具ID的工单|-|
|client_id|string|YES|使用前端token时的可选参数, 可指定列出特定APP的工单|-|


#### 5.2.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|tickets|array(`TicketEntity`)|-|列出的工单|

成功时`rootKey-data`定义: 无特殊键值

### 5.3 回复工单

此API让用户/OAuth用户/APP回复自己所拥有的工单

---

#### 5.3.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|POST|/tickets/{ticket_id}/responses|201 CREATED|

#### 5.3.2 参数

##### 5.3.2.1 用户请求时参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|ticket_id|string|-|填入URL|-|
|is_frontend_token|bool|-|是否是前端Token|-|
|uid|int|YES|只有是前端Token时才需要提供|-|
|access_token|string|-|前端/OAuth Token|YES|
|content|string|-|回复内容|YES|

##### 5.3.2.2 APP请求时参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|ticket_id|string|-|填入URL|-|
|client_id|string|-|APP的client_id|YES|
|client_secret|string|-|APP的client_secret|YES|
|responder_name|string|YES|回复者名字|YES|
|content|string|-|回复内容|YES|


#### 5.3.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|ticket|`TicketEntity`|-|修改后的工单|

成功时`rootKey-data`定义: 无特殊键值

### 5.4 查询工单信息

此API让用户/OAuth用户/APP查询自己所拥有的工单信息

---

#### 5.4.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|GET|/tickets/{ticket_id}|200 OK|

#### 5.4.2 参数

##### 5.4.2.1 用户请求时参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|ticket_id|string|-|填入URL|-|
|is_frontend_token|bool|-|是否是前端Token|-|
|uid|int|YES|只有是前端Token时才需要提供|-|
|access_token|string|-|前端/OAuth Token|YES|

##### 5.4.2.2 APP请求时参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|ticket_id|string|-|填入URL|-|
|client_id|string|-|APP的client_id|YES|
|client_secret|string|-|APP的client_secret|YES|

#### 5.4.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|ticket|`TicketEntity`|-|查询到的工单|

成功时`rootKey-data`定义: 无特殊键值

### 5.5 APP查询拥有的工单数量

此API让APP查询自己所拥有的工单数量

---

#### 5.5.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|GET|/apps/{client_id}/tickets/count|200 OK|

#### 5.5.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|client_id|string|-|APP的client_id, 填入URL|YES|
|client_secret|string|-|APP的client_secret|YES|
|mask_id|string|YES|APP可以用此参数筛选指定的MaskID的工单|YES|
|title|string|YES|APP可以用此参数筛选包含指定文本为标题的工单|-|

#### 5.5.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|total_count|int|-|服务端共有几条记录|

成功时`rootKey-data`定义: 无特殊键值

### 5.6 APP列出已有工单

此API让APP查询自己所拥有的工单数据

---

#### 5.6.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|GET|/apps/{client_id}/tickets|200 OK|

#### 5.6.2 参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|client_id|string|-|APP的client_id, 填入URL|YES|
|client_secret|string|-|APP的client_secret|YES|
|mask_id|string|YES|APP可以用此参数筛选指定的MaskID的工单|YES|
|title|string|YES|APP可以用此参数筛选包含指定文本为标题的工单|-|
|offset|int|YES|数据从服务端上第几条数据开始, 默认为0|-|
|count|int|YES|数据需要包含几条(最多), 默认为-1, 指全部|-|

#### 5.6.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|result|`MultipleResult`&lt;`TicketEntity`&gt;|-|查询到的信息|

成功时`rootKey-data`定义: 无特殊键值

### 5.7 更改已有工单状态

此API让用户/OAuth用户/APP更改自己所拥有的工单的状态

---

#### 5.7.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|PATCH|/tickets/{ticket_id}|200 OK|

#### 5.7.2 参数

##### 5.7.2.1 用户请求时参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|ticket_id|string|-|填入URL|-|
|is_frontend_token|bool|-|是否是前端Token|-|
|uid|int|YES|只有是前端Token时才需要提供|-|
|access_token|string|-|前端/OAuth Token|YES|
|set_resolved|bool|YES|将工单设为已解决状态(true)/未解决状态(false)|-|
|set_closed|bool|YES|此值为true时, 将工单关闭, 其余值不会更改工单|-|

##### 5.7.2.2 APP请求时参数

|参数|类型|可选|注释|格式同步|
|-|-|-|-|-|
|ticket_id|string|-|填入URL|-|
|client_id|string|-|APP的client_id|YES|
|client_secret|string|-|APP的client_secret|YES|
|set_resolved|bool|YES|将工单设为已解决状态/未解决状态|-|
|set_closed|bool|YES|此值为true时, 将工单关闭, 其余值不会更改工单|-|

#### 5.7.3 返回值

成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|ticket|`TicketEntity`|-|修改后的工单|

成功时`rootKey-data`定义: 无特殊键值
