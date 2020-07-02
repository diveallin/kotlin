### for 

```kotlin
// iterator
for (item: Int in ints) { // ...
}

// index를 통한 접근 
for (i in array.indices) { 
	print(array[i])
}

// index와 값
for ((index, value) in array.withIndex()) { 
	println("the element at $index is $value")
}
```

### break, continue 사용 가능

### label
```kotlin
// label을 통한 break
loop@ for (i in 1..100) { 
	for (j in 1..100) {
		if (...) break@loop
	}
}
```
