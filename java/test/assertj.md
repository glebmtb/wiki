
Сравнение двух объектов POJO:
```
import static org.assertj.core.api.Assertions.assertThat;

    assertThat(obj1).usingRecursiveComparison()
        .ignoringFields("id", "creationDate") // поля, которые не должны участвовать в сравнении
        .isEqualTo(obj2);
```

Точное сравнение двух списков (те количество элементов должно совпадать) по одному полю
```
    import static org.assertj.core.api.Assertions.assertThat;
    assertThat(result)
        .usingElementComparatorOnFields("id") //поля по которым надо сравнивать
        .containsExactlyInAnyOrderElementsOf(Arrays.asList(entity2, entity3));
```
