!SLIDE
# Zero

!SLIDE
# ~
## Unary not with primitive types.

    @@@ scala
    val w: Option[Boolean] = ...
    val x: Boolean = ~w // w | false
    val y: Option[String] = ...
    val z: String = ~y // y | ""

.notes unary_~ defined in OptionW
    
!SLIDE
# Defining your own Zero[A]

    @@@ scala
    case class Foo(s: String)
    implicit val fooZero: Zero[Foo] = {
      new Zero[Foo] { 
        override val zero: Foo = Foo("")
      }
    }
    val x: Option[Foo] = none[Foo]
    val y: Foo = ~x // x | zero

