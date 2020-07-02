![범위 지정 함수](https://github.com/diveallin/kotlin/blob/master/kv_range.png)

### apply
```swift
val peter = Person().apply {
	// this = Person()
    // apply 의 블록 에서는 오직 프로퍼티 만 사용합니다!
    name = "Peter"
    age = 18
}
```

### also
```swift
class author {
	val author = author().also {
		// it = Person()
		requireNotNull(it.age)
		print(it.name)
	}
}
```

### let
```swift
// 지정된 값이 null이 아닌 경우 실행해야 하는 경우
getNullable()?.let {
	// null 이 아닌 경우만 실행
}
```

### with
```swift
// Non null 인 경우만 사용
val person: Person = getPerson()
with(person) {
	print(name) // person.name
}
```

### run
```swift
// 
fun printPage(person: Person) = person.run {
	println(person.name)
}
```

- let?, 반환 결과, 코드 블럭 수신 객체 형식 외 다른 점이 별로 없다.
