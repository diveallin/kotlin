### Boxing 
- Value type의 값을 reference type 으로 변환 하는 경우. (스택에 있던 데이터가 힙으로 복사)

```kotlin
val a: Int = 1
val aRef: Int? = a
```

### Unboxing
- Reference type 의 값을 value type으로 변환 하는 경우. (힙에 있는 데이터가 스택으로 복사)

```kotlin
val aRef: Int? = 100
val a: Int = aRef ?: 0
```

### 비교 (==, ===)
```kotlin
// "===" -> java의 == 와 같다.
// "==" -> primitive type의 경우는 값 비교, object 의 경우 java의 equals와 같다.

// Long 의 경우 equal은 비교대상이 Long 인지 확인한다.
val t1 = 1
val t2 = 1L
println(t1 == t2) // 컴파일 에러
println(t1 === t2) // 컴파일 에러
```

### 숫자의 형 변환
- toByte(): Byte
- toShort(): Short
- toInt(): Int

- toLong(): Long
- toFloat(): Float 
- toDouble(): Double 
- toChar(): Char

### 쉬프트 연산
- shl(bits) ­ 부호있는 왼쪽 시프트 (자바의 << )
- shr(bits) ­ 부호있는 오른쪽 시프트 (자바의 >> )
- ushr(bits) ­ 부호없는 오른쪽 시프트 (자바의 >>> )
- and(bits)
- or(bits)
- xor(bits)
- inv() ­비트역

### """ """
raw 문자열을 만들 수 있다. .trimIntent()를 사용하여 공백을 제거 할 수 있다.
