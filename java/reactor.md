


**Mono** - один элемент  
**Flux** - список элементов, последовательность  

###  методы
`mono.map()` - для выполнения синхронного кода который работает без засыпания и отробатывает моментально  
`mono.flatMap()` - для вызова асинхронных функций  
`Mono.zip([асинхронные методы])` - для вызова несколькоих асинхронных функций с целью дождатся их выполнения, и передать ответ дальше  
`Mono.fromFuture()` - из фючи в mono объект  
`Mono.just()` - вернуть объект обернутый в моно  
`mono.toFuture()` - из Моно в CompletableFuture  
`Flux.collectList()` - и флюкса в моно<лист>  
`Mono.empty()` - вернет пустоту, если допустим надо вернуть Mono<Void> то отлично подойдет  
`Flux.fromIterable()` - построить Flux из List  
`mono.flatMapMany(Flux::fromIterable)` - из Mono сделать Flux  
`Mono.fromCompletionStage()` - тоже самое что и Mono.fromFuture() но лучше fromFuture  
`mono.doOnSuccess()` - аналог thenAcceptAsync, метод позволяет выполнить какое-то действие с результатом, полученным от Mono или Flux, не изменяя сам поток данных  

### примеры:
[then](reactor-example-then.md)


### отладка

###### дополнительные дебаг логи
если падает поток не понятно где из за NPE,
поможет включить дебаг логи
```Hooks.onOperatorDebug();```

###### принт промежуточного состояния
```
.map(something)
.doOnNext(result -> System.out.println("Result: " + result))
.map(something)
```
`.doOnNext()` - позволяет выполнить действие для каждого элемента, проходящего через последовательность, не изменяя сам поток данных.

###### принт промежуточной ошибки
```
        .onErrorResume(e -> {
          System.err.println("Exception occurred during buildPdfAndSendToSp: " + e.getMessage());
          e.printStackTrace();
          return Mono.error(e); // Пробрасываем ошибку дальше, если необходимо
        });
```
`.onErrorResume()` — используется для обработки ошибок в потоке данных. Он позволяет перехватывать ошибки и предоставлять альтернативный поток данных в случае возникновения исключения.
