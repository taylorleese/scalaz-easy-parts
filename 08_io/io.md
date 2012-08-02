!SLIDE
# IO

    @@@ scala
    import scalaz.effects._

!SLIDE
# Using IO

    @@@ scala
    scala> val x = io { println("hi") }
    x: scalaz.effects.IO[Unit] = 
     scalaz.effects.IO$$anon$2@650908b5

    scala> x.unsafePerformIO()
    hi

!SLIDE
# IO happens when you call...

    @@@ scala
    unsafePerformIO()

!SLIDE
# IO is Composable
## map and flatMap work as expected.

    @@@ scala
    scala> val x = for {
      |   _ <- io { println("hi") }
      |   _ <- io { println("there") }
      | } yield ()
    x: scalaz.effects.IO[Unit] = 
      scalaz.effects.IO$$anon$2@4f675ff4

    scala> x.unsafePerformIO()
    hi
    there
    
!SLIDE
# except
## Handle exceptions gracefully.

    @@@ scala
    val x = io { 
      throw new Exception("fail"); () 
    }
    x.except { e => io { 
      println(e.getMessage) 
    }}

    scala> x.unsafePerformIO()
    java.lang.Exception: fail
