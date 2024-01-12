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

route rutracker.org
route static.rutracker.cc
route rutrk.org
route cdn.admitad-connect.com
route cdn.jsdelivr.net
route static.cloudflareinsights.com
route wallet.advcash.com
route 1xbet.kz

route openai.com
route chat.openai.com
route cdn.oaistatic.com
route widget.intercom.io
route js.intercomcdn.com
route lh3.googleusercontent.com
route tcr9i.chat.openai.com
route files.oaiusercontent.com

route instagram.com
route static.cdninstagram.com
route www.instagram.com
route www.facebook.com
route static.xx.fbcdn.net
route scontent-vie1-1.cdninstagram.com
route web-chat-e2ee.facebook.com
route gateway.instagram.com

route 8.8.8.8
```
3.В конце прописан dns сервер с которым должен работать Vpn - укажите правильный, также в случае использования отдельных маршрутов под системами Windows нужно будет прописать этот же dns в систему.
Для Windows 10 в конфиг .ovpn нужно добавить:
Код:
```
setenv opt block-outside-dns
```
