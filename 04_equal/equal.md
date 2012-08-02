!SLIDE
# Equal

!SLIDE
# ===
## Typesafe equals.

    @@@ scala
    val s1: String = ...
    val s2: String = ...
    s1 === s2

!SLIDE
# /==
## Typesafe not equals.

    @@@ scala
    val s1: String = ...
    val s2: String = ...
    s1 /== s2


!SLIDE
# Define your own Equal[A]

    @@@ scala
    case class Foo (x: String)
    implicit val fooEqual: Equal[Foo] = equalA
    val f1 = new Foo("one")
    val f2 = new Foo("two")
    f1 === f2

