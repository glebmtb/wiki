
**Скачиваем и устанавливаем:**  

    _yum install squid_

**Редактируем файл конфига:**  

    _vi /etc/squid/squid.conf_  
добавляем:  

    _acl our\_networks src 192.168.1.0/24_  
    _http\_access allow our\_networks_  
сохраняем настройки:  
_chkconfig squid on_

**Запускаем и останавливаем:**  

    _/etc/init.d/squid start_  
    _/etc/init.d/squid stop_

[Дополнительные сведения](https://web.archive.org/web/20210119012348/http://www.cyberciti.biz/tips/howto-rhel-centos-fedora-squid-installation-configuration.html)

**Установка под Windows**

[Скачиваем дистрибутив](https://web.archive.org/web/20210119012348/http://squid.acmeconsulting.it/index.html) Squid для Windows  
Распаковываем на диск "C"

В папке c:\\squid\\etc\\ убираем у всех файлов дописку deffult  
_Добавляем_// squid.conf _добавляем:  
_acl our\_networks src 192.168.1.0/24http\_access allow our\_networks//

_создание сваб директория для кеша_  
_squid.exe -z_

**Squid как служба**  
Устанавливаем:  

    _squid -i -f c:/squid/etc/squid.conf -n Squid27_  
Старт squid-а:  

    _net start Squid27_  
Останов:  

    _net stop squid27_  
Переконфигурация:  

    _squid -n Squid27 -f c:/squid/etc/squid.conf -k reconfigure_

**Установка под Windows дополнительные ресурсы:**  
[1\. eng](https://web.archive.org/web/20210119012348/http://squid.acmeconsulting.it/Squid27.html), [2\. rus](https://web.archive.org/web/20210119012348/http://squid.opennet.ru/win/squidwin.shtml)

**WEB-интерфейс возможен через "SAMS - SQUID Account Management System"**
