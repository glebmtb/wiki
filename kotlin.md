**let, also, apply**
```
fun main() {
  val test1 = "hello world".apply {
    "test"
  }
  println(test1) //this -> hello world

  val test2 = "hello world".let {
    "test"
  }
  println(test2) //it -> test

  val test3 = "hello world".also {
    "test"
  }
  println(test3) //it -> hello world
}
```
**for**
```
for (indexItem in 0..codesRows.size) {
  println(indexItem)
}
```    
