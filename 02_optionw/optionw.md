!SLIDE
# OptionW

!SLIDE
# Have you written this? 
## It's not very typesafe.

    @@@ scala
    val x: Option[T] = ...
    val y = x match {
      case Some(s) => ...
      case None => ...
    }

!SLIDE
# some/none
## A more typesafe match.

    @@@ scala
    val x: Option[T] = ...
    val y: A = {
      x some { 
        // s: T => A 
      } none { 
        // n: => A
      }
    } 

!SLIDE
# fold
## Another more typesafe match.

    @@@ scala
    val x: Option[T] = ...
    val y: A = x.fold(
      some = s => { ... }, // s: T => A
      none = { ... } // n: => A
    )

!SLIDE
# ifNone
## The opposite of foreach.

    @@@ scala
    val x: Option[T] = ...
    x ifNone { ... }

!SLIDE
# |
## A better getOrElse.

    @@@ scala
    val x: Option[T] = ...
    val y: T = x | { ... }
    
## Defined as...

    @@@ scala
    def |(a: => A): A = value getOrElse a

!SLIDE 
# .some and none[T]

    @@@ scala
    val x = "foo".some
    val x = none[String]
    val x: Option[String] = none
