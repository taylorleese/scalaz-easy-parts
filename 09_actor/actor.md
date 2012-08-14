!SLIDE
# Actor

    @@@ scala
    import scalaz.concurrent._

!SLIDE
# Create an actor

    @@@ scala
    def doAction(f: () => Unit) { f() }
    val a: Actor[() => Unit] = actor(doAction)

!SLIDE
# Actors are async
## Fire and forget.

    @@@ scala
    val a: Actor[() => Unit] = ...
    def f(): Unit = ...
    a { () => f() }   // using apply
    a ! { () => f() } // using !

.notes actors don't return anything
