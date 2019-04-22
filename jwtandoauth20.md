# JWT vs OAuth2.0

> [https://www.cnblogs.com/adamans/articles/9149833.html](https://www.cnblogs.com/adamans/articles/9149833.html)



|  | 定义 | 应用场景 | 优点 | 缺点 |
| :--- | :--- | :--- | :--- | :--- |
| JWT（JSON Web Token） | 认证协议，用户提供用户名和密码给认证服务器，认证成功后返回Token | 无状态的分布式API | 快速开发，无需Cookie,不依赖社交网络 | Token有长度限制，不能撤销，需要失效时间限制 |
| OAuth2.0 | 授权框架，描述系统中用户、前端应用以及客户端之间如何实现相互认证 | 外包认证服务器 | 工作量少，方式灵活，可和JWT同时使用，可针对不同应用扩展 | 时间投入多，引入错误的风险更高 |



