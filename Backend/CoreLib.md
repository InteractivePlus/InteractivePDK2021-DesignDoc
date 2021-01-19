# 核心库标准文档

 [返回](README.md)   
 本文档将标准化后端核心支持库的架构   

## 目录

- [核心库标准文档](#核心库标准文档)
  - [目录](#目录)
  - [1.0 功能分库](#10-功能分库)

## 1.0 功能分库

 在开发核心库时, 由于InteractivePDK项目庞大, 且功能繁多, 故会将每个功能分离做成分开的核心库. 具体分割方案见下表

 |核心库名|中文名称|负责功能|
 |-|-|-|
 |BaseLib|基础库|提供全局共用的类, 比如异常类|
 |CommunicationCoreLib|沟通核心库|负责发送验证码(SMS, Email)|
 |UserCoreLib|用户核心库|负责用户注册, 登录, 分配/验证Token, 验证权限, 修改/查看设置等|
 |APPCoreLib|APP核心库|负责第三方/第一方APP注册, 查看/修改管理列表, 设置回调链接, 查看/修改client_id和client_secret|
 |OAuthCoreLib|OAuth交互库|负责分发授权码, 访问凭证等|
 |EXT-OAuthStorageLib|拓展-OAuth储存库|负责给第一方/第三方APP提供云同步功能|