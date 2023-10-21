
**Псевдонимы (алиасы) bash**  
все свои алиасы хроним в ~/.bash\_aliases

#пример
alias art\="php artisan"

#перегрузить алиасы
. ~/.bashrc //for Ubuntu
source .bash\_profile //for MacOs

**Алиасы для клавиш в bash (горячи клавиши)**  
настройки в файле /home/<user>/.inputrc

**Алиасы и опции для подключений в .ssh/config**  
Файл ~/.ssh/config позволяет задать параметры подключения, в том числе специальные для серверов, что самое важное, для каждого сервера своё. Вот пример конфига:

    Host ric
            Hostname ооо-рога-и-копыта.рф
            User Администратор
            ForwardX11 yes
            Compression yes
    Host home
            Hostname myhome.dyndns.org
            User vasya
            PasswordAuthentication no

  
Все доступные для использования опции можно увидеть в _man ssh\_config_

**Алиас на папку**

    alias myfold='cd ~/Files/Scripts/Main'
    #Then you can just use (without the cd):
    myfold

  
алиасы хранятсы тут: ~/.bashrc
