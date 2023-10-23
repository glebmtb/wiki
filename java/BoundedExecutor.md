```
package es.ibs.tech.engine.resell.test

import org.junit.jupiter.api.Test
import org.slf4j.LoggerFactory
import java.util.concurrent.Callable
import java.util.concurrent.CompletableFuture
import java.util.concurrent.Executors
import java.util.concurrent.Semaphore
import kotlin.random.Random
import kotlin.random.nextInt

class TestThread {


  @Test
  internal fun name5() {
    val executor = BoundedExecutor(5)

    for (indexItem in 0..10) {
      executor.submitTask { testRun() }.thenAccept {
        println("[$indexItem] result $it")
      }.exceptionally {
        println("[$indexItem] exception ${it.message}")
        null
      }
    }
    executor.shutdown()
  }

  private fun testRun(): String {
    val time = Random.nextInt(IntRange(1000, 20000)).toLong()
    Thread.sleep(time)
    if(Random.nextBoolean()){
      throw RuntimeException("upppsss $time")
    }
    return time.toString()
  }

  class BoundedExecutor(private val poolSize: Int) {
    private val exec = Executors.newFixedThreadPool(poolSize)
    private val semaphore = Semaphore(poolSize)
    private val logger = LoggerFactory.getLogger(this.javaClass)

    fun <T> submitTask(command: Callable<T>): CompletableFuture<T> {
      semaphore.acquire()
      try {
        return CompletableFuture.supplyAsync({
          try {
            command.call()
          } finally {
            semaphore.release()
          }
        }, exec)
      } catch (e: Exception) {
        semaphore.release()
        throw e
      }
    }

    fun shutdown() {
      logger.info("call shutdown, active threads [${poolSize - semaphore.availablePermits()}]")
      while (semaphore.availablePermits() != poolSize) {
        Thread.sleep(100)
      }
      exec.shutdown()
    }
  }
}
```

```
package es.ibs.tech.engine.resell.test

import org.junit.jupiter.api.Test
import java.util.concurrent.Executors
import java.util.concurrent.Semaphore
import kotlin.random.Random
import kotlin.random.nextInt

class TestThread {


  @Test
  internal fun name() {

    val poolSize = 5

    val executor = BoundedExecutor(poolSize)

    for (indexItem in 0..10) {
      println("[$indexItem] schedule")
      executor.submitTask {
        val now = System.currentTimeMillis()
        val time = Random.nextInt(IntRange(1000, 20000)).toLong()
        println("[$indexItem] test run ms '$time'")
        Thread.sleep(time)
        println("[$indexItem] test stop planet '$time' but run ms '${System.currentTimeMillis() - now}'")
      }
      println("[$indexItem] scheduled")
    }
    println("shutdown")
    executor.shutdown()
  }

  class BoundedExecutor(private val poolSize: Int) {
    private val exec = Executors.newFixedThreadPool(poolSize)
    private val semaphore = Semaphore(poolSize)

    fun submitTask(command: Runnable) {
      semaphore.acquire()
      try {
        exec.execute {
          try {
            command.run()
          } finally {
            semaphore.release()
          }
        }
      } catch (e: Exception) {
        semaphore.release()
      }
    }

    fun shutdown() {
      println("shutdown")
      while (semaphore.availablePermits() != poolSize) {
        Thread.sleep(100)
        println("wait shutdown, active threads [${poolSize - semaphore.availablePermits()}]")
      }
      println("exec.shutdown")
      exec.shutdown()
    }
  }
}
```


