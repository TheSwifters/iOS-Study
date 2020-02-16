# CH4. 흐름 제어 구문

흐름 제어 구문이란 프로그램 실행 과정에서 실행 흐름을 제어하기 위한 목적으로 사용되는 구문이다.  
예를 들면 순차적으로 실행되어야할 동작을 실행하지 않고 건너 뛰거나 되돌아오도록 할 수 있고,  
필요에 따라 반복적으로 동작 하게 할 수도 있다.

스위프트는 일반적으로 통용되는 흐름 제어 구문 대부분을 제공하는데, 성격에 따라 세가지로 나눌 수 있다.  

- 조건문(Conditional Statments)
- 반복문(Loop Statements)
- 제어 전달문(Control Transfer Statements)

-

## - 조건문
조건문은 프로그램에서 하나 또는 그 이상의 조건값에 따라 특정 구문을 실행하도록 프로그램의 흐름을 분기하는 역할을 한다.  
조건문 에서 사용되는 조건 값은 프로그램이 어떻게 분기되고, 어느부분의 코드가 실행될지를 결정하는데 사용된다.   
실행 방식에 따라 조건문이 세분화 되는데, 스위프트에서 제공하는 조건문은 크게 세가지가 있다.  
### - if
if 구문은 하나 또는 그 이상의 조건을 평가하고 결과에 따라 코드 블록의 실행여부를 결정하는 구문 이다.

#### - if
if 구문의 가장 기본적인 형태 이다 <조건식> 에는 반드시 Bool 타입이 들어가야 하며,  
들어간 조건식의 값이 true 이면 <실행할 구문>을  실행 하고 false 이면 실행하지 않고 건너뛴다.

```swift
if condition {
print("condition is true")
}
```

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
그 else if 문의 조건 또한 참이 아닐경우 다음 else if 문의 조건을 확인한다.  
여러개의 else if 문을 사용 할 수 있고   모든 조건이 참이 아닐경우 else 문이 있다면 else 문의 코드블럭의 동작을 실행하고 else문이 없다면 아무 동작도 하지 않는다.  

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

```swift
guard condition else { return }
// condition이 true 일 경우 guard문의 하위 코드 블럭이 실행 된다.

```
guard 구문은 else 블록이 반드시 있어야 하며 else 블록에는 이후 코드 진행을 막아주는 구문이 반드시 포함 되어야 한다.  
함수의 실행을 종료하는 return 또는 반복문을 종료하는 break 가 이에 해당된다. 

### - #available 
앱을 개발 하다 보면 OS 버전별로 구문을 나누어 작성해야 하는 경우가 있다. 이때 사용하는것이 #available 구문이다.  
 #available 구문을 사용하면 직접적으로 OS의 버전을 구분 할 수 있다.

```swift
if #available(iOS 13, OSX 10.15, watch 1, *) {
// iOS 13버전, OSX 10.15버전, watch 1 버전에 대한 조건
}
```

###- switch
switch 구문은 if 구문과 달리 조건식이 아니라 패턴으로 비교하고 그 결과를 바탕으로 실행 블록을 결정하는 조건문 이다.  
switch 구문에 사용된 비교 대상은 반드시 하나의 비교 패턴과 일치해야 한다.  
만약 비교대상이 비교 패턴중 어느 것 과도 일치하지 않아 분기문 내의 어떤 블록도 실행되지 못하는 경우를 방지하기 위해 default 구문을 추가 해야 한다.  
단, default 구문을 대신 하여 모든 패턴을 매칭시킬 수 있는 구문이 존재하는 경우에 한하여 default 구문을 생략 할 수 있다.  

패턴을 비교하는 방법은 여러가지가 있다.
 
- 단일 값 비교 

```swift
switch someInt {
case 0:
print("someInt is 0")
case 1: 
print("someInt is 1")
default:
print("default")
}
```
- 여러 값 비교

```swift
switch someInt {
case 0, 1: 
print("someInt is 0 or 1")
case 2, 3, 4:
print("simeInt is 2 or 3 or 4")
default: 
print("default")
}
```

- 범위 비교

```swift 
switch someInt {
case 0...5:
print("someInt is 0...5")
case 6...10:
print("someInt is 6...10")
default:
print("default")
}
```
  
- 특정 타입 비교

```swift

//튜플의 경우
let value = (1, 3)
switch value {
case let (x, 3):
print("When second value of tuple is 3, the first value is \(x)")
case let (3, y):
print("When first value of tuple is 3, the second value is \(y) ")
case let (x, y):
print("The value is (\(x), \(y))") 
// 튜플의 모든 경우를 명시 했기 때문에 default구문을 작성하지 않아도 된다.
}


// enum을 사용하는 경우
enum SomeEnum {
case first, second
}

let someEnum = SomeEnum.first

switch someEnum {
case .first:
    print("someEnum's value is first")
case .second:
    print("someEnum's value is second")
// enum의 모든 case를 명시해 주었기 때문에 default 구문을 작성하지 않아도 된다.
}
```



### - 반복문
반복문은 주어진 조건에 따라 코드 블록을 반복적으로 실행 하고


























