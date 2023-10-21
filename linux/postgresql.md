
**[Установка на CentOS 6](https://web.archive.org/web/20210117103826/http://www.postgresql.org/download/linux/redhat/)**  

    rpm -i [http://yum.postgresql.org/9.1/redhat/rhel-6-x86\_64/pgdg-redhat91-9.1-5.noarch.rpm](https://web.archive.org/web/20210117103826/http://yum.postgresql.org/9.1/redhat/rhel-6-x86_64/pgdg-redhat91-9.1-5.noarch.rpm)  
    yum install postgresql91-server postgresql91-contrib  
    service postgresql-9.1 initdb  
    chkconfig postgresql-9.1 on

**Настройка**  
Добавляем строку listen\_addresses = '\*'  

    nano /var/lib/pgsql/9.1/data/postgresql.conf

Прописываем маршрутизацию: 

    iptables -A INPUT -p tcp -s 0/0 —sport 1024:65535 -d **IP\_адрес** —dport 5432 -m state —state NEW,ESTABLISHED -j ACCEPT  
    iptables -A OUTPUT -p tcp -s IP\_адрес —sport 5432 -d 0/0 —dport 1024:65535 -m state —state ESTABLISHED -j ACCEPT  
или вырубаем iptables если не надоservice iptables stop

Добавляем IP\_адрес для доступа к БД:  

    nano /var/lib/pgsql/9.1/data/pg\_hba.conf  
    host all all _IP\_адрес_/32 md5

Добавляем пользователя БД:  

    su postgres  
    psql  
    alter role postgres with password 'postgres'; (точка с запятой в конце обязательна!)  
    \\q  
    exit

**Управление**  

    service postgresql-9.1 start - запускservice  
    postgresql-9.1 stop - стоп  
    service postgresql-9.1 restart - перезагрузка

**Команды**  
Подсоединение к серверу 

    psql -h PostgreSQL-IP-ADDRESS -U USERNAME -d DATABASENAME  
    psql -h 192.168.1.5 -U vivek -d sales

**Размер всех таблиц**  
[https://www.opennet.ru/tips/917\_postgresql\_size\_database.shtml](https://web.archive.org/web/20210117103826/https://www.opennet.ru/tips/917_postgresql_size_database.shtml)  
[https://postgrespro.ru/docs/postgresql/9.6/functions-admin](https://web.archive.org/web/20210117103826/https://postgrespro.ru/docs/postgresql/9.6/functions-admin)

    SELECT
        schemaname||'.'||tablename AS full\_tname,
        pg\_size\_pretty(pg\_total\_relation\_size(schemaname||'.'||tablename)) AS total\_usage,
        pg\_size\_pretty((pg\_total\_relation\_size(schemaname||'.'||tablename) - pg\_relation\_size(schemaname||'.'||tablename))) AS external\_table\_usage
    FROM pg\_catalog.pg\_tables
    ORDER BY pg\_total\_relation\_size(schemaname||'.'||tablename) DESC;
