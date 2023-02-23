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
