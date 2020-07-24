### Exception
- 모든 Exception 클래스는 Throwable을 상속
- throw 하려면 throw ExceptionClass()를 사용

```kotlin
try {
}
catch (e: ExceptionClass) {
}
finally {
}
```

- try는 식이어서 리턴 가능
```kotlin
val a: Int? = try { parseInt(input) } catch(e: NumberFormatException) { null }
```
