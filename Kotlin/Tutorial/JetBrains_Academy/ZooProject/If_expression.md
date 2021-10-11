# Theory: If expression

조건문(짧게 if 문이라고 말함)은 프로그램에서 결과값(boolean) 에 따라서 다르게 행동하는 것을 문장을 말합니다. 만약 결과값이 true인 경우 프로그램은 A라는 동작을 수행하고 결과값이 false인 경우 B라는 동작을 수행하는 것을 말합니다. 'a > b' , ' i - j == 1' 과 같은 연산문들이 boolean 결과값을 돌려주는 연산입니다.

## The single if-case

키워드 if문이 들어간 조건문은 결과값이 boolean(이하 조건)과 중괄호로 묶여진 수행문으로 구성됩니다.

```kotlin
if (expression) {
    // body
}
```

만약 expression이 true인 경우 if의 구성인 수행문이 수행됩니다.  만약 false라면 수행문은 생략됩니다.

예를 들어 아래의 코드에서 "Very exprerienced person"의 문장을 출력하고 싶다면 age는 100 초과의 값이 할당되어야 할것입니다.

```kotlin
val age = ...
if (age > 100) {
    println("Very experienced person" )
}
```

만약 100 이하의 값이 age에 할당된다면 출력은 이루어지지 않고 이후의 코드가 실행됩니다.

조건이 false가 된다면 if문 구조의 수행문은 실행되지 않습니다.

```kotlin
if (3 == 4) {
    println("3 is 4")
}
```

조건인 3 == 4인 false이기 떄문에 수행문은 생략됩니다.

가끔 조건문의 조건에서 변수 하나만 있는 것을 본적이 있을 수도 있습니다. 이는 변수 자체가 boolean 타입이기에 가능한 것 입니다. 이러한 조건 대신에 booelan 타입의 변수에 == true, == false 연산을 하여도 결과는 같습니다. (만약 boolean 타입의 변수에 == false or true를 입력하면 컴파일러가 simplify를 권장합니다.)

```kotlin
val b = ...
if (b) {
    // do something
}
```

이러한 조건문은 프로그램 어디에서나 사용할 수 있으며 심지어 if문 안에 if를 넣을 수 도 있습니다.

## The if-else-cases

위에서 본 if문은 완전체가 아닙니다. else를 이용해 조건문이 false인 경우에도 수행문을 등록할 수 있습니다.

```kotlin
if (expression) { 
    // do somthing
} else {
    // do something else
}
```

위의 예제에서는 if문의 조건이 true인 경우 첫번째 수행문을 실행하고, false인 경우에는 else 이후에 있는 수행문을 실행하게 됩니다. 따라서 두 수행문이 함꼐 실행되는 경우는 없습니다.

그렇다면 아래의 예제를 살펴보겠습니다. 아래의 에제는 변수 num에 따라 다른 수행문이 실행됩니다. num이 짝수인지 홀수 인지에 따라서 달라지는 코드입니다.

```kotlin
val num = ...

if (num % 2 == 0){
    println("It's an even number")
} else {
    println("It's an odd number")
}
```

num은 짝수 또는 홀수가 되기에 한개의 수행문만 실행되게 됩니다. 만약 num이 10이라면 "... even number"가 실행될 겁니다.

## The if-else-if-cases

대부분의 조건문은 다수의 else 분기가 존재합니다

```kotlin
if (expression0) {
    // do something
} else if (expression1) {
    // do somthing esle 1

// ...

} else if (expressionN) {
    // do somethin else N
}
```

아래의 예제는 소유금에 따라 어떠한 물픔을 사야하는지 보여주는 코드입니다.

```kotlin
val asset = ...

if (asset < 1000) {
    println("Buy a labtop")
} else if (asset < 2000) {
    println("Buy a personal computer")
} else if (asset < 100_000) {
    println("Buy a server") 
} else {
    println("Buy a data center or a quantum computer")
}
```
위의 예제는 총 4가지의 분기를 가지고 있는 if 문입니다. 만약 자산이 10000 이라면 "Buy a server" 라는 문장이 출력됩니다.


## Nested If's

위에서 잠깐 이야기 한 것처럼 if 문 안에 또다른 if문을 넣을 수 있습니다.

```kotlin
if (n % 2 == 0 ){
    if( n % 3 == 0) {
        println("The number can be divided by 6")
    } else {
        println("The number can be divided by 2")
    }
} else {
    println("The number cannot be divided by 2")
}
```

위의 코드는 먼저 2로 나눌 수 있는지에 대한 판단을 한 후 3으로 나눌 수 있는 지를 판단하는 코드입니다. 만약 그렇다면 6으로 나눌 수 있음을 뜻합니다.

## Condition is an expression

다른 언어들과는 다르게 코틀린에서는 if문을 statement가 아닌 expression으로 쓰입니다. 일반적인 expression의 경우 어떠한 값은 연산해 리턴해줍니다. 따라서 다음과 같이 사용한다면 if 문에 return할 값을 넣어주어야 합니다.

```kotlin
val max = if (a > b) {
    println("Choose a")
    a
} else {
    println("Choose b")
    b
}
```

위의 코드를 실행한다면 max는 a 또는 b의 값이 할당되고 비교문을 수행 할 때에 출력이 조건에 맞게 출력됩니다.

위의 긴 문장을 아래와 같이 짧게 사용할 수도 있습니다.

```kotlin
val max = if (a > b) a else b
```

가끔 결과값을 저장할 필요가 없을 떄가 있습니다. 그런 경우 아래와 같이도 사용할 수 있습니다.

```kotlin
fun main() {
    val a = readLine()!!.toInt()
    val b = readLine()!!.toInt()

    println(if (a == b) {
        "a equal b"
    } else if (a > b) {
        "a is greater than b"
    } else {
        "b is greater than a"
    })
}
```

## Conclusion

오늘 이야기한 것들을 다시 한번 복기 해봅시다. 우리는 이번에 if문을 배웠습니다. if문은 조건 수행문으로 이루어지며 else if else를 이용해 분기문을 만들 수도 있었습니다. if 문은 if문 안에도 위치할 수 있었습니다. 그리고 kotlin은 if문에 return값을 주어 값을 바로 할당도 가능했었습니다.