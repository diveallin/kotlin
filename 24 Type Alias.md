### Type Alias
- 타입 별칭 선언

```kotlin
// 타입 이름 짧게 변경
typealias NodeSet = Set<Network.Node>

// 함수 타입
typealias MyHandler = (Int, String, Any) -> Unit

// 내부 클래스도 가능
class A {
  inner class Inner
}
class B {
  inner class Inner 
}
typealias AInner = A.Inner
typealias BInner = B.Inner
```
