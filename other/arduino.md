
Arduino

[Электричество в квартире](/web/20210123174052/http://wiki.n5g.ru/elektricestvo-v-kvartire)  
[Датчики Arduino](/web/20210123174052/http://wiki.n5g.ru/datciki-arduino)  
[Programming ESP8266](/web/20210123174052/http://wiki.n5g.ru/programming-esp8266)  
[Arduino IDE Reference](https://web.archive.org/web/20210123174052/https://www.arduino.cc/en/Reference/HomePage)

Общие сведения
==============

Катот - электрод некоторого прибора, присоединённый к отрицательному полюсу источника тока.  
Анод - положительному полюсу

Arduino API
===========

val = analogRead() - val = значения 0-1024 что соответствует 0-5 вольт  
analogWrite(val) - val = значения от 0 до 255  
digitalWritel()  
digitalRead()  
Serial.begin(9600)  
Serial.println(value)  
pinMode(PORT, OUTPUT/INPUT) - регестрировать только цифровые выходы

Идеи
====

Газовая колонка
---------------

Вентиляция в квартире
---------------------

Переносной датчик
-----------------

на борту:  
\- Датчик влажности  
\- Датчик температуры  
\- Датчик углекислого газа  
\- Датчик пыли  
\- Датчик воздушного давления  
\- Датчик освещености  
Вывод на TFT экран  
Работает от акамулятора  
Может заряжатся  
И работать от разетки  
[Пример](https://web.archive.org/web/20210123174052/http://g02.a.alicdn.com/kf/HTB1ulhBKVXXXXcCXVXXq6xXFXXXs/Household-PM2-5-detector-air-quality-monitoring-PM2-5-dust-haze-measuring-sensor-TFT-LCD-G3.jpg)

Пайка
-----

Паяльник 25-40вт достаточно, 40-60вт многовато, выше 60вт дохера.  
Припой - олово  
Флюс - канифоль  
Бывает припой сразу с флюсом.
