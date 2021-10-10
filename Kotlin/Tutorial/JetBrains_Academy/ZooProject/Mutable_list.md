# Theory: Mutable list

이전에 우리는 변수의 선언과 값 할당 그리고 할당된 값을 수정하는 것을 배웠습니다. 그렇다면 이러한 의문이 들 수 있습니다. 같은 타입의 변수는 모두 따로 변수를 선언해줘야 하나?라고요. 이러한 경우에 사용할 수
있는 것이 바로 list입니다. 이 list는 하나의 변수에 같은 타입의 값들을 저장할 수 있는 객체입니다. 그래서 이번에 우리는 MutableList에 대해서 어떻게 사용하는지에 대해 배우게 될것입니다.

## Introduction to MutableList

코틀린에서 기본적으로 데이터를 하나로 묶는 다양한 방법이 있지만 이번엔 그 중에서 Mutable List라는 것을 배워보겠습니다.

MutableList는 같은 타입의 값들을 일련의 순서대로 저장하는 타입입니다. 이 저장된 값들은 인덱스를 이용해 접근할 수 있습니다.

```kotlin
val numbers = mutableListOf(10.8, 14.3, 13.5, 12.1, 9.7)
println(numbers) // [10.8, 14.3, 13.5, 12.1, 9.7]
```
아래의 그림을 보면 5개의 유리수가 있는 것을 볼 수 있습니다.각각의 값들은 인덱스를 가지며 이 인덱스를 이용해 값들에 접근할 수 있습니다. 첫번째 값의 인덱스는 언제나 0을 가지며 제일 마지막 값의 인덱스는 언제나 list의 길이에서 1을 뺀 인덱스를 갖습니다.
![img_1.png](img_1.png)

## Creating a MutableList with specified elements
코틀린에서는 MutableList를 만들기 위한 함수 mutableListOf()라는 함수를 제공하고 있습니다.

이 MutableList는 다양한 타입의 List가 될 수 있습니다. 예를 들어, Int, Long, Double, Float, Char, String, Byte 그리고 Boolean 까지 가능합니다.

MutableList를 만드는 예제를 함꼐 보겠습니다. 꺽새 괄호 안에는 어떠한 타입의 MutableList를 만들지에 대한 타입선언입니다. 이에 대해서는 이후에 좀 더 알아보도록 하겠습니다.

```kotlin
// Int타입의 값을 가지는 MutableList만들기
val mutableListA = mutableListOf<Int>(1, 2, 3, 4, 3)
println(mutableListA)

// String 타입의 값을 가지는 MutableList
val mutableListB = mutableListOf<String>("Kotlin", "JetBrains")
println(mutableListB)

// Boolean 값을 가지는 빈 MutableList
val mutableListC = mutableListOf<Boolean>()
println("Empty list $mutableListC")
```
위의 코드 결과는 아래와 같습니다.
```shell
[1, 2, 3, 4, 3]
[Kotlin, JetBrains]
Empty list []
```
또한 코틀린의 경우 List에 어떠한 타입이 들어가는지 선언을 안해주어도 가능합니다.
```kotlin
//declaring a mutable list of integers
val mutableListA = mutableListOf(1, 2, 3, 4, 5)

println(mutableListA) // [1, 2, 3, 4, 5]
```

##Reading list from input
콘솔에서 입력되는 데이터를 얻기 위해서는 먼저 MutableList를 선언하면서 사이즈와 타입을 선언해야 할겁니다. 그리고 괄호 안에는 readLine()!!함수를 만들어 콘솔에서 입력되는 값을 가져옵니다. readLine()!!함수는 String을 반환하기 때문에 이것을 적절한 타입으로 변환하는 것을 잊지말고 해주어야 합니다.
```kotlin
val numbers = MutableList(5) {readLine()!!.toInt()}
println(numbers) // [1,2,3,4,5]
```

## Reading list from input
여기에서 소개하는 것들을 모두 기억하려고 하지마세요! 이곳에 있는 예제들을 이용해 실제 프로젝트에서 사용하면 그것을 족합니다.

일정한 크기의 인풋을 읽기 위해 먼저 선행되어야 할 것은 mutableList를 만들고 list의 크기를 알아야 합니다. {} 안에 readLine()!! 함수를 넣음으로써 콘솔로 부터 얻어지는 값들을 읽게 도와줍니다. radLine()!!함수는 String 타입을 반환하기에 우리는 적절한 타입으로 변환하는 것을 잊지 말아야 합니다.
```kotlin
val numbers = MutableList(5) { readLine()!!.toInt() }
println(numbers) // [1,2,3,4,5]
```
이 코드를 설명하자면 각 한 줄에 하나의 번호가 위치한 5개의 줄에서 값을 읽어오는 코드입니다.

