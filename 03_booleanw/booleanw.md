!SLIDE
# BooleanW

!SLIDE
# option
## If true Some else None.

    @@@ scala
    def f(): A = ...
    val x: Boolean = ...
    val y: Option[A] = x.option(f)

!SLIDE
# when
## If true then do f().
  
    @@@ scala
    def f(): Unit = ...
    val x: Boolean = ...
    x.when(f)

!SLIDE
# unless
## If false then do f().

    @@@ scala
    def f(): Unit = ...
    val x: Boolean = ...
    x.unless(f)

!SLIDE
# fold
## A typesafe if/else.

    @@@ scala
    val x: Boolean = ...
    val y: A = x.fold(
      a = { ... }, // if true, a: => A
      b = { ... }  // if false, b: => A
    }

