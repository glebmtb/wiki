[.gitignore](gitignore.md)  
[git_console](git-console.md)      
[Git на сервере - Настраиваем сервер](http://git-scm.com/book/ru/Git-%D0%BD%D0%B0-%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80%D0%B5-%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%B0%D0%B8%D0%B2%D0%B0%D0%B5%D0%BC-%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80)   


**Git и ssh:**  
по умолчанию git использует следующие ssh ключи
```
~/.ssh/id_dsa.pub
~/.ssh/id_rsa.pub
~/.ssh/identity.pub
```


**Установка:**  
-ubunta   
`
apt install git
`   
-OpenSuse   
`
zypper install git-core
`   



**Установка репозитория на сервере:**   
```
sudo adduser git #создаем пользователя git
su git #регистрируемся от пользователя git в системе
sudo mkdir /opt/git #создаем папку для репозиторий
sudo chown git /opt/git #ставим владельца пользователя git
sudo vim /etc/passwd #изменяем строчку git:x:1000:1000::/home/git:/bin/sh Замените /bin/sh на /usr/bin/git-shell для безопасности
```

**Инициализация репозитория на сервере**    
```
cd /opt/git #открываем папку с репозиториями
mkdir <repo_name>.git #по соглашения папки для гит репозиторий заканчивают имена окончанием .git
cd /var/git/<repo_name>.git
git --bare init #Параметр --bare инициализирует репозиторий без рабочего каталога.
sudo chown -R git /opt/git/<repo_name>.git #ставим владельца пользователя git
```

**Права на папку:** (для чего эта магия нужна не помню)   
```
cd /path/to/repo.git
chgrp -R git .
chmod -R g+rwX .
find . -type d -exec chmod g+s '{}' +
git repo-config core.sharedRepository true
```

**Установка git из исходников:**      
Скачиваем git - [http://git-scm.com/downloads git-1.*.*.*.tar.gz]     
Теперь скомпилируйте и установите:      
```
tar -zxf git-1.7.2.2.tar.gz
cd git-1.7.2.2
make prefix=/usr/local all
sudo make prefix=/usr/local install
```

**Создание нового репозитория в командной строке:**   
```
touch README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:mabden/simple_rmi.git
git push -u origin master
```

**Push существующего хранилища, из командной строки**     
```
git remote add origin git@github.com:mabden/simple_rmi.git
git push -u origin master
```

**Git консольный Destop**   
```
apt install git & gitk & git-gui && aspell-ru 
```

**Команды**   
Восстановить потерянный коммит    
git reflog - список состояний   
git merge 7c61179 - соединиться с нужным состоянием   

**Список старых веток**     
```
git for-each-ref --sort=committerdate --format='%(refname:short) * %(authorname) * %(committerdate:relative)' refs/remotes/ | column -t -s '*'
````

**Показать последнюю ветку**    
```
git for-each-ref --sort=-committerdate --format='%(refname:short)' refs/remotes/ | head -n 1
```

**Удалить ветку на удаленном сервере**    
```
git push origin --delete <branchName>
```

**удалить все ветки которые уже объединены**      
```
git branch --merged | grep -v '\*\|master\|develop' | xargs -n 1 git branch -d
```

**удалить все ветки на удаленном сервере, которые уже объединены**    
```
git branch -r --merged | grep -v '\*\|master\|develop' | sed 's/origin\///' | xargs -n 1 git push --delete origin
```

**Синхронизировать локальный реестр удаленных ветвей**    
```
git fetch -p
```

[http://qaru.site/questions/10906/how-can-i-delete-all-git-branches-which-have-been-merged про удаление веток]

**Отключить .origin файлы**   
```
git config --global mergetool.keepBackup false
```

**Удалить все .origin файлы**   
```
sudo find . -name '*.orig' -delete 
```

**удаления файлов, которые не находятся под управлением версиями.**   
```
Используйте git clean -xdn для выполнения сухого хода и посмотрите, что будет удалено. 
Затем используйте git clean -xdf для его выполнения.
```

**Отчет по репозиторию за опредмеченное время (sh скрипт)**   
[https://gist.github.com/eyecatchup/3fb7ef0c0cbdb72412fc More information]
```
#!/usr/bin/env bash
from="1 Jun, 2018"
to="17 Aug, 2018"
users=$(git shortlog -sn --no-merges --since="$from" --before="$to" | awk '{printf "%s %s\n", $2, $3}')
IFS=$'\n'
echo -e "User name;Files changed;Lines added;Lines deleted;Total lines (delta);Add./Del. ratio (1:n);Commit count"

for userName in $users
do
     result=$(git log --author="$userName" --no-merges --shortstat  --since="$from" --before="$to" | grep -E "fil(e|es) changed" | awk '{files+=$1; inserted+=$4; deleted+=$6; delta+=$4-$6; ratio=deleted/inserted} END {printf "%s;%s;%s;%s;%s", files, inserted, deleted, delta, ratio }' -)
     countCommits=$(git shortlog -sn --no-merges  --since="$from" --before="$to" --author="$userName" | awk '{print $1}')
     if [[ ${result} != ';;;;' ]]
     then
        echo -e "$userName;$result;$countCommits"
     fi
done
```

**Изменить ссылку на original(удаленный) репозитрий**     

```
git remote -v
git remote remove origin
git remote add origin {url}
git remote -v
```

**показать конфигурации git репозитория**   

```
git config -l
```

**Напечатать короткий хеш**   
``` 
git rev-parse --short HEAD
```

**удалить файл из индекса git**
надо указать полный путь к файлу
```
git rm --cached [file]
```
