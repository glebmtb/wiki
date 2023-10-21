
[OpenVPN сервера с помощью docker-compose](https://web.archive.org/web/20210117081918/https://habr.com/ru/post/354632/)

**Добавление клиента**

    docker-compose run --rm openvpn easyrsa build-client-full {client_name} nopass  
    docker-compose run --rm openvpn ovpn_getclient {client_name} > certificate.ovpn

**Настройка клиента MacOs**  
Использую openvpn, ставиться через brew.  
Если на маке не работает впн, попробовать [script](https://web.archive.org/web/20210117081918/https://github.com/andrewgdotcom/openvpn-mac-dns)

Проверено работает на openvpn stable 2.4.7 + openvpn-mac-dns без конфликтов с OpenVpn Connect 2.1.3
