
**GUI вариант**  
sudo apt install samba smbclient system-config-samba

открываем system-config-samba и добавляем все что нужно

**Серверный вариант**

Установка и настройка Samba

Установим Samba:  
sudo apt-get install samba samba-common-bin

Так как моя Rpi находится в домашней сети, я решил не устанавливать пароль на доступ к папкам, а просто настроил публичный шаринг для всей сети.  
Для этого открываем файл smb.conf:  
sudo nano /etc/samba/smb.conf

Вместо всего имеющегося содержимого пишем:

    [global]
    workgroup = WORKGROUP
    guest ok = yes
    netbios name = Raspberry
    security = share
    browseable = yes
    
    [www]
    path = /var/www
    writeable = yes
    browseable = yes

  
Сохраняем. Перезапускаем Samba:  
sudo /etc/init.d/samba restart

С этого момента в вашей сети появилось новое устройство RASPBERRY, которое имеет папку www.  
В ней Вы можете создать любые файлы, которые будут доступны для просмотра во всей сети с помощью браузера.

Кстати! Гораздо удобнее управлять шарингом файлов и папок с помощь программы SWAT, которая предоставляет веб-интерфейс.  
Установить ее очень просто:  
sudo apt-get install swat

Панель управления SWAT будет расположена по адресу: [http://\[IP-устройства\]:901](https://web.archive.org/web/20210123163211/http://ip-%D1%83%D1%81%D1%82%D1%80%D0%BE%D0%B9%D1%81%D1%82%D0%B2%D0%B0:901/)  
логин и пароль соответствуют Вашей учетной записи (той, которой Вы пользуетесь для SSH) **надо входить под root**
