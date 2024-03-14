main application 
https://docs.gradle.org/current/userguide/application_plugin.html

for kotlin
```
object Main {
    @JvmStatic
    fun main(args : Array<String>) {
        println("Hello, World!")
    }
}
```

```
// Включить вывод стандартного потока вывода и ошибок в консоль во время тестирования в случае если тест упал
test {
    testLogging {
        showStandardStreams = true
        events "failed" //похоже это не влияет но не проверил
    }
}
```