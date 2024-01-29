
PODAM (POjo DAta Mocker) - предназначен для автоматического заполнения Java POJOs (Plain Old Java Objects) случайными данными. 
Он автоматически анализирует POJO и заполняет их атрибуты. PODAM позволяет настраивать процесс заполнения данных, 
предлагая определение глобальных стратегий и стратегий на уровне атрибутов. Инструмент поддерживает настройку значений 
для примитивных типов и обертывающих классов через аннотации. Также возможно исключение некоторых атрибутов из процесса 
заполнения данных. PODAM поддерживает настройку заполнения данных для коллекций, карт и массивов. Этот инструмент обладает 
гибкостью и масштабируемостью, позволяя использовать его в различных сценариях тестирования. PODAM распространяется под 
лицензией MIT, что делает его доступным для широкого круга разработчиков. Поддержка различных систем сборки и управления 
зависимостями, таких как Maven и Gradle, делает его интеграцию удобной в различные проекты.


Добавление в проект:
`integrationTestImplementation("uk.co.jemos.podam:podam:7.2.11.RELEASE")`

Использование:
```
PodamFactory factory = new PodamFactoryImpl();
PojoEntity entity = factory.manufacturePojo(PojoEntity.class);
```

Игнорирование полей которые не нужно генерировать:
```
  @Before
  public void setUp() throws Exception {
    DefaultClassInfoStrategy classInfoStrategy = DefaultClassInfoStrategy.getInstance();
    classInfoStrategy.addExcludedField(ApplicableDiscountEntity.class, "id");
    classInfoStrategy.addExcludedField(ApplicableDiscountEntity.class, "someField");
  }
```