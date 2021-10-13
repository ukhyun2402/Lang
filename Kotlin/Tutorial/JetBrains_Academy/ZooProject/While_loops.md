# Theory: While loops

조건의 상태에 따라서 코드블락을 반복하는 방법은 다양하게 있습니다. 이번에는 다양한 방법 중 while과 do..while에 대해서 알아보겠습니다. 이 둘의 차이는 조건의 평고와 반복의 순서에서 차이가 납니다.

## While loop
while 루프는 코드블락과 결과가 boolean인 조건문의 포함되어있습니다. 만약 조건문이 true인 경우 코드블락을 수행합니다. 코드블락의 실행은 조건문이 false가 될 때까지 실행됩니다. while 루프는 시작하기 앞서 조건을 평가하며 이를 pre-test loop라고 부르는 경우도 있습니다.

```kotlin
while (condition) {
    // body
}
```

반복문의 body는 어떠한 코드도 올 수 있습니다.(변수 선언, 데이터 읽기, 조건문, 반복문)

또한 반복문을 무한히 수행하고 싶다면 조건문에 true를 위치시켜 무한히 반복하게 할 수 있습니다.

```kotlin
while (true) {
    // body
}
```

이러한 무한반복문에 대해서는 이후에 좀 더 자세히 알아보겠습니다.

지금은 아래의 예제에 집중해 봅시다. 아래의 코드는 number가 5가 되기 전까지 숫자를 출력하는 코드입니다.

```kotlin
fun main() {
    var i = 0
    while (i < 5) {
        println(i)
        i++
    }
    println("Completed")
}
```

이 반복문에 대해서 좀 더 자세히 알아보겠습니다. 먼저, 변경 가능한 변수 i에 0을 할당합니다. 그리고 while 반복문이 수행되기 전에 i < 5 의 조건을 확인하며 결과 값이 true임을 확인합니다. 값이 true이기에 while 반복문의 코드블락을 수행합니다. 이렇게 계속 반복하여 수행하면 어느샌가 i가 4가 되며 그 떄에는 4가 출력된 이후 i는 5가 되면서 더이상 while 조건문의 값이 true가 되지 앟기에 반복문은 무시되며 이후의 코드인 Completed가 출력됩니다. 그러한 결과는 다음과 같습니다

```text
0
1
2
3
4
Completed
```

반복문은 Char, String 그리고 다른 타입 역시도 사용할 수 있습니다. 아래의 프로그램은 한 줄에 모든 알파벳을 작성하는 프로그램입니다.

```kotlin
fun main() {
    var letter = 'A'

    while (letter <= 'Z') {
        print(letter)
        letter++
    }
}
```

위의 프로그램은 알파벳 A를 입력받은 후 Z가 될때까지 반복문을 수행합니다. 결과는 다음과 같습니다.

```text
ABCDEFGHIJKLMNOPQRSTUVWXYZ
```

이렇게 가능한 이유는 바로 증감연사자를 이용해 다음 문자를 얻을 수 있기 떄문입니다. (이에 대해서는 이전 Unicode에서 알아봄)

다음의 예제는 입력값으로 받은 숫자를 출력하는 프로그램입니다. 이 때 Scanner 클래스의 hasNext()함수를 이용해 다음과 같이 구현할 수 있습니다.

```kotlin
import java.util.*

fun main() {
    val scanner = Scanner(System.`in`)
    while(scanner.hasNext()) {
        val next = scanner.next()
        println(next)
    }
}
```

입력값이 다음과 같다면
```text
Kotlin is a modern language
```

결과는 다음과 같습니다.

```text
Kotlin
is
a
modern
language
```

String 값을 입력받을 때에는 hasNext(), 정수값을 받을 때에는 hasNextInt()를 사용합니다. 

## Do...while loop
do while 반복문은 while문과 다르게 먼저 실행 한 후에 조건문을 검사하는 반복문입니다. 만약 조건이 true이면 조건이 false가 될 때까지 실행합니다. do...while반복문은 먼저 실행한 후에 조건을 하기에 post-test loop라고 불리어 집니다. 그래서 do while 반복문은 어떠한 상황이든 한번은 코드블락이 실행됩니다.

do...while 반복문은 do 키워드와 코드블락, 그리고 while(조건) 으로 구성돼 있습니다.

```kotlin
do {
    // body
} while (condition)
```

아래의 프로그램은 숫자를 입력받고 출력하는 프로그램입니다. 만약 사용자가 0을 입력했다면 프로그램은 출력을 그만두게 됩니다. 

```kotlin
fun main() {
    do {
        val n = nextLine().toInt()
        println(0)
        
    } while (n > 0)
}
```

```text
1
2
4
0
3
```

```text
1
2
4
0
```

do...while문 역시 while문 처럼 무한반복이 가능합니다.

## Conclusion
이번에는 while문과 do...while문에 대해서 배웠습니다. 두 반복문 모두 조건문과 코드블락을 가지고 있으며, 차이점은 먼저 실행하는지에 대한 차이 밖에 없었습니다. while 반복문은 코드블락을 수행하기 전에 조건문을 수행하지만 do while문은 실행한 후에 조건문을 수행합니다.

실제로는 while문을 좀 더 많이 사용합니다.