
**Сокращения**  
VTL - Velocity Template Language

**Разные ссылки**  
[rus wiki](https://web.archive.org/web/20210116100042/https://ru.wikipedia.org/wiki/Apache_Velocity)  
[небольшое Hello World](https://web.archive.org/web/20210116100042/http://y3x.ru/2011/12/velocity-templates/)  
[хорошее описание основ](https://web.archive.org/web/20210116100042/http://rulinux.org/?p=71)  
[небольшой обзор на Хабре](https://web.archive.org/web/20210116100042/http://habrahabr.ru/post/47564/)

**Примеры**

//Загрузка ресурсов из класс лоудера
Velocity.setProperty(RuntimeConstants.RESOURCE\_LOADER, "classpath");
Velocity.setProperty("classpath.resource.loader.class", ClasspathResourceLoader.class.getName());
