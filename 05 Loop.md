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

// 조건식
for (i in 1..100) { //... } // 100까지 포함
for (i in 1 until 100) { //... } // 100은 포함되지 않음
for (x in 2..10 step 2) { //... } //2씩 증가
for (x in 10 downTo 1) { //... }//숫자 감소

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
