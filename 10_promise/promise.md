!SLIDE
# Promise

    @@@ scala
    import scalaz.concurrent._

!SLIDE
# Execute an expression async 
## 

    @@@ scala
    def f(): T = ...
    val x: Promise[T] = promise { f() }
    val y: T = x.get // block until finished

.notes promise defined in Promises

!SLIDE
# Promises are composable

    @@@ scala
    val x: Promise[Int] = promise { 1 }
    val y: Promise[Int] = x.map { _ + 1 }
    val z: Int = y.get // z = 2

!SLIDE
# Using to
## Don't block.

    @@@ scala
    def f(): T = ...
    def handleResult(r: T): Unit = ...
    promise { f() } to { handleResult(_) }
