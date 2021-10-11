# Theory: String templates

프로램을 작성하다보면 문자열을 할당해야 할 때가 있습니다. 코틀린은 이러한 당신의 요구를 채워주는 언어입니다!. 정말로 그러한지 이번 토픽에는 String과 관련된 것을 알아보겠습니다.

우리는 오늘의 온도를 나타낼 메시지를 보여주어야 한다고 가정해보겠습니다.

```text
Now, the temperature in ... is ... degrees Celsius.
```

... 에는 도시와 온도를 보여줄 예정입니다. 그러기 위해서는 두 변수 city와 temp가 필요할 겁니다.

```kotlin
val city = "Paris"
val temp = 24

println("Now, the temperature in " + city + " is " + temp + " degrees Celsisu")
```

위의 예제를 이용해 할 수 있습니다. 하지만 완벽? 아닙니다. 이 예제는 뭔가 어색합니다.

코틀린은 문자열을 출력할 때 좀 더 편리한 기능을 제공하고 있습니다. 그럼 그 기능을 어떻게 사용하는지 알아보겠습니다. string문자열 안에 $와 변수이름을 붙여주면 됩니다.

```kotlin
val city = "Paris"
val temp = 24

println("Now, the temperatures in $city is $temp degrees Celsius")
```

위의 코드를 비교해보면 좀 더 가독성있는 코드가 되었습니다. 물론 출력 결과는 같습니다.

만약 string을 출력하고 싶지 않다면 다음과 같이도 사용할 수 있습니다.

```kotlin
val value = "55"
val currency = "dollars"
val price = "$value $currency"
```

이러한 string 템플릿을 이용해 변수를 할당 출력하는 것을 권장힙니다. 이를 이용해 String을 연결하는 것도 시도해 보세요.

## Templates for expressions

{} 중괄호를 이용하다면 template에 단순 변수뿐만 아니라 연산도 넣을 수 있습니다.

```kotlin
val language = "Kotlin"
prinln("$language has ${language.length} letters in the name")
```

```text
Kotlin has 6 letters in the name
```

이라고 출력될겁니다. 여기서 {languate.length}는 연산되어 값이 할당됩니다. 만약 {} 중괄호를 없앤다면 다음과 같이 출력됩니다.

```text
Kotlin has Kotlin.length letters in the name
```

그렇기에 중괄호를 꼭 사용해 위와 같은 오류는 피해야 합니다. 그리고 만약 변수만 넣는다면 작동하기는 하지만 이러한 방법은 피해야 합니다.

## Conclusion

이번에 기억해야 할 것은 무엇일까요?

- string에 변수값을 함께 출력하기. "this string has $value"
- 만약  연산이 필요한 식을 넣을 경우엔 {} 중괄호를 써야한다.
