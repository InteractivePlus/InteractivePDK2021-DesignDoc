# SimpleCaptchaAPI 定义

 [返回](README.md)   

 SimpleCaptcha是InteractivePDK中自带的一种验证码, 具体形式为图片验证码.

## 目录

- [SimpleCaptchaAPI 定义](#simplecaptchaapi-定义)
  - [目录](#目录)
  - [0.0 公共常数](#00-公共常数)
    - [0.1 验证码长度](#01-验证码长度)
    - [0.2 验证码长宽](#02-验证码长宽)
  - [1.0 API定义](#10-api定义)
    - [1.1 申请验证码](#11-申请验证码)
      - [1.1.1 请求方式](#111-请求方式)
      - [1.1.2 参数](#112-参数)
      - [1.1.3 返回值](#113-返回值)
    - [1.2 提交验证码](#12-提交验证码)
      - [1.2.1 请求方式](#121-请求方式)
      - [1.2.2 参数](#122-参数)
      - [1.2.3 返回值](#123-返回值)

## 0.0 公共常数

### 0.1 验证码长度

后端设置的默认验证码长度为5, 意味着每个验证码默认长度5个字符, 此设置在后端可调, 建议前端也将此设置编写为可调节的配置.

### 0.2 验证码长宽

验证码默认宽高为`150px`×`40px`, 在申请验证码时前端可以申请长宽不同的验证码

## 1.0 API定义

### 1.1 申请验证码

此API用来让前端表单申请验证码

---

#### 1.1.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|GET|/captcha|201 CREATED|

#### 1.1.2 参数

|键值|类型|可选|注释|
|-|-|-|-|
|width|int|YES|生成的验证码宽度(px), 默认150|
|height|int|YES|生成的验证码高度(px), 默认40|

#### 1.1.3 返回值
成功时`dataKey-data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|captcha_id|string|-|验证码ID|
|captcha_data|array|-|验证码详细信息|
|expire_time|int|-|验证码过期UTC时间|

成功时`captcha_data`定义:

|键值|类型|可选|注释|
|-|-|-|-|
|width|int|-|生成的验证码宽度(px)|
|height|int|-|生成的验证码高度(px)|
|jpegBase64|string|-|验证码图片jpeg数据,base64编码|
|phraseLen|int|-|验证码长度|

注: jpegBase64可以直接内置到&lt;image&gt;标签内, 用法:

```html
<image src="data:image/jpeg;base64, {{jpegBase64}}" />
```

将`{{jpegBase64}}`替换为实际数据即可.

调试接口时可以使用[Github上的这个Base64图片查看器](https://jaredwinick.github.io/base64-image-viewer/)

成功时`rootKey-data`定义: 无特殊键值

### 1.2 提交验证码

此API用来让前端表单申请验证码

---

#### 1.2.1 请求方式

|HTTP Method|URL|成功HTTP Code|
|-|-|-|
|GET|/captcha/{{captcha_id}}/submitResult|200 OK|

#### 1.2.2 参数

|参数|类型|可选|注释|
|-|-|-|-|
|captcha_id|string|-|填入URL|
|phrase|string|-|用户填写的验证码, 无需区分大小写|


#### 1.2.3 返回值

失败时(验证码错误)会返回 [`CREDENTIAL_NOT_MATCH`](API.md#02-错误代码errorcode)错误代码, 返回数据的`credential`键会是固定的`phrase`,代表验证码填写错误.

成功时`dataKey-data`定义: 无特殊键值

成功时`rootKey-data`定义: 无特殊键值