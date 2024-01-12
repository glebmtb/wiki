Чтобы пустить только заблокированные сайты через OpenVpn нужно проделать в .ovpn такое:
1. Удалить (если есть)
Код:
```
redirect-gateway
```


2. Добавить
Код:
```
config routes
```
Рядом с .ovpn файлом должен лежать файл routes с таким содержимым:
Код:
```
route-nopull
route vk.com
route mail.ru
route yandex.ru
route rutracker.org
route static.rutracker.cc
route rutrk.org
route 8.8.8.8
```
3.В конце прописан dns сервер с которым должен работать Vpn - укажите правильный, также в случае использования отдельных маршрутов под системами Windows нужно будет прописать этот же dns в систему.
Для Windows 10 в конфиг .ovpn нужно добавить:
Код:
```
setenv opt block-outside-dns
```
