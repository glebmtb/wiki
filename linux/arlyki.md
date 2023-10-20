
**Создать ярлык**  
На рабочем столе правой кнопкой мыши, и выбираем "Создать кнопку запуска здесь"

**Шаблон .destktop файла**

    [Desktop Entry]
    Version=1.0
    Type=Application
    Name=Git Extensions
    Icon=/opt/GitExtensions/gitextensions.2.49.02.svg
    Exec="/opt/GitExtensions/gitext.sh" %f
    Comment=The Drive to Develop
    Categories=Development;    
    Terminal=false
    StartupWMClass=jetbrains-idea

**Посмотреть StartupWMClass для приложения**

    xprop WM_CLASS

**Папка с ярлыками**  

    ~/.local/share/applications/

**Папка с настройками Plank**  

    ~/.config/plank/dock1/launchers/
