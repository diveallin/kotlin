### object 식

- 익명 클래스 선언

```kotlin
// 익명 클래스 선언
// 익명 클래스에서 둘러싼 범위의 변수 접근 가능. Java와 달이 final 변수로 제한 두지 않는다. 
window.addMouseListener(object : MouseAdapter() { 
	override fun mouseClicked(e: MouseEvent) {
		// ...
	}
	override fun mouseEntered(e: MouseEvent) {
		// ...
	} 
})
```

- 상속
```kotlin
// 상위 타입이 생성자를 가지면 알맞게 전달, 여러 개면 콜론 뒤에 콤마로 구분
open class A(x: Int) {
	public open val y: Int = x
}
interface B {...}
val ab: A = object : A(1), B {
	override val y = 15 
}
```

- 단순 선언
```kotlin
// 상위 타입이 없는 경우 콜론 없이 선언
fun foo() {
	val adHoc = object {
		var x: Int = 0
		var y: Int = 0 
	}
	print(adHoc.x + adHoc.y) 
}
```

- object의 반환
```kotlin
// object의 리턴은 private 에서만 내부 접근이 가능
class C {
	// private 함수이므로 리턴 타입은 익명 객체 타입이다 
	private fun foo() = object {
		val x: String = "x" 
	}
	// public 함수이므로 리턴 타입은 Any이다 
	fun publicFoo() = object {
		val x: String = "x" 
	}
	fun bar() {
		val x1 = foo().x // 동작
		val x2 = publicFoo().x // 에러: 레퍼런스'x'를 찾을 수 없음
	} 
}
```

### object 선언
- Singleton
상위 타입을 선언하는 것도 가능
```kotlin
object DataProviderManager {
	fun registerDataProvider(provider: DataProvider) {
		// ...
	}
	val allDataProviders: Collection<DataProvider>
}
DataProviderManager.registerDataProvider(...)
```

- companion object
```kotlin
// static method와 비슷
// factory method로 생성 시에도 사용 가능
class MyClass {
	companion object Factory {
		fun create(): MyClass = MyClass() 
	}
}
val instance = MyClass.create()

// 이름 생략 가능 
class MyClass { 
	companion object { 
	}
}
val x = MyClass.Companion
```

### object 식과 object 선언의 차이
- object 식은 사용한 위치에서 즉시 초기화 되고 실행.
- object 선언은 처음 접근할 때까지 초기화를 지연
- companion object는 대응하는 클래스를 로딩할 때 초기화된다. 자바의 정적 초기화와 동일
