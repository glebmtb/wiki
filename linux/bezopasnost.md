
**Открытые соединения**\*  
netstat -at | grep ESTABLISHED

**Логи авторизации**  
sudo grep -o Failed -R /var/log/\* | grep -v grep | wc -l - количество плохих авторизаций  
sudo grep "Nov 16.\*Failed" /var/log/sec\* | grep -v grep | wc -l - количество плохих авторизаций за день  
sudo cat /var/log/secure | grep Failed | grep -v grep - найти все плохие авторизации  
sudo grep "Accept.\*from" /var/log/sec\* | grep -v 31.13.128.62 | grep -v grep - найти все хорошие авторизайии с других серваков

**Проверить IP адрес**  
ip-lookup.net

**Дать права на выполнении команды от руда без рута**

    #<name_file>
    %<user_name> ALL= NOPASSWD: <comand_name>

    sudo nano /etc/sudoers.d/<name_file>
    sudo chmod 0440 /etc/sudoers.d/<name_file>
    sudo visudo -c
