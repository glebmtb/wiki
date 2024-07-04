
Сравнение двух объектов POJO:
```
import static org.assertj.core.api.Assertions.assertThat;

    assertThat(actual).usingRecursiveComparison()
        .ignoringFields("id", "creationDate") // поля, которые не должны участвовать в сравнении
        .isEqualTo(expected);
```

Точное сравнение двух списков (те количество элементов должно совпадать) по одному полю
```
    import static org.assertj.core.api.Assertions.assertThat;
    assertThat(result)
        .usingElementComparatorOnFields("id") //поля по которым надо сравнивать
        .containsExactlyInAnyOrderElementsOf(Arrays.asList(entity2, entity3));
```