만약 한 줄에 있는 모든 수를 읽고 싶다면 다음과 같이 접근할 수 있습니다. readLine()함수를 이용한 후 split 함수를 이용할 수 있습니다.

```kotlin
val numbers = readLine()!!.split(" ").map { it.toInt() }.toMutableList()
println(numbers) // [1,2,3,4,5]
```

위의 예제를 보겠습니다. 먼저 readLine()함수를 이용해 string 값을 읽고 그 값에 split() 함수를 사용했습니다. 이 함수는 string의 값을 공백 또는 일정한 패턴을 이용해 자르는 함수입니다. 그리고 이 잘라진 값들에 대해 map함수를 사용해 모든 값에 toInt() 함수를 적용했고 toMutableList함수를 이용해 MutableList로 만들었습니다.

또는 엔터키(라인브릭)과 공간에 관련된 무시함으로써 값을 얻는 방법도 있습니다. 이번에는 정규식을 한번 사용해보겠습니다.

```kotlin
val regex = "\\s+".toRegex() // \s 는 공백문자를 의미함
val str = "1 2\t\t3 4\t5 6"
val nums = str.split(regex).map { it.toInt() }.toMutableList()
println(nums) // [1,2,3,4,5]
```

정규식을 사용한다면 띄워쓰기 \t \n 등을 무시할 수 있습니다.

## MutableList size

특정한 크기의 mutable list를 만들고 싶다면 MutableList(n)으로 만들 수 있습니다.

```kotlin
val list = MutableList(5) {0}
println(list) // [0,0,0,0,0]
```

대괄호 안을 보면 초기값을 줄 수 있다는 사실을 확인할 수 있습니다. 만약 "a"라고 값을 준다면 이 리스트는 "a"로 초기화 됩니다.

```kotlin
val list = MutableList(5) {"a"}
println(list) // [a,a,a,a,a]
```

mutable list는 언제나 특정한 크기를 가집니다. 이는 몇개의 요소가 있는지를 말합니다. 이 크기를 알기 위해서는 size 프로퍼티를 이용해 파악할 수 있습니다.

```kotlin
val numbers = mutableListOf<Int>(1,2,3,4,5)
println(numbers.size)
```

## Accessing elements

인덱스를 이용해 값을 할당하면 리스트에 저장된 값을 변경할 수도 있습니다.

```kotlin
list[index] = elem
```

인덱스를 이용해 값을 얻을 수도 있습니다.

```kotlin
val elem = list[index]
```

리스트의 인덱스는 0부터 시작하고 list.size -1까지 사용할 수 있습니다. 예제를 통해 조금 더 확인해 보겠습니다.

```kotlin
val numbers = mutableListOf(0,0,0)
numbers[0] = 1
numbers[1] = 2
numbers[2] = numbers[0] + numbers[1]

// [1,2,3]

println(numbers[0]) // 1
println(numbers[2]) // 3
```

위의 예제를 살펴보겠습니다. 먼저 모든 요소들이 길이 3의 리스트를 만들었습니다. 그리고 인덱스 0을 이용해 1을 첫번째 값에 1을 할당했고, 인덱스 1을 이용해 2번째 값에 2를 할당했습니다. 그리고 인덱스 2를 이용해 마지막 인덱스에 0번째 값과 1번째 값을 더한 값을 할당했습니다.

만약 존재하지 않는 인덱스를 이용해 리스트에 접근한다면 error가 발생합니다. 그렇다면 예제를 통해 알아봅시다.

```kotlin
val elem = numbers[3]
```

위의 예제를 실행하면 에러가 발생하게 됩니다.

위에서 이야기한 것처럼 마지막 인덱스의 값은 list.size -1이 됩니다. 그렇다면 이를 활용해 각 리스트이 마지막 값을 가져와 봅시다.

```kotlin
val alphabet = mutalbleListOf('a','b','c','d')

val last = alphabet[alphabet.size -1] //d
val preList = alphabet[alphabet. size -2] // c
```

코틀린은 리스트와 관련된 편리한 함수를 제공하고 있습니다. 그 중 first last lastIndex를 알아보겠습니다.

```kotlin
println(alphabet.first()) // 'a'
println(alphabet.last()) //'d'
println(alphaber.lastIndex)
```

이를 활용해 좀 더 가독성 있는 코드와 에러를 방지하며 프로그램을 작성할 수 있습니다.

## Conclusion

이번에는 mutableList에 대해 이야기 해 보았습니다. 모두를 기억할 필요는 없지만 아래의 사항을 한번 더 복기 해보겠습니다.

- mutableList는 인덱스를 이용해 접근할 수 있는 데이터 구조이다
- 첫번째 인덱스는 0 이다.
- mutable list는 항상 일정한 크기를 가진다
- 각 요소들은 값읗 수정할 수 있다
- 다양한 타입을 가지는 MutableList를 만들 수 있다.
