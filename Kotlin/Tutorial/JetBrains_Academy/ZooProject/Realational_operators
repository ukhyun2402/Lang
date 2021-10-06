# Theory: Relational operators

## List of relational opeartors
코틀린은 다음의 6가지 관계 연산자를 이용할 수 있습니다
- == - 같은지 
- != - 다른지
- \> - 큰지
- \>= - 크거나 같은지
- < - 작은지
- <= 작거나 같은지

관계연산자는 언제 Boolean(true or false)의 값을 반환합니다.


## Comparing integer numbers
관계연산자를 통하여 2개의 숫자를 비교할 수 있습니다.

```kotlin
val one = 1
val two = 2
val three = 3
val four = 4

val oneIsOne = one == one // true

val res1 = two <= three // true
val res2 = two != four // ture
val res3 = two > four // false
val res4 = one == three // false
```

관계연산자를 사용하면서 산술 연산자 역시도 사용할 수 있습니다. 이러한 표현식에서는 산술 연산자가 논리 연산자 보다 더욱 높은 우선순위를 갖습니다.

아래의 예시를 봅시다. 먼저 코틀린은 두개 더하기 연산을 먼저 실행합니다. 그리고는 > 연산자를 이용해 관계연산을 실행합니다.
```kotlin
val number = 1000
val result = number + 10 > number + 9 // true
```
위 예시의 결과는 true가 반환됩니다.

관계연산자라고 해서 모든 숫자형 타입 섞어서 연산할 수는 없습니다. Int 와 Long타입의 동위 연산(==, !=)은 할 수 없습니다. 하지만 >, <, >=, <= 연산은 사용 가능합니다. 만약 Int와 Long의 동위 연산이 필요할 경우 Int를 Long으로 변환하여 비교할 수는 있습니다.
```kotlin
val one: Long = 1
val two: Int = 0

println(one >= two)             // true
println(one == two)             // Error
println(one == two.toLong())    // false
```


## Joining relational operations
코틀린은 다음과 같은 연산은 실행할 수 없습니다
```kotlin
a <= b <= c
```
만약 위와 같은 연산을 하고싶다면 논리 연산자인 || 와 &&을 사용해 연산을 합쳐야 합니다. 
예를 들어, 아래의 연산을 코틀린에서 사용할 수 있는 연산으로 바꿔보겠습니다
```kotlin
100 < number < 200
```
위와 같은 연산이 있다면 아래와 같이 바꾸어야 합니다
```kotlin
100 < number && number < 200
```
또한 괄호를 넣어 좀 더 명확하게도 할 수 있습니다
```kotlin
(100 < number) && (number < 200)
```
관계 연산에서 괄호는 가장 높은 우선 순위를 가지지만, 이는 연산에서 꼭 넣어야 하는 것은 아닙니다.

논리 연산은 일련의 관계 연산식을 하나의 식으로 만들어줍니다. 이러한 방식은 프로그래밍 분야에서 널리 사용됩니다.

더욱 어려운 예제를 보겠습니다. 프로그램을 한번 작성해보겠습니다. 입력된 수가 있으면 일정한 범위 (여기서는 100과 200으로 하겠습니다.)에 들어있는지를 판단하는 프로그램입니다
```kotlin
fun main(){
    val left = 100
    val right = 200
    val number = readLine()!!.toInt()
    
    val inRange = left <= number && right >= number
    
    println(inRange)
}
```
## Conclusion
이번에는 유용하게 사용가능한 관계연산자에 대해서 알아보았습니다.  관계연산자와 논리연산자를 조합해 다양한 연산을 만들 수 있습니다. 하지만 명심해야 할 것이 있습니다. 연산자는 언제나 Boolean 타입의 결과만 반환합니다. 이후에는 코틀린 프로그램에 어떻게 연산자를 적용하는지 알아보겠습니다.
