
**Установка**  
1) скачиваем исходники "Source tarball (tar.gz)" и распаковываем  
[Sphinx](https://web.archive.org/web/20210122160138/http://sphinxsearch.com/downloads/release/)

2) устанавливаем make  
_yum install make_  
3) устанавливаем gcc  
_yum install gcc_  
4) устанавливаем postgresql-dev  
_yum install postgresql-devel_  
5) устанавливаем g++  
_yum intsall gcc-c++.x86\_64_  
6) создаем папку  
_mkdir /opt/sphinx_  
7) конфигурируем под Postgrase  
_./configure —with-pgsql —without-mysql —prefix=/opt/sphinx —enable-id64_

Если так не работает, попробуйте:  
./configure —with-pgsql —without-mysql —prefix=/opt/sphinx —enable-id64 —with-pgsql-libs=/usr/pgsql-9.1/lib/ —with-pgsql-includes=/usr/pgsql-9.1/include/  
8) собираем  
_make_  
9) устанавливаем  
_make install_

**Настройка**  
конфиги sphinx/bin_/sphinx.conf_  
индексы sphinx/var/data

**Управление**  
_./searchd_ - запуск  
_./searchd —stop_ - остановка
