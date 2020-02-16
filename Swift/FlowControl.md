# CH4. 흐름 제어 구문

## 흐름 제어 구문

흐름 제어 구문이란 프로그램 실행 과정에서 실행 흐름을 제어하기 위한 목적으로 사용되는 구문이다.
예를 들면 순차적으로 실행되어야할 동작을 실행하지 않고 건너 뛰거나 되돌아오도록 할 수 있고, 
필요에 따라 반복적으로 동작 하게 할 수도 있다.

스위프트는 일반적으로 통용되는 흐름 제어 구문 대부분을 제공하는데, 성격에 따라 세가지로 나눌 수 있다.

- 반복문(Loop Statements)
- 조건문(Conditional Statments)
- 제어 전달문(Control Transfer Statements)

-

### - 조건문
조건문은 프로그램에서 하나 또는 그 이상의 조건값에 따라 특정 구문을 실행하도록 프로그램의 흐름을 분기하는 역할을 한다.
조건문 에서 사용되는 조건 값은 프로그램이 어떻게 분기되고, 어느부분의 코드가 실행될지를 결정하는데 사용된다.
실행 방식에 따라 조건문이 세분화 되는데, 스위프트에서 제공하는 조건문은 크게 세가지가 있다.

#### - if  
if 구문은 하나 또는 그 이상의 조건을 평가하고 결과에 따라 코드 블록의 실행여부를 결정하는 구문 이다.

```swift
if condition {
print("condition is true")
}
```

위 구문은 if 구문의 가장 기본적인 형태 인데 <조건식> 에는 반드시 Bool 타입이 들어가야 하며, 
들어간 조건식의 값이 true 이면 <실행할 구문>을  실행 하고 false 이면 실행하지 않고 건너뛴다.

#### - if ~else
if ~ else 구문은 if 구문이 참이 아닐경우 else 구문의 코드블럭의 동작이 실행된다.

```swift
if  condition {
print("dondition is true")
} else { 
print("condition is false")
}
```

#### - if ~ else if
if ~ else if 구문은 if 구문이 참이 아닌경우 그다음 else if 구문의 조건을 확인하여 참인경우 그 else if 구문의 코드블럭의 동작을 실행 한다.
그 else if 문의 조건 또한 참이 아닐경우 다음 else if 문의 조건을 확인한다. 여러개의 else if 문을 사용 할 수 있고 모든 조건이 참이 아닐경우 else 문이 있다면 else 문의
코드블럭의 동작을 실행하고 else문이 없다면 아무 동작도 하지 않는다.

```swift
if someInt == 1 {
print("somdeInt is 1")
} else if someInt == 2 {
print("someInt is 2")
} else if someInt == 3 {
print("someInt is 3")
} else {
print("There is no condition")
}
```


### - guard
guard 구문은 주로 후속 코드들이 실행되기전 조건을 만족 하는지 확인하는 용도로 사용한다.
특정 조건을 만족하지 않는다면 해당 구문을 조기 종료 하기 위한 목적으로 사용한다.




- witch




### - 반복문
반복문은 주어진 조건에 따라 코드 블록을 반복적으로 실행 하고


























