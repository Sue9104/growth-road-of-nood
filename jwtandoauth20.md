# JWT vs OAuth2.0

> [https://www.cnblogs.com/adamans/articles/9149833.html](https://www.cnblogs.com/adamans/articles/9149833.html)

用户认证 Authentication

用户授权 Authorization

|  | 定义 | 应用场景 | 优点 | 缺点 |
| :--- | :--- | :--- | :--- | :--- |
| JWT（JSON Web Token） | 认证协议，用户提供用户名和密码给认证服务器，认证成功后返回Token | 无状态的分布式API | 快速开发，无需Cookie,不依赖社交网络 | Token有长度限制，不能撤销，需要失效时间限制 |
| OAuth2.0 | 授权框架，描述系统中用户、前端应用以及客户端之间如何实现相互认证 | 外包认证服务器 | 工作量少，方式灵活，可和JWT同时使用，可针对不同应用扩展 | 时间投入多，引入错误的风险更高 |

> More: [https://www.lijiaocn.com/%E6%8A%80%E5%B7%A7/2015/12/03/%E8%AE%A4%E8%AF%81%E4%B8%8E%E6%8E%88%E6%9D%83.html\#oauth](https://www.lijiaocn.com/%E6%8A%80%E5%B7%A7/2015/12/03/%E8%AE%A4%E8%AF%81%E4%B8%8E%E6%8E%88%E6%9D%83.html#oauth)

# LDAP

> [https://blog.fe.ioteams.com/post/basicldap.html](https://blog.fe.ioteams.com/post/basicldap.html)

Lightweight Directory Access Protocol, 轻量目录访问协议

* 基于TCP/IP，支持SSL/TLS加密
* 树状结构存储，读取速度快，写入速度慢
* 开放的协议，跨平台，维护简单
* 服务器存放数据，客户端操作数据

应用场景：单点登录、局域网资源统一管理（多应用系统间账户管理方案）

