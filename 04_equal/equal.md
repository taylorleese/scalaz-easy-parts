!SLIDE
# Equal

!SLIDE
# ===
## Typesafe equals.

    @@@ scala
    val s1: String = ...
    val s2: String = ...
    val i = 1
    s1 === s2
    s1 === i // does not compile (awyeah)

!SLIDE
# /==
## Typesafe not equals.

    @@@ scala
    val s1: String = ...
    val s2: String = ...
    s1 /== s2

!SLIDE
# How does typesafe equals work?

    @@@ scala
    def equalA[A]: Equal[A] = new Equal[A] 
      with NaturalEqual {
      def equal(a1: A, a2: A) = a1 == a2
    }

.notes equalA defined in Equals
.notes === defined in Identity[A]

!SLIDE
# Define your own Equal[A]

    @@@ scala
    case class Foo (x: String)
    implicit val fooEqual: Equal[Foo] = equalA
    val f1 = new Foo("one")
    val f2 = new Foo("two")
    f1 === f2

