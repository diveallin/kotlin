### 가시성 접근자 visibility (access) modifier 
- class, object, interface, constructor, property, property setter 는 가시성 접근자를 가질 수 있다.
- 코틀린에서 외부 class는 내부 class의 private을 볼 수 없다.
- private, protected, internal, public (default)  
  - private : 클래스 안에서만 접근 가능  
  - protected: 자신과 하위 클래스 내에서 접근 가능  
  - internal: 모듈 내에서 접근 가능  
  - public: 모든 접근 가능

```kotlin
open class Outer {
	private val a = 1
	protected open val b = 2 
	internal val c = 3
	val d = 4 // 기본으로 public
	protected class Nested { 
		public val e: Int = 5
	} 
}
class Subclass : Outer() { 
	// a는 접근 불가
	// b,c,d는 접근 가능
	// Nested와 e는 접근 가능
	override val b = 5 // 'b'는 protected
}
class Unrelated(o: Outer) {
	// o.a, o.b는 접근 불가
	// o.c 와 o.d는 접근 가능(같은 모듈)
	// Outer.Nested는 접근 불가며, Nested::e 역시 접근 불가
}
```

