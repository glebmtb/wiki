
\- Настроить работу с SSD ([с ubuntu.ru](https://web.archive.org/web/20210123161701/http://help.ubuntu.ru/wiki/ssd) )  
\- Настроить работу с аккумулятором ([c ubuntu.ru](https://web.archive.org/web/20210123161701/http://help.ubuntu.ru/wiki/laptop_mode) )

**Отключение и добавление горячих клавиш:**  
Параметры системы -> Клавиатура -> Комбинации клавиш  
переделать ctrl+alt+left на win+left и другие стрекли тоже

**Включения дополнительных рабочих столов:**  
Параметры системы -> Внешний вид-> Поведение -> Задействовать рабочие места

**Создание ярлыков:**  
устанавливаем нужный пакет  
apt-get install --no-install-recommends gnome-panel  
запускаем программу  
gnome-desktop-item-edit --create-new ~/Рабочий /стол  
~/Рабочий /стол - куда положиться новый ярлык

**Включить спящий режим:**  
sudo gedit /var/lib/polkit-1/localauthority/50-local.d/hibernate.pkla  
Когда откроется редактор с файлом, скопируйте и вставьте в него строки ниже, а затем сохраните:  
\[Re-enable hibernate by default\]  
Identity=unix-user:\*  
Action=org.freedesktop.upower.hibernate  
ResultActive=yes

**Как включить скроллинг двумя пальцами по тачпаду**  
1\. Через центр приложений устанавливаем dconf-tools  
2\. Запускаем dconf-editor  
3\. Открываем ветку org/gnome/settings-daemon/peripherals/touchpad  
4\. Меняем значение параметра scroll-method на two-finger-scrolling  
5\. Проверяем чтобы параметр touchpad-enabled был включён

**Изменить программу по умолчанию:**  
Правой кнопкой по файлу который хотим открыть.  
Выбираем свойства, в открывшемся окне переходим на вкладку "Открыть в"  
Выбираем программу и нажимаем "Использовать по умолчанию"

Список программ
---------------

**Системные программы**  
HardInfo - информация об железе  
Disks - информацию о подключенных дисках

**Разное**  
Skype (с офф. сайта)  
Chrome (с офф. сайта)  
TeamViewer - удаленный доступ к компьютеру  
[BitTorrent Sync](/web/20210123161701/http://wiki.n5g.ru/bittorrent-sync) - шарить файлы между устройствами  
[VLC](/web/20210123161701/http://wiki.n5g.ru/vlc) - видео плеер  
Transmission - torrent клиент  
[KeePass](/web/20210123161701/http://wiki.n5g.ru/keepass) - хранение паролей (с офф. сайта)

**Программы для разработки**  
программы для установки sudo apt-get install:  
maven  
git  
git-gui

программы для установки через менеджер программ:  
KRename  
KDiff3  
Krusader - ?

программы для установки c офф сайтов  
Java JDK  
IntelliJ IDEA  
Sublime Text 2

разное:  
\- TomCat  
\- Git  
\- Maven  
\- Gradle  
\- Java JDK 7  
\- IntelliJ IDEA

**(редактирует)**  
pidgin  
remmina  
PyCarm (со всем барахлом для разработки)  
radiotray (не могу без «нашего радио»)  
gimp 2.8  
nanoshot

Горячие клавиши
---------------

ctrl + alt + t

Открыть консоль на иксах

ctrl + alt + f1

Переход в консольный режим

alt + f2

Окно "выполнить команду"

Изменение разрешения экрана загрузки
------------------------------------

hwinfo —framebuffer - список доступных разрешений  
sudo gedit /etc/default/grub - редактируем файл добавляя следующее:  
GRUB\_CMDLINE\_LINUX="gfxpayload=true"  
GRUB\_GFXMODE=1280x800x24  
GRUB\_GFXPAYLOAD\_LINUX=1280x800
