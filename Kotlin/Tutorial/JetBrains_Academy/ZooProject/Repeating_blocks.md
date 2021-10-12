# Theory: Repeating blocks

프로그램을 작성하다보면 같은 코드를 반복해야 할 때가 있습니다. 그럴 때 어떻게 하셨나요? 복사 붙여넣기를 했나요? 그렇다면 백번 반복 해야 된다면 어떻게 해야될까요? 이런 경우 복사 붙여넣기는 부적절한 방법이 됩니다.

그래서 코틀린은 이러한 반복을 위해 다양한 구문이 존재합니다. 이 구문을 아시다시피 Loop라고 말합니다. 

## Repeat Loop

간단한 반복문을 원할 때에는 repeat(n) 과 { } 중괄호를 이용해 반복문을 사용합니다. 그리고 reapeat함수 안에 있는 n은 { }에 있는 코드를 몇번 반복할지를 결정하는 인자입니다.

```kotlin
repeat(n) {
    // statements
}
```

예를 들어 다음과 같은 코드가 있다면 Hello가 3번 반복해 출력됩니다.

```kotlin
fun main() {
    repeat(3) {
        println("Hello")
    }
}
```

```text
Hello
Hello
Hello
```

> 만약 n이 음수거나 0인 경우엔 반복문이 실행되지 않습니다.

## Reading and processing data in loop

이러한 repeat함수를 이용해 변수를 선언하고 계산을 할 수도 있습니다.

아래의 예제를 봅시다. 아래의 프로그램은 입력값을 받아 합을 계산하는 프로그램입니다. 첫번째 숫자는 몇개의 숫자가 있는지를 나타내느 숫자입니다.

```kotlin
fun main() {
    val n = readLine()!!.toInt()
    var sum = 0

    repeat(n) {
        val next = readLine()!!.toInt()
        sum += next
    }
}
```

이 코드는 몇개의 숫자가 있는지를 입력받아 n에 할당한 후 합을 저장할 변수 sum을 선언합니다. 그 후 n 만큼 반복하면서 숫자를 입력받고 합을 더하는 함수입니다.

## conclusion
Loop는 코드를 반복할 때 매우 유용한 구문입니다. 이번엔 repeat()함수를 이용한 간단한 반복문을 알아보았습니다. 이후엔 이보다 좀 더 확장된 반복문을 알아볼 예정입니다.