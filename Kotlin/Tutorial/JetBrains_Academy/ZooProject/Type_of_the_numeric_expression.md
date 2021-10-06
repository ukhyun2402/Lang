#Theory: Type of the numeric expression

우리는 이미 타입 캐스팅(type conversion)을 경험해 보았습니다. 이번에는 이러한 지식을 좀 더 강화할 수 있도록 해보겠습니다. 예를 들어 Int 타입을 Long타입으로 캐스팅할 수 없는 것을 알고 있습니다. 그렇다면 Int 와 Long을 더하면 어떤 일을 생기게 될까요? 이 경우에는 구문에서 데이터 형식의 추론이 발생합니다.

## 1. Type coercion (타입 강제)
위와 같이 Int 와 Long을 더하게 되면 자동으로 더 넓은 데이터 형식으로 강제됩니다. 아래의 그림은 이를 설명하고 있습니다.
![type_coercion_image](E:\UKHYUN\Kotlin\ZooProject\Tran\type_coercion.png)
연산의 결과가 이전 타입보다 더 큰 타입이 되기 때문에 데이터가 손실될 걱정은 없습니다.

> 코틀린에서 Type coercion은 매우 희귀합니다. String과 Number에서만 일어납니다.

## 2. Example
이 이론을 예제와 함께 좀 더 명확하게 알아봅시다

- from Int to Long
```kotlin
val num: Int = 100
val longNum: Long = 1000
val result = num + longNum // 1100, Long
```
```result```를 보면 알 수 있듯이 1100이 됩니다. 이는 Long과 Int가 합쳐진 것이며 타입은 더 넓은 데이터 형식인 Long입니다. 만야 result를 Int로 선언하였다면 위의 예제는 에러를 발생시킵니다. 왜냐하면 Long타입은 Int타입에 할당할 수 없기떄문입니다.

- from Long to Double
```kotlin
val bigNum: Long = 100000
val doubleNum: Double = 0.0
val bigFraction = bigNum - doubleNum // 100000.0 Double
```

## 3. Short and Byte types
연산의 결과를 보면 알 수 있듯이 데이터 형식의 차이는 더 넓은 형식으로 변경됩니다. 하지만 Byte 와 Short는 일반적이지 않습니다. 이러한 타입의 연산은 Int로 반환됨을 명심해야 합니다.

- Byte and Byte
```kotlin
val one: Byte = 1
val two: Byte = 2
val three = one + two // 3, Int
```
- Short and Short
```kotlin
val fourteen: Short = 14
val ten: Short = 10
val four = fourteen - ten // 4, Int
```
- Short and Byte
```kotlin
val hundred: Short = 100
val five: Byte = 5
val zero = hundred % five // 0, Int
```

그렇다면 Byte 결과를 얻으려면 어떻게 해야할까요? toInt()함수와 같은 캐스팅 함수를 써야 합니다.
```kotlin
val one: Byte = 1
val five: Byte = 5
val six = (one + five).toByte() // 6, Byte
```

## 4. Summary
다른 데이터 타입의 연산은 다음과 같은 규칙을 숙지해야합니다.
1. ```Double```이 연산자에 있다면 ```Double```
2. ```Float```가 연산자에 있다면 ```Float```
3. ```Long```이 연산자에 있다면 ```Long```
4. 그렇지 않다면 모든 연산은 ```Int```가 됩니다.

> Type coercion 값 할당에는 발생하지 않습니다. 예들들어 ```val longValue: Long = 10.toInt()```는 잘못된 구문입니다. 그 이유는 10은 Int이고 longValue에는 Long타입을 할당할 수 있기 때문입니다. 

## 5. Conclusion
컴파일러는 연산의 타입을 추론합니다. 이는 간단한 경우에 타입 캐스팅을 생략하도록 돕게됩니다. 하지만 이를 이해하는 것이 에러나 혼동을 방지하는데에 큰 도움이 될 것입니다.