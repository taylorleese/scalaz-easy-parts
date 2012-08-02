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
    val y: Option[A] = {
      x some { ... } none { ... }
    } 

!SLIDE
# fold
## Another more typesafe match.

    @@@ scala
    val x: Option[T] = ...
    val y: Option[A] = x.fold(
      some = s => { ... }, 
      none = { ... }
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

!SLIDE 
# .some and none[T]

    @@@ scala
    val x: Option[String] = "foo".some
    val x: Option[String] = none[String]
