
**Общий вид команды:** команда опции аргументы  
**Опции:** начинаются с "-" - состоят из одной буквы, можно объединять в группы, пример: -la = -l -a  
начинаются с "--" состоят более чем из одной буквы, пример "--almost-all"  
**Специальные символы:**  
. - текущая директория  
.. - директория на уровень выше  
~ - домашняя директория  
\* - любое количество любых символов  
? - ровно один любой символ  
**Запустить в фоновом режиме:** в конце команды поставить &

Перенаправление вода и вывода

Программа <файл

брать из файла

Программа >файл

выводить в файл

Программа >>файл

выводить в файл, но с дозаписью

Программа 2>файл

выводить ошибки в файл

Программа 2>>файл

выводить ошибки в файл, но с дозаписью

Программа &>файл

выводить все в файл

Программа &>>файл

выводить все в файл, но с дозаписью

/dev/null - перенаправление в никуда

Сочетания клавиш для командной оболочки

Ctr + D

выход из текущего терминала

Ctr + Shift + C, Ctr + Insert

копировать

Ctr + Shift + V, Shift + Insert

вставить

Ctr + C

прервать выполнение

Ctr + Z

приостановить выполнение  
fg %<номер> - продолжить \[номер\]  
bg %<номер> - продолжить в фоновом режиме  
jobs - список программ в фоне

Работа в графическом терминале под linux

Ctr + Shift + T

открыть новую вкладку в терминале

Alt +<цифра>

перейти в указанную вкладку

Ctr + Shift + W

Закрыть указанную вкладку

Команды
-------

