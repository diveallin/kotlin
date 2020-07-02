### 확장 
- 클래스에 새로운 method, property 추가 가능
- package 밖에서 확장을 사용하려고 하면 확장 함수를 import 해야 한다.


### 확장 함수
```kotlin
// MutableList<Int> class 에 swap 함수 추가
// 확장 함수 내 this 는 receiver에 대응 
fun MutableList<Int>.swap(index1: Int, index2: Int) {
	val tmp = this[index1]
	this[index1] = this[index2]
	this[index2] = tmp
}

val l = mutableListOf(1, 2, 3)
l.swap(0, 2)
```
  

### Generic Type class 의 확장
```kotlin
// Generic class에서 함수 확장
fun <T> MutableList<T>.swap(index1: Int, index2: Int) {
	val tmp = this[index1]
	this[index1] = this[index2]
	this[index2] = tmp
}
```

### 확장 함수 중복
- 클래스의 멤버에 선언된 함수를 확장함수로 선언한 경우 확장함수는 호출되지 않는다. 멤버함수가 호출된다.

```kotlin
// Generic class에서 함수 확장
class C {
	fun foo() {
		println("member")
	}
}
fun C.foo() {
	println("extension")
}
C().foo() // "member" 가 출력됨.

// 인자 값이 다른 경우
fun C.foo(i: Int) {
	println("extension")
}
C().foo(1) // "extension" 이 출력됨
```

### null 가능 receiver
- 확장이 null 가능 receiver type을 가질 수 있도록 정의할 수 있다.

```kotlin
fun Any?.toString(): String {
	if (this == null) {
		return "null"
	}
}
```

### Property 확장
- 실제 클래스에 멤버를 추가하는 것이 아니기 때문에 선언 후 초기화하는 방법은 없다. 명시적으로 getter/setter  를 제공하여 정의한다.

```kotlin
val String?.test: String
	get() {
		return "Test"
	}
val s = String()
println(s.test) // "Test" 
```

### Companion object 확장
```kotlin
class MyClass {
	companion object {}
}
fun MyClass.Companion.foo() {
	println("MyClass.Companion.foo")
}
MyClass.foo()
```

### Class 내부에서 다른 클래스를 위한 확장을 선언하는 것이 가능
- dispatch receiver : 확장을 정의한 class 
- extension receiver: 확장 대상 class

```kotlin
class C {
	// D class 확장
	fun D.foo() {
		toString()	// D.toString() 호출. 이름 충돌이 있을 경우 확장 리시버가 우선되므로 D.toString이 호출
		this@C.toString()	// this 접근으로 확장 대상 선택, C.toString() 호출
	}
}
```

### 확장 함수의 상속
- dispatch receiver에서 정의한 확장 함수도 open 으로 정의하여 상속한 다른 클래스에서 재정의 가능하다.

```kotlin
open class D
class D1 : D()
open class C {
	open fun D.foo() {
		println("D.foo in C")
	}
	open fun D1.foo() {
		println("D1.foo in C")
	}
	fun caller(d: D) {
		d.foo() // 확장 함수를 호출
	}
}
class C1 : C() {
	override fun D.foo() {
		println("D.foo in C1")
	}
	override fun D1.foo() {
		println("D1.foo in C1")
	}
}
```
