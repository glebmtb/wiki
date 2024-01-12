
Пример:
```java

import reactor.core.publisher.Mono;

public class TestMono {
  public static void main(String[] args) {


    Mono<Void> testObject = Mono.empty();

    Mono<String> result = testObject
        .then(Mono.defer(() -> firstMethod()))
        .flatMap(ignored -> secondMethod())
        .then(therdMethod());
    
    System.out.println("hello world");
    System.out.println(result.block());
  }

  public static Mono<String> firstMethod() {
    System.out.println("firstMethod: do some work");
    return Mono.just("firstMethod");
  }

  public static Mono<String> secondMethod() {
    System.out.println("secondMethod: do some work");
    return Mono.just("secondMethod");
  }

  public static Mono<String> therdMethod() {
    System.out.println("secondMethod: do some work");
    return Mono.just("therdMethod");
  }
}

```

Результат:
```text
secondMethod: do some work
hello world
firstMethod: do some work
secondMethod: do some work
therdMethod
```