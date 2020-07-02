### 기본 사용
각 상수는 객체이며 콤마로 구분

```kotlin
enum class Direction {
	NORTH, SOUTH, WEST, EAST
}
```

### 초기화
```kotlin
enum class Type(val t: Int) {
	A(1),
	B(2),
	C(3)
}
```

### 익명 클래스
```kotlin
enum class State {
	WAITING {
		override fun getState() = 0
	},
	READY {
		override fun getState() = 1
	}
	abstract fun getState(): Int
}
```

### enum 상수 사용
- valueOf()는 지정한 이름에 해당하는 enum 상수가 존재하지 않으면 IllegalArnumentException을 발생시킨다.
- EnumClass.valueOf(value: String): EnumClass
- EnumClass.values(): Array<EnumClass>

```kotlin
enum class Type(val t: Int) {
	A(1), B(2), C(3)
}
val e = Type.valueOf("A") // = enumValueOf<Type>("A") --> enum A
val es = Type.values() // = enumValues<Type>() --> enum A, B, C
es.forEach {
	println(it)
}
```

### 이름과 위치 제공 property

- 모든 enum에는 이름과 순서 property가 존재
  - val name: String
  - val ordinal: Int
