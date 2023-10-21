
менеджер пакетов **[zypper](https://web.archive.org/web/20210116091057/http://ru.opensuse.org/SDB:Zypper_%D0%B8%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5_11.3)**  
поиск пакетов [http://software.opensuse.org/123/ru](https://web.archive.org/web/20210116091057/http://software.opensuse.org/123/ru)  
список пакетов\*\* - \*\*zypper se  
удаление - zypper rm package  
переустановить - zypper in -f package

zypper # вывести список доступных глобальных опций и команд  
zypper help search # вывести справку для команды search  
zypper lр # увидеть, какие требуются патчи-обновления  
zypper patch # применить необходимые патчи  
zypper se sqlite # поиск sqlite  
zypper rm sqlite2 # удалить sqlite2  
zypper in sqlite3 # установить sqlite3  
zypper in yast\* # установить все пакеты по шаблону yast\*  
zypper up # обновить все установленные пакеты до последних версий, где возможно

подключение репозитория для версии 12.3 - **zypper addrepo [http://download.opensuse.org/repositories/devel:/tools:/scm/openSUSE\_12.3/devel:tools:scm.repo](https://web.archive.org/web/20210116091057/http://download.opensuse.org/repositories/devel:/tools:/scm/openSUSE_12.3/devel:tools:scm.repo)**  
добавления репозитория - zypper ar <URL> <псевдоним>  
Вывод списка репозиториев - zypper lr  
Удалить репозиторий - zypper rr номер  
[список реп](https://web.archive.org/web/20210116091057/http://ru.opensuse.org/%D0%94%D0%BE%D0%BF%D0%BE%D0%BB%D0%BD%D0%B8%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D1%8B%D0%B5_%D1%80%D0%B5%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%BE%D1%80%D0%B8%D0%B8):  
zypper ar [http://download.opensuse.org/distribution/12.3/repo/oss/](https://web.archive.org/web/20210116091057/http://download.opensuse.org/distribution/12.3/repo/oss/) Oss  
zypper ar [http://download.opensuse.org/distribution/12.3/repo/non-oss/](https://web.archive.org/web/20210116091057/http://download.opensuse.org/distribution/12.3/repo/non-oss/) Non-oss  
zypper ar [http://download.opensuse.org/update/12.3/](https://web.archive.org/web/20210116091057/http://download.opensuse.org/update/12.3/) Update

установка git - **zypper install git-core**
