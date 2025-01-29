```java


@Override
public void initialize(ConfigurableApplicationContext configurableApplicationContext) {
    TestPropertyValues values = of("some.property.url=" + someValue);    
    values.applyTo(configurableApplicationContext);
}

class SomeService{
    @Value("${some.property.url}")
    private String url; 
}
```