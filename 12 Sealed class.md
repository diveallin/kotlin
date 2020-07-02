### sealed class
값이 제한된 타입 집합 중 하나를 가질 수 있지만 다른 타입은 가질 수 없을 때, 클래스 제한을 표현하기 위해 sealed class 를 사용한다. enum 과 용도가 비슷

### 사용 예
```kotlin
sealed class Expr
data class Const(val number: Double) : Expr()
data class Sum(val e1: Expr, val e2: Expr) : Expr() 
object NotANumber : Expr()

fun eval(expr: Expr): Double = when(expr) { 
	is Const -> expr.number
	is Sum -> eval(expr.e1) + eval(expr.e2) 
	NotANumber -> Double.NaN
	// 모든 경우를 다루므로 `else` 절이 필요 없다 
}
```
