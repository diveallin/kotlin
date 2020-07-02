### interface

```swift
// 추상 메소드 선언, 또는 구현을 포함시킬 수 있다.
interface InterTest {
	fun foo()
	fun bar() {
		...
	}
}
class Child: InterTest {
	override fun foo() {
		...
	}
}
```

### interface property

```swift
// interface 에 프로퍼티를 선언할 수 있다.
// 선언한 property는 초기화할 수 없으나, setter/getter 접근자를 선언하는 것은 가능.
interface MyInter {
	val prop: Int 
	val propString: String
		get() = "foo"
	fun foo() {
		print(prop)
	}
}
// 상속한 class에서 선언한 접근자를 초기화해야 한다.
// interface의 val 선언에 getter 가 있다면 상속하지 않아도 됨
class Child: MyInter {
	override val prop: Int = 29
}
```

### overriding 충돌 해결
```swift
interface A {
	fun foo() {
		println("A-foo")
	}
	fun bar()
}
interface B {
	fun foo() {
		println("B-foo")
	}
	fun bar() {
		println("B-bar")
	}
}
// A를 구현한 C 는 정의되지 않은 bar() 만 정의하면 됨
class C: A {
	override fun bar() {
		println("C-bar")
	}
}
// D는 A, B를 상속받아 foo()가 충돌되었으므로 foo() 와 bar()를 모두 정의해야 함.
class D: A, B {
	override fun foo() {
		super<A>.foo()
		super<B>.foo()
	}

	override fun bar() {
		super<B>.bar()
	}
}
```
