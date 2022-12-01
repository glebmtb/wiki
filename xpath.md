**XPath**
```
//input[@id="someId"]/../button
//input[@id="someId" and contains(text(), 'text') and not(@style='display:none')]
```
`input` - елемент  
`@id` - название атрибута  
`..` - переход к вышестоящему элементу  
`text()` - текст элемента

**поиск по содержимому**  
`contains(@class, 'text')`
`starts-with(@class, 'text')`

**поиск по совпадению класса один в один**  
`contains(concat(' ', @class, ' '), ' pmts-error-message-inline ')`



