- list.filter
```kotlin
val p = list.filter { x -> x > 0 }
val p = list.filter { it > 0 }
```

- map list
```kotlin
for ((k, v) in map) {
    println("$k : $v")
}
```

- map 선언
```kotlin
val map = mapOf("one" to 1, "two" to 2)
val map = mapOf(Pair("one", 1), Pair("two", 2))
map["key"] = v
```

- lazy 지연
```kotlin
val p: String by lazy {
    // 문자열
}
```

- 확장함수
```kotlin
fun String.toMyString() {
    ...
}
"a".toMyString()
```

- Singleton
```kotlin
object MySingleton {
    val name = "name"
}
```

- elvis
```kotlin
// null 인 경우 실행
val files = File("test").listFiles()
print(files?.size ?: "empty")
```

- let
```kotlin
// null 이 아닌 경우 실행
val data = ...
data?.let {
    // data 가 null이 아닌 경우 실행
}
```

- let + elvis
```kotlin
val data = ...
val mapped = data?.let { ... } ?: defaultValue
```
 
- when return
```kotlin
fun test(msg: String): Int {
    return when(msg) {
        "1" -> 1
        "2" -> 2
        else -> throw IllegalArgumentException("...")
    }
}
```

- 'if' 대입 식
```kotlin
val result = if (p == 1) {
        "1"
    } else if (p == 2) {
        "2"
    } else {
        "many"
    }
```

- 단일식 함수
```kotlin
func result() = 0
```

- 람다 식
```kotlin
// 중괄호 앞위 공백,
// 파라미터와 body 구분을 위해 -> 사용
list.filter { it > 10 }.map { element -> emelent * 2 }
```
