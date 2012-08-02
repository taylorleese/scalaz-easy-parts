!SLIDE
# NonEmptyList

!SLIDE
# Typesafe non-empty lists

    @@@ scala
    val x: NonEmptyList[String] = nel("foo")

!SLIDE
# List => NonEmptyList

    @@@ scala
    val x: List[T] = ...
    val y: Option[NonEmptyList[T]] = x.toNel
    val z: List[T] = y.list

