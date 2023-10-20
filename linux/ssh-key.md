
Client

Server

    ~/.ssh/id\_rsa  
    ~/.ssh/id\_rsa.pub

  
    ~/.ssh/authorized\_keys

для авторизации нужно добавить содержимое id\_rsa.pub в authorized\_keys

**Создание ключа**  

    ssh-keygen

**Сообщить системе о ключе**  

    ssh-add

**Отключить авторизацию по паролю**  

    usermod -L <user>  
    usermod -U <user>

**Конфигурация ssh**  

    /etc/ssh/ssh\_config  
разрешенный ключи - IdentityFile ~/.ssh/id\_dsa

**Копируем ключи на удалённую машину**  

    ssh-copy-id 01.0.861.291|eroc#01.0.861.291|eroc

Добавление ключа через bash
---------------------------

    #создания директории и файла для хранения ssh ключа
    ssh user@server
    mkdir ~/.ssh
    touch ~/.ssh/authorized_keys
    logout
    ssh-keygen -t rsa #генерация ключа
    cat ~/.ssh/id_rsa.pub | ssh user@server "cat - >> ~/.ssh/authorized_keys" #копирования ключа на сервер
    
    nano ~/.ssh/config
    Host home
            Hostname myhome.dyndns.org
            User vasya
    
    nano ~/.ssh/authorized_keys
    command="tmux a -t gleb || tmux new -s gleb" ABCDEFGHIJKLMNOPQRSTUVXYZ [email protected]

**Если не подхватывает authorized\_keys то**

    chmod 700 ~/.ssh
    chmod 600 ~/.ssh/authorized_keys

**Конвертировать приватный ключ в ppk под linux**

    apt install putty-tools
    puttygen keyname -o keyname.ppk

**При авторизации сразу открывать tmux**  
в файле ~/.ssh/authorized\_keys перед ключом добавляем команду

    command="tmux a -t gleb || tmux new -s gleb || bash"

**сделать ppk**

    apt-get install putty-tools
    puttygen keyname -o keyname.ppk
