
*   [ssh key](linux/ssh-key.md)
*   [vim](linux/vim.md)
*   [Java SDK](linux/ustanovka-java-sdk-na-linux.md)
*   [Squid](linux/squid.md)
*   [PostgreSQL](linux/postgresql.md)
*   [Apache Tomcat](linux/apache-tomcat.md)
*   [Sphinx](linux/sphinx.md)
*   [OpenSUSE](linux/opensuse.md)
*   [nginx](linux/nginx.md)
*   [Переменные среды Linux](linux/peremennye-sredy-linux.md)
*   [VPN](linux/vpn.md)
*   [Zsh](linux/zsh.md)
*   [Samba](linux/samba.md)
*   [Алиасы](linux/alias.md)
*   [Безопасность](linux/bezopasnost.md)
*   [Ярлыки](linux/arlyki.md)

Destop
------
*   [Ubuntu destop](linux/ubuntu-destop.md)
----

[Скрипты на bash](linux/skripty-na-bash.md)  
[bash](bash.md)

Программы
---------

**Destop**  
launcher: [Synapse](synapse.md) (_sudo apt install synapse_)  
Хранение паролей: KeePassX (_sudo apt install keepassx_)  
Просмотр видео: SMPlayer (_sudo apt-get install smplayer_)  
Файловый менеджер: Double Commander (_sudo apt install doublecmd-gtk_), Gnome commander, [Krusader](https://web.archive.org/web/20211021092320/http://www.krusader.org/) (_sudo apt-get install krusader_)  
Просмотр фото: Gwenview (_sudo apt install gwenview_)  
Редактировать избражения: GIMP (_sudo apt-get install gimp_)  
Терминал: [Guake Terminal](guake-terminal.md) (_sudo apt install guake_), [PAC Manager](https://web.archive.org/web/20211021092320/https://sourceforge.net/projects/pacmanager/)  
Gui клиент для git: [SmartGit](https://web.archive.org/web/20211021092320/http://www.syntevo.com/smartgithg/welcome), GitKraken  
Браузер: [Chrome](chrome.md), Firefox  
IM клиент: Skype, Pidgin  
Среда разработки: IntelliJ IDEA  
Скриншоты: [Joxi](https://web.archive.org/web/20211021092320/http://joxi.ru/)  
FTP/SFTP клиент: filezilla  
Редактировать видео: kdenlive, audacity, lightworks  
Настройка звука: [PulseAudio](pulseaudio.md)  
Настройка жестов: Easystroke (_sudo apt install easystroke_)  
Док панель как в маке: Plank (_sudo apt install plank_), Docky, Cairo-Dock  
Управление жесткими: GParted (_sudo apt install gparted_)  
Cоздание Windows загрузочной флешки: [UNetbootin](https://web.archive.org/web/20211021092320/http://unetbootin.github.io/linux_download.html/)  
Преобразование звука: SoundConverter (sudo apt-get install soundconverter)  
Запись образов на flesh: [Etcher SD](https://web.archive.org/web/20211021092320/https://etcher.io/), [WoeUSB](https://web.archive.org/web/20211021092320/https://github.com/slacka/WoeUSB/releases)

Ярлыки (.destop файлы) складывать в /usr/share/applications

**Proxy:**  
[Squid](linux/squid.md)  
[Privoxy](privoxy.md)

**Консольные**  
[tmux](linux/tmux.md) - менеджер терминалов  
[vim](linux/vim.md) - текстовый редактор  
[gnuplot](linux/gnuplot.md) - программа для постарения графиков  
iptraf - активность сетевого интерфейса реалтайм  
[https://github.com/wg/wrk](wrk.md) - бенчмарк http запросов

**Разное**  
WebLog - красивый анализ access log

Разное
------

**Каталоги:**  
_/usr/bin_ - Дополнительные программы для всех пользователей, не являющиеся необходимыми в однопользовательском режиме. (sh скрипты для выполнения )  
_/opt_ - В этом каталоге размещаются дополнительные пакеты программ.  
_/etc/init.d_ - сервисы  
_/etc/default_ - настройки для сервиса  
~/.local/share/applications/ - ярлыки для системы

**Синхранизация времени**  
добаваляем строчку  
server ate.kirkazan.ru prefer  
в  
nano /etc/ntp.conf  
потом выполняем команду  
chkconfig -a ntp

**Дистрибутивы Linux с малым потреблением ресурсов**  
linux Mint Xfce  
Lubuntu  
Xubuntu

Desktop Environments for Linux

GNOME 2.x

Required RAM: 384 MB  
Required CPU: 800 MHz

GNOME 3

Required RAM: 768 MB  
Required CPU: 400 MHz

UNITY

Required RAM: 1 GB  
Required CPU: 1 GHz

KDE

Required RAM: 615 MB  
Required CPU: 1 GHz

CINNAMON

Required RAM: 512 MB  
Required CPU: 1 GHz

MATE

Required RAM: 512 MB  
Required CPU: 800 MHz

Xfce

Required RAM: 192 MB  
Required CPU: 300 MHz

LXDE

Required RAM: 128 MB  
Required CPU: 266 MHz

Enlightenment

Required RAM: 64 MB  
Required CPU: 200 MHz

**Полезные ссылки**  
[http://rus-linux.net/](https://web.archive.org/web/20211021092320/http://rus-linux.net/) - виртуальная энциклопедия Linux  
[Как получить работающий сервер как можно быстрее](https://web.archive.org/web/20211021092320/http://ru.opensuse.org/Apache_Quickstart_HOWTO)

**Настройка сетевых интерфейсов**  
ifconfig -a - показывает все интерфейсы и не активные тоже  
для активации нужно добавить в конфиг данные  
/etc/network/interfaces  
auto ethX  
iface ethX inet dhcp

**Настройка удаленного сервак на работу с мышкой**

    #VIM
    echo "set mouse=a" >> ~/.vimrc
    
    #NANO
    echo "set mouse" >> ~/.nanorc
    echo "set smooth" >> ~/.nanorc
    
    #TMUX
    echo "set -g mode-mouse on" >> ~/.tmux.conf
    echo "set -g mouse-select-pane on" >> ~/.tmux.conf
    echo "set -g mouse-select-window on" >> ~/.tmux.conf

**Enable Keep Alive**

    sudo nano /etc/ssh/ssh_config
    ServerAliveInterval 60
    
    or
    
    sudo nano ~/.ssh/config
    Host *
      ServerAliveInterval 60
    
    sudo service ssh restart

**Bluetooth audio**  
Удобный графический клиент bloetooth: Blueman  
Кодеки для нушников Bose: Ffmpeg
