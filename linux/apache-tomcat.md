
**[Tomcat](https://web.archive.org/web/20210116095239/http://tomcat.apache.org/)** - являеться полнофункциональной реализацией стандартов JSP и сервлетов.

Установка
---------

### Из пакетов

    #Tomcat 7
    apt-get install tomcat7

### Копированием папки

Скачать [дистрибутив](https://web.archive.org/web/20210116095239/http://tomcat.apache.org/download-70.cgi). Извлекаем содержимое архива в каталог на жестком диске. По умолчанию имя каталога "Tomcat".  
Что бы Tomcat работал корректно, нужно определить переменную окружения _JAVA\_HOME_ - должна указывать на каталог, содержащий Java.

### Возможные ошибки

    # ошибка 1.
    no JDK found - please set JAVA_HOME
    
    # добавляем путь к jdk в настройках
    # редактируем конфиг
    vim /etc/default/tomcat7
    # добавляем строчку
    # JAVA_HOME=/usr/lib/jvm/java-7-oracle

Управление
----------

    service tomcat7 start #запустить
    service tomcat7 stop #остановить
    service tomcat7 restart #перезапуск

Каталоги
--------

    /var/lib/tomcat7/webapps #расположения Web-приложений (war файлов)

Развертывание Web-приложений
----------------------------

JSP-страницы, сервлеты и их вспомогательные файлы развертываются как часть Web-приложения. Web-приложения развертываются в подкаталоге _webapps_ каталога _Tomcat_. WAR-файлы помещенные в каталог _webapps_ в начале выполнения сервера Tomcat извлечет содержимое WAR-файла в соответствующую структуру подкаталогов _webapps_.

Поддержка UTF-8 URIEncoding в Tomcat
------------------------------------

[Рекомендации по использованию UTF-8](https://web.archive.org/web/20210116095239/http://wiki.apache.org/tomcat/FAQ/CharacterEncoding#Q3)  
Если ваше GET и POST параметры не кодируются в UTF-8 при использовании Tomcat, попробуйте настроить конфигурацию коннектора в Tomcats server.xml так:

   <Connector port\="8080" maxHttpHeaderSize\="8192"
               maxThreads\="150" minSpareThreads\="25" maxSpareThreads\="75"
               enableLookups\="false" redirectPort\="8443" acceptCount\="100"
               connectionTimeout\="20000" disableUploadTimeout\="true"
               URIEncoding\="UTF-8"
   />

Разные хитрости
---------------

Если вы хотите использовать в запросах %2f (escaping "/") то надо добавить параметры [JVM](https://web.archive.org/web/20210116095239/http://tomcat.apache.org/tomcat-5.5-doc/config/systemprops.html), по умолчанию будет 400 ошибка

    -Dorg.apache.tomcat.util.buf.UDecoder.ALLOW_ENCODED_SLASH=true

  
или добавить в конфигурацию запуска Tomcat строчку

    CATALINA_OPTS="-Dorg.apache.tomcat.util.buf.UDecoder.ALLOW_ENCODED_SLASH=true"
