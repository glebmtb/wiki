
Установка JDK 7 на Ubuntu
-------------------------

    sudo add-apt-repository ppa:webupd8team/java
    sudo apt-get update
    sudo apt-get install oracle-java7-installer
    java -version
    
    sudo add-apt-repository ppa:webupd8team/java
    sudo apt-get update
    sudo apt-get install oracle-java8-installer

**JAVA\_HOME**

    sudo nano /etc/environment

  
Добавляем в файл: JAVA\_HOME="/usr/lib/jvm/open-jdk"

**Возможные ошибки**

#ошибка
add\-apt\-repository: command not found
 
#решение:
#for <= 12.04

    sudo apt\-get install python\-software\-properties
#for >= 12.10

    sudo apt\-get install software\-properties\-common

Установка JDK
-------------

Скачиваем [Java SDK jdk-\*u\*\*-linux-x\*\*.tar.gz](https://web.archive.org/web/20211129205725/http://www.oracle.com/technetwork/java/javase/downloads/index.html)  
Распаковываем в _/opt_/  
[Создаем](globalnye-peremennye-linux.md) глобальную переменную: _JAVA\_HOME=/opt/jdk\*_
