### Data class
- 데이터 보관 목적
- 최소 한 개 이상의 생성자 파라미터
- 추상, open, sealed, inner class 일 수 없다.

### Data class 사용 예)
```kotlin
data class User(val name: String, val age: Int)// parameter initdata class User(val name: String = "", val age: Int = 0)
```

### 복사
```kotlin
// 자동 생성되는 copy 함수
fun copy(name: String = this.name, age: Int = this.age) = User(name, age)

val foo = User(name = "foo", age = 1)
val copyFoo = foo.copy()

// 일부 변경 가능
val copyFoo2 = foo.copy(age = 10)
```

### 분리 선언
```kotlin
val user = User("foo", 10)
val (n, u) = user
println("$n is $u")
```
