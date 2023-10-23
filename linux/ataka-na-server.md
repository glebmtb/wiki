
\[\] - не обязательный параметры  
{} - обязательные параметры  
| - или  
— DNS/WHOIS/NETWORK  
**Формирование запросов к DNS серверу**  
nslookup \[-q=ns|mx|axfr|txt|…\] {name} \[server\]  
host {name} \[server\]  
dig \[@server\] {name} {type}  
_name - доменное имя  
server - сервер с которого получать DNS  
mx - адрес SMPT сервера  
ns - авторитетные name сервера_

**зонтрансфер атака**  
получаем авторитетные днс сервера  
nslookup -q=ns zonetransfer.me  
и мы можем получить список потдоменов следующим образом  
dig zonetransfer.me @dnsserver axfr

**WHOIS** - сохранение регистрационной информации о сетевых объектах  
\- nslookup domain  
получаем ип адресс  
\- whois ip\_adress

**whois \[flag\] {keyword}**  
keyword - ip,доменное имя, nichandle  
flag - whois серивис

**Search engines**  
Поисковые сайты: Google, Yahoo, Yandex, Shodan  
Поисковые запросы используя спец слова  
inurl: admin (содержание в урле)  
site: target.com (конкретно какой сайт)  
filetype: txt (тип файла)  
cache: target.com (вернет закэшиворанную копию)  
в robots.txt могут оказаться ссылки на админку

**Сканирование портов**  
nmap -sS -T4 -n <target>  
\-sS - sean scan, отправляем пакет и смотрим на реакцию системы на этот пакет  
\-T4 - taiming template, больше число более агрессивно и быстрее, меньше число будем дольше ждать  
\-n - мы не хотим резолвить обратный ip адреса  
\-A - более углубленный анализ цели  
\-p <ports> - сканировать порты  
\-p 1-65535 - сканить все порты

nmap -sn 192.168.1.0/24 - скан сети

**Точки входа в веб приложение**  
\- GET/POST  
\- Cookies  
\- Headers  
\- Hosts  
\- Data sources

Интересные заголовки: [X-Forwarded-For](https://web.archive.org/web/20210116095847/https://en.wikipedia.org/wiki/X-Forwarded-For) (содержит реальный ип), X-Real-Ip.

**Инструменты - анализ запросов**  
OWASP-ZAP  
Burp Suite -> [https://portswigger.net/burp/](https://web.archive.org/web/20210116095847/https://portswigger.net/burp/)﻿  
Fiddler -> [http://www.telerik.com/fiddler](https://web.archive.org/web/20210116095847/http://www.telerik.com/fiddler)﻿

**Инструменты - создания запросов**  
telnet <target> 80  
nc <target> 80

    telnet ya.ru 80
    Trying 93.158.134.3...
    Connected to ya.ru.
    Escape character is '^]'.
    GET / HTTP/1.1
    Connection: keep-alive
    Cookie: param=value;
    Host: ya.ru

    wget -O - [--header "headername:value"] http://<target>
    curl [-H "headername:value"] http://<target>

  
**https**  
openssl s\_client -connect <target>:<port>

**base64**  
echo "AAA"| base64 //кодируем  
echo "somthing" | base64 -d //раскодирование

**Анализ**  
1) фиксируем 3 типа ответа:

http://target.ru/?id=...  

Значение id

Результат

есть данные

1

username:admin

нет данных

1000

username:

ошибка

aaa

DB Error

**LFI**  
можно вставить как параметр  
../../../../../../../etc/password%00

**Брутфорс**  
[john](/web/20210116095847/http://wiki.n5g.ru/john)

**Проверка окружения на доступность ресурсов**  
netstat -anp | grep ESTABLISHED - проверка отрытых соединений с локальными машинами  
samba: smbclient -L target - сканим  
rsync: rsync rsync:_target - сканим, rsync rsync:_target/file ./ - забираем  
NFS: showmount -e target - сканим, mount -o nolock -t nfs target:/path /locl - подключаем
