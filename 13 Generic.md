### Generic
```kotlin
class Box<T>(t: T) {
	var value = t
}
val box: Box<Int> = Box<Int>(1)

// 파라미터가 추론 가능하면 타입을 생략할 수 있다.
val box = Box(1)
```


### 선언 위치 변성 class 선언 시 generic에 In/Out 설정
```kotlin
// Out 소비하지 않고 리턴만 할 때 사용
abstract class Source<out T> {
	abstract fun getSource(): T
}
fun demo(strs: Source<String>) {
	val objects: Source<Any> = strs
}

// In 소비만 하고 생산은 할 수 없을 때
abstract class Comparable<in T> {
	abstract fun compareTo(other: T): Int
}
fun demo(x: Comparable<Number>) {
	x.compareTo(1.0)
	val y: Comparable<Double> = x
}
```

### 사용 위치 변경 
out, int 한 가지만으로 클래스 선언 시 generic 선언을 할 수 없는 경우

```kotlin
// In/Out 을 함수에 선언
fun copy(from: Array<out Any>, to: Array<Any>) { 
	// ...
}
fun fill(dest: Array<in String>, value: String) { 
	// ...
}
```

### 스타 프로젝션(Star projection)
- Foo<out T> 으로 공변일 때 Foo<*> :  T 의 상위 클래스로 안전하게 값을 읽을 수 있다는 것을 의미
- Foo<in T> 으로 반공변일 때 Foo<*> : T를 알 수 없을 때 안전하게 쓸 수 없다는 것을 의미
