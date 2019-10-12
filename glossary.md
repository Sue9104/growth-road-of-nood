# Glossary

<!-- toc -->

## ORM

Object Relation Mapping, 对象关系映射，
是一种为了解决面向对象与关系数据库存在的互不匹配的现象的技术。

## CRUD

Create Read Update Delete 基本的数据库操作。

### HTTP method vs CRUD

|Method|CRUD|
|:--:|:--:|
|POST|Create|
|PUT|Update|
|PATCH|Partially Update|
|GET|Read|
|DELETE|Delete|



## WSGI vs uWSGI

> 参考: https://www.jianshu.com/p/679dee0a4193

- WSGI: Web Server Gateway Interface, 只是一种规范协议，
必须同时实现Web Server和Web Application。

- uWSGI：是一个web服务器，实现了WSGI协议、uwsgi协议、http协议等。

### django

- django Application: 可调用对象, 如函数、方法、类(包含call), 
接收两个参数environ(请求上下文)和start_response(响应状态和响应头)。

- django WSGI Server: 获取Http请求传递给Application,处理后返回response.
涉及多个类的实现及相互引用，如WSGIServer\WSGIRequestHandler\ServerHandler\WSGIHandler.





