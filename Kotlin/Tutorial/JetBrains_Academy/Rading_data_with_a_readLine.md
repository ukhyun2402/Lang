#Theory: Reading data with a readLine

이번에는 사용자의 인풋을 읽는 방법과 이를 활용해 어떻게 상호작용하는지 알아보겠습니다.
사용자와 상호작용하는 것은 꽤나 자주 이루어집니다. 우리는 이러한 상호작용에 대해서 readLine()함수를 이용해 어떻게 상호작용하는지 알아 보게 될것입니다.

## 1. Standard input
Standard input은 스트림 데이터를 프로그램으로 보내는 것을 말합니다. 이러한 스트림은 운영체제를 통해 이루어집니다. 일반적으로는 Standard input은 키보드로 부터 얻게되지만 파일로부터 얻어지는 경우도 있습니다.

모든 프로그램이 standard input을 요하는 것은 아니지만, 이를 배우게 된다면 다양한 곳에서 자주 활용하게 될 겁니다. 특히 알고리즘 문제에서 다음의 순서로 활용하게 됩니다.

- Standard input으로 부터 데이터 읽기
- 데이터를 처리하여 원하는 결과 얻기
- Standard output을 활용해 결과를 출력

시작하기 전에 데이터를 읽고 출력하는 것에 대한 이해를 돕기 위해 간단한 프로그램을 작성하고자 합니다.

## 2. Using readLine
크틀린에서는 <function>readLine()</function>함수를 이용해 데이터를 읽을 수 있습니다. 이 함수는 모든 것을 String 타입으로 처리합니다.
```kotlin
val line = readLine()!!
```
코드 블락에 있는 line 변수는 String 타입이 됩니다. 그 이유는 <function>readLine()!!</function> 함수는 String을 반환하기 때문입니다.

> 아마도 !! 마크에 대해서 혼동스러울 수 있습니다. !! 이 마크가 의미하는 바는 컴파일러에게 non-empty임을 선언하는 것입니다. 이에 대해서는 후에 더 자세히 이야기 하겠습니다.

여기 standard input과 standart output 이용하는 간단한 프로그램이 있습니다.
```kotlin
fun main() {
	val line = readLine()!!
    println(line)
}
```
아래의 문장을 인풋으로 한다면
> Hello, Kotlin

아웃풋은 다음과 같게됩니다.
> Hello, Kotlin 

일반적으로 위의 과정을 위해서는 Enter를 눌러야 작동하게됩니다.

## 3. toInt() and toLong()
 때때로 숫자로 이루어진 데이터가 필요할 때도 있습니다. 예를 들어, 사용자의 졸업연도와 나이가 필요하다고 가정해봅시다. 숫자 데이터를 활용하고 싶다면 <function>toInt()</function> 함수를 사용해야 합니다. Standard input을 이용한다면 반환타입이 String이기에 <function>toInt()</function>를 사용해야합니다.

```kotlin
println("Print any number: ")
val number = readLine()!!.toInt()
print("You printed the number : ")
print(number)
```
아래와 같이 인풋을 넣는다면
```kotlin
56
```
결과는 다음과 같게됩니다.
```shell
print any number:
56
you printed the number: 56 
```
아래의 경우는 큰 수를 다룰때입니다. 예를 들어 비싼 요트의 금액이라 해봅시다. 이때는 <function>toLong()</function>을 사용합니다
```kotlin
println("How much is your tacht worth?")
val cost = readLine()!!.toLong()
print("you printed: ")
print(cost)
```
결과는 다음과 같을 겁니다
```shell
Print any double type number:
0.5673421
You printed the number: 0.5673421
```
만약 Boolean타입을 사용한다면 다음과 같이 <function>toBoolean()</function>을 사용합니다
```kotlin
println("The earth is flat. Print true or false:")
val answer = readLine()!!.toBoolean()
print("The earth is flat: ")
print(answer)
```
결과는 지구는 둥그니까 false가 될겁니다.
```shell
The earth is flat. Print true or false:
false
The earth is flat: false
```

## 5. Multiple inputs
여러개의 인풋역시도 받을 수 있을까요? 정답은 그렇다 입니다. 이를 위해서는 각각의 인풋에 대해서 변수를 선언해주어야 합니다. <function>readLine()!!</function>함수와 함께말입니다. 만약 여러개의 변수에 각각 다른 데이터 타입을 넣고 싶다면 위에서 사용한 캐스팅 함수를 사용하여 원하는 타입으로 변경할 수 있습니다.
```kotlin
val a = readLine()!! // String
val b = readLine()!!.toInt() // Int
val c = readLine()!! // String
print(a)
print(" ")
print(b)
print(" ")
print(c)
```
예시와 같은 순서대로 String 타입과 Int타입을 넣는다면
```shell
You earned
100
points!
```
결과는 다음과 같습니다
```shell
You earned 100 points!
```
이처럼 여러개의 입력변수에 다른 데이터 타입을 적용하는 것은 어렵지 않습니다. 그냥 인풋 갯수에 맞게끔 변수를 선언해주고 <function>readLine()!!</function>함수를 불러오면 됩니다. 그리고는 타입을 변경하거나 출력할 수 있습니다.

## 6. Reading multiple values in one line
이때까지 우리는 줄 단위로 입력을 받아왔습니다. 만약 한 줄에 여러개의 데이터가 있는 경우는 어떻게 할까요?
그러한 경우 다음과 같이 합니다.
```kotlin
val (a, b) = readLine()!!.split(delimiters = " ") // delimiters 생략가능
println(a)
println(b)
```
예시 입력데이터는 다음과 같습니다.
```shell
Hello, Kotlin
```
그렇다면 출력은 다음과 같이 됩니다.
```shell
Hello,
Kotlin
```

```val (a, b)```이 구문은 입력데이터로 들어온 데이터를 공백을 기준으로 짤라 변수 a와 b에 넣는 작업을 합니다. 이에 대해서는 이후에 더욱 자세하게 알아보겠습니다.

같은 방법으로 한줄에 다섯개의 데이터 역시도 읽을 수 있습니다.
```kotlin
val (a, b, c, d) = readLine()!!.split(" ")
println(a)
println(b)
println(c)
println(d)
```

예시 입력데이터는 다음과 같습니다.
```shell
Have a nice Kotlin
```
그렇다면 출력은 다음과 같습니다.
```shell
Have
a
nice
Kotlin
```

## 7. Conclusion
보면 알 수 있듯이 입력데이터를 받는 것은 매우 쉽습니다. 변수를 선언하고 ```readLine()``함수를 이용해 값을 할당해주면 됩니다. ```readLine()```함수는 자동으로 입력데이터를 String 타입으로 변환시켜줍니다. 이를 활용해 사용자는 타입 캐스팅 (type Conversion)을 이용해 string, number, boolean 타입을 사용할 수 있습니다.