**[краткий список](https://web.archive.org/web/20210123173754/http://forum.ubuntu.ru/index.php?topic=79579.0)**, [очень полезные команды Linux на одном листе](https://web.archive.org/web/20210123173754/http://www.f-notes.info/linux:linux_command), [примеры использования команд](https://web.archive.org/web/20210123173754/http://ru.najomi.org/_nix)

**Вывести текущую директорию**  

    pwd

**Вывести содержимое директории**  
    
    ls  
опции: -h - более читабельный вид ,-l - отображать дополнительную информацию, -a - вывести все и скрытые папки.  
\--sort=\[size | time\]

**Присоединиться к другой машине из под консоли**  

    ssh _логин@адрес\_сервера_ -p _порт_  
Пример: ssh xuser@55.23.621.118:22, ssh [\[email protected\]](/cdn-cgi/l/email-protection) -p 22  
\-t "command" - подключится и выполнить эту команду на удаленном сервере

**читать log файлы**  

    tail -f /log/file|grep error

**Определить версию Linux/Unix**  

    cat /etc/issue  
    cat \`ls /etc/\*{-,\_}{release,version} 2>/dev/null | head -n 1\`  
    lsb\_release -d  
    cat /etc/os-release

**Версия ядра**  

    uname -a

**Переименовать/пернести файл или папку**  

    mv _путь1 путь2_  
переместить путь1 в путь2

    mv _имя1 имя2_  
переименовать имя1 в имя2

**rpm**  

    rpm -e название проекта - удаление  
    rpm -qa - список установленных пакетов

**yum**  

    yum list installed | grep \* - список установленных пакетов

**zypper**  

    zypper se - список доступных пакетов  
    zypper lr - список репозиторий  
    zypper addrepo http:download.opensuse.org/repositories/devel:/tools:/scm/openSUSE\_12.3/devel:tools:scm.repo - добавление репозитория для 12.3

**Список репозиториев**  

    /etc/yum.repos.d/

**Создать папку**  
mkdir название\_папки

**Создать файл**  
touch название\_файла

**Копировать**  
cp что\_копировать куда\_копировать (cp -R для папок)

**Постраничный вывод**  
команда | more

**Подключить доп репозитории**  
rpm -i http:packages.sw.be/rpmforge-release/rpmforge-release-0.5.2-2.el6.rf.x86\_64.rpm

**Отслеживать процессы в реальном времени**  
top

top -u <имя пользователя>  
отслеживать процессы этого пользователя

top -n1000 -d5  
выведет 1000 процесов с интервалом обновления 5сек

колонка res - текущее использование оперативной памяти  
shift + p - сортировать по загрузки процессора  
shift + m - сортировать по занятости памяти  
с - показать полный путь к программе  
q - выход  
e - способ отображения кб/мб в процесах  
shift - e - способ отображения кб/мб в используемой памяти  
shift + w - сохранить текущую конфигурацию

**Просмотреть процессы**  
ps  
процессы текущего пользователя

ps ax  
x : процессы, отсоединённые от терминала;  
a : процессы, связанные с текущим терминалом, а также процессы других пользователей.

ps o pid,user,command  
опция o позволяет указать набор столбцов в ответе:

ps ax | less  
для команды ps удобно пользоваться конвейером и утилитой less для пролистывания выводимой информации с помощью кнопок вверх и вниз

ps ax | grep smbd  
с помощью утилиты grep удобно искать и выводить только нужные процессы

**Завершение процессов**  
kill <номер процесса>  
завершить процесс с этим номером

kill -9 <номер процесса>  
"убить" процесс с этим номером

killall _имя_  
убить все процессы с этим именем

**если процесс завис**  
ps ax | grep _программа_ - узнаем pid  
kill -9 \[pid\] - убиваем процесс

**Изменить пароль**  
passwd user

**Удаление файлов и папок**  
rm name\_file - удаление файла  
rm -r name\_dir - удаление папки  
Опции: -f - удалять не спрашивая

**Скачивание файлов из интернета**  
wget _ссылка_  
скачать файл по ссылке и сохранить в текущей директории

wget -P _путь\_до\_директории ссылка_  
скачать файл по ссылке и сохранить в директории загаданной путем

wget -O _путь\_до\_файла ссылка_  
скачать файл по ссылке и сохранить под указанным именем

wget -с _ссылка_  
докачать файл по ссылке в случае обрыва связи

wget —spider _ссылка_  
проверить доступность файла по ссылке

wget -i _текстовый\_файл_  
скачать несколько файлов по ссылкам из текстового файла

wget -r -l _глубина ссылка_  
рекурсивное скачивание файлов по ссылке на указанную глубину (по умолчанию глубина 5)

wget -r -A _тип,тип,…,тип ссылка_  
рекурсивное скачивание файлов только определенного типа (типов)

**Пакеты Ubuntu**  
sudo apt-get install _программа_  
установка программ через терминал

sudo apt-get remove _программа_  
удаление программ через терминал

sudo apt-cache search _программа_  
поиск пакета

sudo apt-get update  
обновление ссылок на пакеты

sudo apt-get upgrade  
обновление установленных пакетов

sudo apt-get install --only-upgrade _программа_  
обновление отдельной программы

dpkg -l  
список установленных пакетов

sudo apt-key adv —recv-key —keyserver keyserver.ubuntu.com 241FE6973B765FAE  
восстановление ключа при "Ошибка GPG:"

**Пакеты в Centos**  
sudo yum install название\_пакета

sudo yum remove название\_пакета  
удаление

**Копирование файлов**  
scp -P _порт логин@адрес\_сервера:путь1 путь2_  
копирование с сервера (путь1) на клиент (путь2)

scp -P _порт путь1 логин@адрес\_сервера:путь2_  
копирование с клиента (путь1) на сервер (путь2)

**запуск приложения**  
чтобы управление у тебя не забрало в конце & поставь

**открытые порты**  
netstat -ltupn  
netstat -anut

для мака  
netstat -na| grep 104.16.240.21  
\-n - Показывать сетевые адреса как числа. netstat обычно показывает адреса как символы. Эту опцию можно использовать с любым форматом показа.  
\-a - Показывать состояние всех сокетов; обычно сокеты, используемые серверными процессами, не показываются.  
ESTABLISHED - Соединение установлено.  
TIME\_WAIT - Сокет закрыт, но ожидает пакеты, ещё находящиеся в сети для обработки  
[подробнее](https://web.archive.org/web/20210123173754/https://ru.wikipedia.org/wiki/Netstat)

**остановить фаервол**  
/sbin/SuSEfirewall2 off - openSuse

**добавить группу**  
groupadd название\_группы

**список групп**  
cat /etc/group

**Изменить имя хоста**  
hostnamectl set-hostname new-hostname

**Параметры среды**  
/etc/profile

**Поднятия SOCKS через ssh**  
ssh -D 1080 your.ubuntu.host

**Редактировать крон**  
crontab -e

**Переброс портов**  
LocalForwards ssh -L local\_listen\_port:destination\_host:destination\_port - открываем локальный порт который будет переноправлять данные на удаленный порт  
RemoteForwards ssh -R remote\_listen\_port:destination\_host:destination\_port - открываем на сервере порт который будет присылать данные на локальный порт

ssh -2 -N -f -L 5023:localhost:23 moc.elpmaxe.oof|resu#moc.elpmaxe.oof|resu  
\-N - Означает использование в не-командном режиме, только для туннелирования. Если этот параметр опущен, ssh запустит обычную сессию.  
\-f - Указывает ssh запускаться в фоновом режиме.  
\-L - Означает локальный туннель в стиле localport:remotehost:remoteport.

**Выполнить команду от рута**  
sudo команда

**Выключение компьютера**  
sudo halt -p

**Имя машины**  
hostname  
uname -n

**Выполнить от имени другого пользователя**  
sudo -u user <команда>

**Работа с архивами**  
unzip _архив.zip_  
распаковать содержимое _архива.zip_

gunzip _архив.gz_  
распаковать содержимое _архива.gz_  
файл _архив.gz_ удалить

tar -xvf _архив.tar_  
распаковать архив.tar

tar -xzvf _архив.tar.gz_  
распаковать _архив.tar.gz_ (с использованием gunzip)

zip _архив.zip файл1 файл2 …_  
запаковать перечисленные файлы и/или папки в архив.zip

gzip _файл_  
запаковать файл в архив.gz, исходный файл удалить

tar -cvf _архив.tar файл1 файл2 …_  
запаковать перечисленные файлы и/или папки в архив.tar (без сжатия)

gzip _архив.tar_  
запаковать архив.tar в архив.tar.gz, исходный архив.tar удалить

tar -zcvf _архив.tar.gz файл1 файл2 …_  
запаковать перечисленные файлы и/или папки в архив.tar.gz (с сжатием при помощи gzip)

\- bz2  
bzip2 _файл_ - упаковать  
bunzip2 _файл.bz2_ - распаковать  
tar -cjvf _архив.tar.bz2 файл1 файл2 …_ - упаковать  
tar -xjvf _архив.tar.bz2_ - распаковать

**поиск файлов и слов в файлах**  
find <папка> -name "<имя файла>"  
найти указанный файл в папке

find -iname "<имя файла>"  
не учитывать регистр

find -path "<путь>"  
найти указанный путь

find -size <размер>  
выводить файлы указанного размера

find -maxdepth <число>  
искать не больше чем на заданное число уровней

find -mindepth <число>  
искать начиная с заданного числа уровней

grep "<строка>" <файл>  
найти строку в файле

grep -c "<строка>" <файл>  
посчитать количество вхождений строки

grep -r "<строка>" <папка>  
найти строку во всех файлах в папке

grep -l "<строка>" <путь>  
список файлов с этой строкой

grep -L "<строка>" <путь>  
список файлов где этой строки нет

grep -n "<строка>" <путь>  
выводить номер строки в файле

grep -m <число> "<строка>" <путь>  
не искать дальше после заданного числа вхождений

grep -A <число> "<строка>" <путь>  
выводить это число строк после вхождений

grep -B <число> "<строка>" <путь>  
выводить это число строк до вхождения

grep -C <число> "<строка>" <путь>  
выводить это число строк вокруг вхождения

grep -E "<шаблон>" <путь>  
найти указанный шаблон в файле

`grep -r --include="*.java" "4007" .`
искать только в файлах с расширением .java 

**замена и вывод текста**  
cat <файл откуда брать> | sed 's/<что искать>/<на что заменить>/g' > <файл куда записать>  
заменит текст

sed -r 's/<что искать>/<на что заменить>/g' <файл откуда брать> > <файл куда записать>  
заменит текст с использование регулярных выражений

sed -n '2,4p' file.txt  
вывести строки с 2 по 4

sed '2,4d' file.txt  
вывести все строки кроме 2-4

**отображает полный путь к файлу или к программе**  
где находится исполняемый файл  
which <программа или файл>

**посчитать в файле**  
wc -l <file>  
количество строк

wc -w <file>  
количество слов

wc -c <file>  
количество символов

**Сравнить файлы и директории**  
diff \[-q -r\] <path1> <path2>  
r - рекурсивно; q - не выводить разницу, а только сообщать факт

**Создание альясов**  
alias <новая\_команда>='<вызываемая\_команда>'  
храниться на время сессии

**Отключить пароль sudo**  
sudo visudo  
and add the following line to the sudoers list  
username ALL = NOPASSWD : ALL

Редактирование файлов в командной строке
----------------------------------------

**cat _файл_**  
вывести содержимое файла на экран

**less _файл_**  
открыть файл на чтение  
q - выход; / - поиск; g - в начало; G - в конец

**nano _файл_**  
редактировать файл  
ctr + x - выход;

**vim _файл_**  
редактировать файл; [команды](/web/20210123173754/http://wiki.n5g.ru/vim)

Информация об железе
--------------------

**Размер директорий**  
du -h --max-depth=1

**Свободное место**  
df -h

**Список подключенных дисков**  
sudo fdisk -l  
cat /proc/partitions  
sudo mount

**Данные по RAM**  
vmstat -s  
или  
cat /proc/meminfo

**Получение информации об аппаратной части RAM**  
sudo dmidecode —type 17

**Информацию о пределах возможностей подсистемы управления памятью**  
sudo dmidecode —type 16

**Данные о CPU**  
cat /proc/cpuinfo  
или  
lscpu

**Подключенные устройства**  
lsusb  
lspci

**Информация об оперативной памяти**  
free -g

**Количество ядер в процессоре**  
nproc

**Детальная информация об процессоре**  
lscpu

**Модель тачпада**  
egrep -i 'synap|alps|etps' /proc/bus/input/devices

**Информация о подключенных устройствах**  
xinput

больше информации о подключенном устройстве  
xinput list-props <device id|device name>

    lshw - команда выведет полную информацию о железе, следует выполнять с правами root'а (sudo lshw).
    hwinfo - вывод информации о железе. Предварительно требуется установить утилиту (sudo apt-get install hwinfo).
    uname -a - вывод информации о системе, версии ядра, дистрибутиве и архитектуре (32/64 бита).
    lsb_release -a - выведет название и версию используемого дистрибутива.
    cat /etc/*release* - аналогично предыдущей команде, плюс информация о базовом дистрибутиве (например, для Linux Mint 9 выведет еще и Ubuntu 10.04, как базовый дистрибутив).
    ls -clt / | tail -n 1 | awk '{ print $7, $6, $8 }' - с помощью этой команды можно узнать дату и время установки системы.
    ls -dl /var/log/installer/ - аналогично предыдущей команде (но немного иного принципа), позволяет узнать дату и время установки системы.

Права доступа
-------------

**Кто сейчас в системе**  
users

**Информация о пользователях, работающих в данный момент**  
w

**Список пользователей**  
less /etc/passwd

**Узнать группу пользователя**  
groups <имя\_пользователя>

**Права у файлов**  
r - просмотр содержимого  
w - редактирование  
x - запуск

**Права у директорий**  
r - просмотр содержимого  
w - создание или удаление файлов/поддиректорий  
x - 1) вход в директорию 2) просмотр inode файлов/поддиректорий

**изменение прав доступа**  
chmod \[ugoa\] \[+-\] \[rwx\] <путь>  
u - юзер; g - группа; o - других; a - для всех; + - дать права; - - убрать права

chmod \[code ugo\] <путь>  
7 = rwx; 6 = rw; 5 = rx; 4 = r; 0 - без прав;

на папки лучше ставить 755 а на файлы 644

    400 (-r--------)
    Владелец имеет право чтения; никто другой не имеет права выполнять никакие действия
    644 (-rw-r--r--)
    Все пользователи имеют право чтения; владелец может редактировать
    660 (-rw-rw----)
    Владелец и группа могут читать и редактировать; остальные не имеют права выполнять никаких действий
    664 (-rw-rw-r--)
    Все пользователи имеют право чтения; владелец и группа могут редактировать
    666 (-rw-rw-rw-)
    Все пользователи могут читать и редактировать
    700 (-rwx------)
    Владелец может читать, записывать и запускать на выполнение; никто другой не имеет права выполнять никакие действия
    744 (-rwxr--r--)
    Каждый пользователь может читать, владелец имеет право редактировать и запускать на выполнение
    755 (-rwxr-xr-x)
    Каждый пользователь имеет право читать и запускать на выполнение; владелец может редактировать
    777 (-rwxrwxrwx)
    Каждый пользователь может читать, редактировать и запускать на выполнение
    1555 (-r-xr-xr-t)
    Каждый пользователь имеет право читать и запускать на выполнение; удалить файл может только владелец этого файла
    2555 (-r-xr-sr-x)
    Каждый пользователь имеет право читать и запускать на выполнение с правами группы(user group) владельца файла
    4555 (-r-sr-xr-x)
    Каждый пользователь имеет право читать и запускать на выполнение с правами владельца файла

**Изменить обладателя**  
chown <user>:<group> <path>

Работа с сетью
--------------

**Пинг TCP порта**  
nc -zv localhost 20

**Тестирование пропускной способности канала (трафик)**  
iperf -s - запустить в режиме сервера  
iperf -c host -n 100m - передать 100мб данных  
другие команды:  
\-i10 - показывать результат каждые 10 сек  
\-u - тестировать UDP  
\-l100 - длина файла 100 байт

**Сканирование портов**  
nmap -sS -T4 -n <target>  
\-sS - sean scan, отправляем пакет и смотрим на реакцию системы на этот пакет  
\-T4 - taiming template, больше число более агрессивно и быстрее, меньше число будем дольше ждать  
\-n - мы не хотим резолвить обратный ip адреса  
\-A - более углубленный анализ цели  
\-p <ports> - сканировать порты  
\-p 1-65535 - сканить все порты

**Получить свой внешний IP**  
curl -s [https://2ip.ru/](https://web.archive.org/web/20210123173754/https://2ip.ru/) | grep -E -o "(\[0-9\]{1,3}\[\\.\]){3}\[0-9\]{1,3}" -m 1

**бенчмарк http запросов**  
[install](https://web.archive.org/web/20210123173754/https://github.com/wg/wrk/wiki/Installing-Wrk-on-Linux)  
wrk -t12 -c400 -d30s [http://127.0.0.1:8080/index.html](https://web.archive.org/web/20210123173754/http://127.0.0.1:8080/index.html)

This runs a benchmark for 30 seconds, using 12 threads, and keeping 400 HTTP connections open.

**Время запроса на урл**  
1\. Create a new file, curl-format.txt, and paste in:

    time_namelookup: %{time_namelookup}\n
    time_connect: %{time_connect}\n
    time_appconnect: %{time_appconnect}\n
    time_pretransfer: %{time_pretransfer}\n
    time_redirect: %{time_redirect}\n
    time_starttransfer: %{time_starttransfer}\n
    ----------\n
    time_total: %{time_total} seconds\n
    \n
    size_request: %{size_request} byte\n
    size_download : %{size_download} byte\n
    http_code: %{http_code}\n

  
2\. Make a request

    curl -w "@curl-format.txt" -o /dev/null -s "http://wordpress.com/"

**Установка локали ru utf8**  
Warning: No support for locale: ru\_RU.utf8  
sudo dpkg-reconfigure locales  
если не помогло то [решение](https://web.archive.org/web/20210123173754/http://www.openkazan.info/linuxmint-warning-locale)

**Hard Link Folder**  
копия папки

    mount --bind /usr /home/user/foo
