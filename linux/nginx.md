
**[nginx](https://web.archive.org/web/20210117103540/http://nginx.org/ru/)**

Установка
---------

### из пакетов

    sudo apt-get install nginx

### собираем из исходников

[Офф. док](https://web.archive.org/web/20210117103540/http://sysoev.ru/nginx/getting_started.html)

    #1) ставим пакеты: pcre-devel
    #2) Скачиваем исходники (http://nginx.org/ru/download.html)
    #3) Подготавливаем конфигурацию установки (http://nginx.org/ru/docs/configure.html)
    #4) Конфигурируем
    ./configure
    #4) Собираем
    make
    #5) Устанавливаем
    make install

Управление
----------

    #старт
    ./nginx
    
    #стоп
    ./nginx -s stop
    
    #изменение конфигурации
    ./nginx -s reload
    service nginx reload

Пути nginx по умолчанию
-----------------------

nginx path prefix: "/usr/local/nginx"  
nginx binary file: "/usr/local/nginx/sbin/nginx"  
nginx configuration prefix: "/usr/local/nginx/conf"  
nginx configuration file: "/usr/local/nginx/conf/nginx.conf"  
nginx pid file: "/usr/local/nginx/logs/nginx.pid"  
nginx error log file: "/usr/local/nginx/logs/error.log"  
nginx http access log file: "/usr/local/nginx/logs/access.log"  
nginx http client request body temporary files: "client\_body\_temp"  
nginx http proxy temporary files: "proxy\_temp"  
nginx http fastcgi temporary files: "fastcgi\_temp"  
nginx http uwsgi temporary files: "uwsgi\_temp"  
nginx http scgi temporary files: "scgi\_temp"

Возможные проблемы
------------------

    #ошибка 1
    invalid URL prefix in
    
    #возможно не правильный формат "proxy_pass", он должен быть формата
    proxy_pass http://localhost:8000/uri/;

Конфигурация
------------

    #пример 1, tomcat c nginx
    server {
      listen 80;
      server_name chain.n5g.ru www.chain.n5g.ru;
      location / {
        proxy_pass http://37.139.7.221:8080/order-chainreactioncycles-0.1/;
        proxy_redirect off;
    
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      }
    }
