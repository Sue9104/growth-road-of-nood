# Django

## deploy

参考： https://uwsgi-docs-zh.readthedocs.io/zh_CN/latest/tutorials/Django_and_nginx.html

- uwsgi

```
uwsgi --http :8000 --module mysite.wsgi
```

- nginx

  - edit mysite_nginx.conf

```
upstream django {
    server 127.0.0.1:8001; # for a web port socket (we'll use this first)
}
server {
    listen      80;
    server_name .example.com; 
    charset     utf-8;
    client_max_body_size 75M;   # adjust to taste
    location /media  {
        alias /path/to/your/mysite/media;  
    }

    location /static {
        alias /path/to/your/mysite/static; 
    }
    location / {
        uwsgi_pass  django;
        include     /path/to/your/mysite/uwsgi_params; 
    }
}
```

  - collect statics and media
  
  ```
  python manage.py collectstatic
  ```
  
  - link to /etc/nginx
  
  ```
  sudo ln -s ~/path/to/your/mysite/mysite_nginx.conf /etc/nginx/sites-enabled/
  ```
  
  - start nginx
  
  ```
  sudo /etc/init.d/nginx restart
  ```
