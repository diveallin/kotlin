### 클래스 생성자
- 클래스 선언
```kotlin
class Test {
}
// 내용이 없다면 {} 생략 가능 
class Test
```

- 기본 생성자 (primary 생성자)
  - class 이름 뒤에 선언
```kotlin
class Test public @Inject constructor(name: String) {
}

// 접근자와 annotation 정보가 없다면 constructor 문구 삭제 가능 
class Test(name: String) {
  // parameter 접근 가능
  val u = name.toUpperCase()
  
  // 기본 생성자의 경우 init {}에서 초기화
  init {
    // Do
  }
}
```

  - 클래스 선언 시 생성자와 프로퍼티 선언 
```kotlin
class Test(val name: String, val lastName: String) {
}
```

- 보조 생성자
  - 클래스 내에서 constructor 로 선언
  - 보조 생성자는 직,간접적으로 주요 생성자를 호출해야 한다.
```kotlin  
class Test(val name: String) {
	constructor(name: String, lastName: String): this(name) {
		...
	}
}
```

### 클래스 상속
- Any (!=java.lang.Object) 를 상속
- 상속 선언
```kotlin
// open 키워드는 상속 가능을 의미. kotlin의 기본은 전부 final 이다.
open class Base(p: Int)
class Child(p: Int) : Base(p)

// 클래스 주요 생성자가 없는 경우 부모 초기화
class MyView: View {
	constructor(ctx: Context) : super(ctx)
	constructor(ctx: Context, attrs: AttributeSet): super(ctx, attrs)
}
```

- method overriding 
  - 명시적으로 open 선언이 되어 있어야 한다.
  - 당연히 final class 는 open 멤버를 가질 수 없다.
```kotlin
open class Base {
	open fun v() {}
	fun nv() {}
}
class Child: Base() {
	override fun v() {}
}
```

- property overriding 
```kotlin
open class Foo {
	open val x: Int get() {...}
}
class Bar1: Foo() {
	override val x: Int = ...
}
```

- 상위 호출
```kotlin
super.x()

// inner class 에서 outer 호출. super@Outer
class Bar: Foo() {
	override fun f() {}
	override val x: Int get() = 0

	inner class Baz {
		fun g() {
			super@Bar.f() // Foo.f()
			println(super@Bar.x) // Foo.x
		}
	}
}

// 모호함을 제거하기 위한 규칙
open class A {
	open fun f() {}
	fun a() {}
}
interface B {
	fun f()
	fun b()
}
class C: A(), B {
	override fun f() { // 반드시 상속해야 함.
		super<A>.f() // 상위 호출
		super<B>.f()
	}
}

// interface 는 모두 open 임. fun 에 open 붙일 필요 없음.
// abstract 선언 가능: class, fun
```
