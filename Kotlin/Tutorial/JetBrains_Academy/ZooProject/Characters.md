# Theory: Characters
이번에는 코틀린에서 어떻게 글자를 쓰는지에 대해서 알아보겠습니다. 이는 매우 기초적인 개념이며 텍스트를 이해하는데에 좀 더 도움이 될겁니다.

## What is a character
각각의 문자는 따옴표로 둘러쌓인 하나의 기호입니다. 이를 우리는 Char 타입이라고 말합니다. 
```kotlin
val lowerCaseLetter: Char = 'a'
val upperCaseLetter: Char = 'Q'
val number: Char = '1'
val space: Char = ' '
val dollar: Char = '$'
```
이 Char 타입은 상형문자와 그리고 특이한 기호 역시도 값을 담을 수 있습니다. 

하나의 문자는 16진수인 Unicode로도 값을 할당 할 수 있습니다.그때는 \u를 어두에 붙여야 합니다.

```kotlin
val ch = '\u0040' // @
println(ch)
```
이처럼 일련의 유니코드를 통해 하나의 문자를 나타낼 수 있습니다.

예를 들어 알파벳 대문자는 16진수로 \u0041 ~ \u005A까지 그리고 소문자는 \u0061 ~ \u007A에 분포해 있습니다

그리고 숫자를 문자로 변형하거나 반대로 문자를 숫자로 변형하는 것 역시도 가능합니다.
```kotlin
val ch = 'a'
println(ch.toInt()) // 97
val num = 97
println(num.toChar()) // a
```

## How to read characters
코틀린은 문자를 읽는 유용한 함수를 제공하지 않습니다. 하지만 다른 방법이 있습니다. 만약 한 줄에서 하나의 문자를 읽기를 원한다면 다음과 같이 할 수 있습니다.
```kotlin
val ch: Char = readLine()!!.first()
```
이렇게 하면 String의 문자열에서 제일 첫번째 위치한 문자를 얻을 수 있습니다. 그리고 이 얻은 문자는 Char 타입이 됩니다. String은 Char로 이루어져 있기 떄문에 가능한것입니다. 이에 대해서는 이후에 알아보겠습니다.

## Retrieving subsequent characters
+, - 연산자를 이용해 유니코드의 앞과 뒤에 위치한 문자들을 얻을 수 있씁니다.
```kotlin
val ch1 = 'b'
val ch2 = ch1 + 1 // 'c'
val ch3 = ch2 - 2 // 'a'
```
하지만 숫자에 문자를 더하는 것은 에러를 발생시킵니다.
```kotlin
val ch = 'a'
val ch1 = 1 + ch // Error
```
그리고 문자 2개를 더하는 것 역시 에러가 발생합니다.
```kotlin
val charsSum = 'a' + 'b' // Error
```

하지만 ++ -- 는 문자의 앞이든 뒤든 어디든 위치할 수 있습니다. 또한 += -=연산 역시도 가능합니다.

```kotlin
var ch = 'A'

ch += 10
println(ch) // K
println(++ch) // L
println(++ch) // M
println(--ch) // L
```

## Escape sequence
\로 시작하는 특이한 문자들이 있습니다. 보았을 수도 있겠지만 이를 escape 또는 control sequence라고 칭합니다. 아래에 나와있는 언어들은 키보드에 있지 않은 것들입니다. 아래와 같은 캐릭터들을 나타내기 위해서는 2개의 문자를 합쳐서 사용해야 합니다. 하지만 컴퓨터는 이를 하나의 문자라고 인식합니다.
- '\n' 은 새로운 줄을 만듭니다.
- '\t' 은 탭을 말합니다.
- '\r' 은 캐리지 리턴 현재줄에서 제일 앞으로 커서를 옮깁니다.
- '\\' 은 \를 나타낼때 쓰입니다.
- '\'' 은 따옴표 한개를 나타날때 쓰입니다.
- '\"' 은 쌍 따옴표를 나타낼때 쓰입니다.

예시를 보겠습니다.
```kotlin
print('\t') // makes a tab
print('a')  // prints 'a'
print('\n') // goes to a new line
print('c')  // prints 'c'
```
```shell
  a
c
```
결과는 다음과 같이 나옵니다.

## Relational operations with characters
비교연산자를 이용해 문자를 비교할 수 있습니다. 이 때는 유니코드 테이블을 기준으로 합니다.

```kotlin
println('a' < 'c') // true
println('x' >= 'z') // false

println('D' == 'D') // true
println('Q' != 'q') // true
println('A' < 'a') // true
```

이렇게 비교연산을 통해 문자가 숫자인지 아닌지도 판별할 수 있습니다. 숫자는 \u0030에서 \u0039에 있기 때문에

```kotlin
fun main() {
    val ch = readLine()!!.first()
    val isDigit = ch >= '\u0030' && ch <= '\u0039'
    
    println(isDigit)
}
```
만약 문자가 0~ 9에 속한다면 true 그렇지 않다면 false를 반환할겁니다.

## Processing characters
Char 타입에는 다양한 함수들이 있습니다.

- isDigit() 문자가 숫자일 경우 true를 반환합니다.
- isLetter() 문자가 알파벳인경우 true를 반환합니다.
- isLetterOrDigit() 문자가 알파벳 또는 숫자인 경우 true
- isWhiteSpace() 공백 또는 \t \n 인경우 true를 반환합니다.
- isUpperCase() 문자가 대문자 인경우 true
- isLowerCase() 문자가 소문자 인경우 true
- toUpperCase() 문자를 대문자로 바꾸어줍니다.  1.5 이상에서는 사용이 불가합니다.
- uppercaseChar() 문자를 대문자로 바꾸어줍니다 . 1.5이상에서 사용가능
- uppercase() 대문자로 바꾸고 String으로 반환해줍니다.
- toLowerCase() 문자를 소문자로 바꾸어줍니다. 1.5이상에서는 사용이 불가합니다.
- lowercaseChar() 문자를 소문자로 바꾸어줍니다. 1.5이상에서 사용가능
- lowercase() 문자를 소문자로 바꾸고 String으로 반환해줍니다.

예제를 보겠습니다.
```kotlin
val one = '1'

val isDigit = one.isDigit()   // true
val isLetter = one.isLetter() // false

val capital = 'A'
val small = 'e'

val isLetterOrDigit = capital.isLetterOrDigit() // true

val isUpperCase = capital.isUpperCase() // true
val isLowerCase = capital.isLowerCase() // false

val capitalEString = small.uppercase() // "E"
val capitalE = small.uppercaseChar()   // 'E'
```
더 자세히는 다음에 알아보겠습니다.

## Conclusion
이번에는 Char타입, Escape문자와 연산자 그리고 함수들 그리고 유니코드까지 알아보았습니다. 그럼 이제 연습시간입니다!