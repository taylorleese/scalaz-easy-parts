!SLIDE
# Validation

!SLIDE
# Do you write code like this?
## Compiler can't enforce type safety on errors.

    @@@ scala
    try {
      methodCouldThrow()
    } catch {
      case e => ...
    }

!SLIDE
# WTF is Validation?
## Success => right side, Failure => left side

    @@@ scala
    class Success[E, A](a: A) 
      extends Validation[E, A]

    class Failure[E, A](e: E) 
      extends Validation[E, A]

!SLIDE
# Using Validation
## More type safety and defined error conditions.

    @@@ scala
    def mayThrow(): T = ...
    val r: Validation[Throwable, T] = try {
      mayThrow().success
    } catch {
      case e => e.fail
    }

!SLIDE
# map
## If Success then Success(f(a)) else Failure.

    @@@ scala
    def f(a: A): B = ...
    val r: Validation[E, A] = ...
    val x: Validation[E, B] = r.map { f(_) }

!SLIDE
# flatMap
## If Succces then f(a) else Failure.

    @@@ scala
    def f(a: A): Validation[E, B] = ...
    val r: Validation[E, A] = ...
    val x: Validation[E, B] = {
      r.flatMap { f(_) }
    }

!SLIDE
# fold

    @@@ scala
    val r: Validation[Throwable, A] = ...
    val x: X = r.fold(
      success = s => { ... },
      failure = f => { ... }
    )

!SLIDE
# toOption

    @@@ scala
    val r: Validation[E, A] = ..
    val x: Option[A] = r.toOption

!SLIDE
# ValidationNEL
## Use it to accumulate errors.

    @@@ scala
    type ValidationNEL[E, X] = 
      Validation[NonEmptyList[E], X]


