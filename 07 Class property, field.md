### 클래스 property
- 클래스 선언 시 property는 초기 값을 지정하거나 생성자에서 초기값을 지정해 주어야 한다.

```kotlin
var <propertyName>[: <PropertyType>] [= <property_initializer>]
	[<getter>]
	[<setter>]
```

### Property 선언
```kotlin
// setter, getter 선언
val isEmpty: Boolean
	get() = this.size == 0
var message: String 
	get() = this.toString()
	set(value) { // value 라고 이름 쓰는 것이 관용이나 다른 이름 사용 가능
		setToOther(value) // 다른 변수에 할당
	}

// setter private 선언
var setterVis: String = "abc"
	private set	// setter를 private으로 설정

// 상수는 const로
const val MESSAGE = "Hello"
```


### 클래스 property
- 코틀린 class는 field를 가질 수 없다. 
- 변수 선언 후 초기값을 할당한 후 접근자를 통해 접근하면 setter와 getter가 호출되어 할당된다. 
- field를 사용하고 싶다면 setter와 getter를 구현한 후 field 식별자를 사용한다.

```kotlin
var counter = 0 // 지원필드
	set(value) {
		field = value + 1 // field 식별자 사용. counter = value + 1을 하게되면 재귀호출이 계속일어나 overflow 에러가 발생
	}
	get() = field + 1
```

### lateinit
```kotlin
// 생성자에 포함되지 않고 setter/getter를 갖지 않을 때 var 로만 사용 가능
// non-null 이어야 하고, 기본 타입이면 안됨.
// 초기화 되기 전에 접근 시 exception을 발생 

lateinit var subject: TestSubject

// 초기화 검사
if (foo::bar.isInitialized) {
	...
}
```
