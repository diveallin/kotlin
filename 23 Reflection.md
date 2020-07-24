### Class 레퍼런스
| Java | Kotlin | 의미 | 
|---|---|---|
| SomeClass.class | SomeClass::class | 클래스 그 자체를 리플렉션 |
| someInstance.getClass() | someInstance::class | 인스턴스에서 클래스를 리플렉션 |

### function 레퍼런스
- 함수를 값으로 다른 함수에 전달 가능
- 함수앞에 "::" 를 붙인다.

```kotlin
fun isOdd(x: Int) = x % 2 != 0
val numbers = listOf(1, 2, 3)
println(number.filter(::isOdd)
```

### Property 참조
- property 접근 시에도 :: 사용

```kotlin
val x = 1
fun main() {
  println(::X.get()) // "1"
  println(::x.name)  // "x"
}
```
