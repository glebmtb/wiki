Проверка на возникновение ошибки
```
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

Exception exception = assertThrows(ExpectedExceptionType.class, () -> {
    // вызов метода, который должен выбросить исключение
});

// Проверка свойств исключения
assertEquals("Ожидаемое сообщение", exception.getMessage());
// другие ассерты для исключения
```