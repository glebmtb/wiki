##### Проверка на возникновение ошибки

```java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertThrows;

public class ExceptionTest {

    @Test
    public void whenExceptionThrown_thenAssertionSucceeds() {
        // Определите класс исключения, которое вы ожидаете
        Class<IllegalArgumentException> expectedType = IllegalArgumentException.class;

        // Выполните действие, которое должно привести к исключению
        IllegalArgumentException exception = assertThrows(expectedType, () -> {
            throw new IllegalArgumentException("Неверный аргумент");
        });

        // Проверьте сообщение исключения, если нужно
        assertEquals("Неверный аргумент", exception.getMessage());
    }
}
```
