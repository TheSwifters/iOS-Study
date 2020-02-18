# CH03. Collection (집단 자료형)




## Contents


- A. Array
- B. Set
- C. Tuple
- D. Dictionary



## A. Array (배열)


- index로 구분되는 순서에 따라 데이터가 정렬된 목록 형태의 자료형

- 중복된 값 저장 가능하다.

- 모든 프로그래밍 언어에서 공통적으로 제공하는 자료형

- index는 0부터 시작해서 아이템이 추가될 때 마다 차례대로 증가한다.

- 중간에 값을 생략하거나 건너뛰는 경우는 없다. 인덱스에 연결된 아이템이 삭제되면 다음 아이템들이 앞으로 이동하면서 빈 인데스 채운다.

- 배열에 저장할 아이템의 타입에는 제약이 없지만, 하나의 배열제 저장하는 아이템 타입은 모두 같아야 한다.

- 선언 시 배열에 저장할 아이템 타입을 명확히 정의해야 한다.

- 배열의 크기는 동적으로 확장할 수 있다.

  - 배열은 index 를 직접 참조하기 위해 참조할 인덱스가 이미 만들어져 있어햐 한다. 그렇지 않을 경우 잘못된 인덱스 참조에 의한 오류가 발생한다.
  - index와 값에 대한 보장이 있어서 저장된 index가 아니면 오류를 발생시킨다. 때문에 값을 꺼내기 쉽다.

- 사용 방법

  - 선언과 초기화
  - 1.

  ```swift
  var arr: Array<String> 	// 선언
  
  var arr2 = Array<String>() 	// 선언과 초기화 동시에 초기화
  ```

  ```swift
  // 1. 초기화
  arr = Array()						// 선언시 지정타입 지정하면 타입생략 가능
  
  
  ```

  ```swift
  // 2. 초기화
  arr = Array<String>()			
  ```

  - 2.

  ```swift
  var student: [String]			// 선언
  student = [String]()			// 초기화
  student = []							// 초기화, 빈배열을 새로 만들어 넣는 것이기 때문에 초기화라고 보지 않는 경우도 있다.
  ```

  ```swift
  var student = [String]()		// 선언과 초기화
  ```

  

  

  - 정적 사용 방법 -  처음부터 배열을 구성하는 item 포함해 정의하는 방식

    ```swift
    var student = ["참솔", "중창", "유진", "의석", "지승", "지승"]
    
    student[0] 				// 참솔
    student[1]				// 중창
    
    
    
    ```

  - 범위 연산자를 이용한 인덱스 참조 가능

    ```swift
    var student = ["참솔", "중창", "유진", "의석", "지승", "지승"]
    student[2...4]		// 유진, 의석, 지승
    student[3..<5]		// 의석, 지승
    ```

    

  - 동적 사용 방법 - 선언과 초기화만 해놓고 필요시에 아이템을 추가하는 경우

    ```swift
    var student = [String]()
    student = [“참솔”, “중창”, “유진”, “의석”, “지승”,”유경”,”홍삼”,”수한”,”지현”]
    
    ```

  -  아이템 값 수정하기

    ```swift
    student[1] = "유진"
    student[5..<7] = ["유꽁", "동현"]
    
    student[7...8] = ["이수한"]		// 범위에 속하는 배열 아이템 모두 제거된 후 그자리에 새로 대입하는 배열이 차지하게 된다.
    ```

  - 아이템 추가하기

    - append(_:)

      - 입력된 값을 배열의 맨 뒤에 추가한다.
      - 존재하지 않는 인덱스에 접근하면 오류 발생한다. 때문에 이 메소드는 아이템이 추가되기 전에 먼저 배열의 크기를  +1만큼 확장하여 공간확보 후 인자값을 마지막 인덱스의 위치에 추가

      ```swift
      student.append("지현")
      ```

      

    - insert(_:at:)

      - 배열의 원하는 위치에 직접 추가하고 싶을 때 사용

      ```swift
      student.insert("기민", at: 0)
      ```

      

    - append(contentsOf:)

      - 배열의 가장 뒤에 여러개의 아이템 추가하고 싶을 때 사용

      ```swift
      student.append(contentOf: ["진경","인준"])
      ```

  - 배열의 순회탐색

    - 반복문 사용

    ```swift
    for i in 0..<student.count {
      print("\(i)번째 학생은 \(student[i])입니다.")
    }
    ```

    - 단, for문 돌릴때 조건문에 배열의 크기를 확인한다면 매번 조건식을 평가하기 때문에 배열의 크기를 매번 다시 계산하게 되므로 어느정도 이상의 크기가 되는 배열을 반복적으로 읽어오도록 처리할 경우 실행속도가 떨어지므로 변수나 상수에 크기를 저장해 두고 사용하는 편이 좋다.

    ```swift
    var count = student.count
    for i in 0..<count {
      print("\(i)번째 학생은 \(student[i])입니다.")
    }
    ```

    - Lterator: for문에 배열을 직접 넣어 사용하는 방식

    ```swift
    for row in student {
      let index = student.index(of: row)
      print(“\(index)번째 학생은  \(row)”)
    }
    ```

    



## B. Set (집합)


- 중복되지 않은 유일 데이터들이 모인 집합 형태의 자료형

- 순서가 중요하지 않은 데이터 혹은 중복없이 저장해야 하는 데이터들을 다룰 때 사용한다.

- 해시 연산의 결과 값을 이용해 데이터를 저장하므로 집합에 저장할 데이터 타입은 해시 연산을 살 수 있는 타입이어야 한다.

  - 해시연산: 임이의 입력된 메시지를 고정 길이의 데이터 크기로 변환해주는 알고리즘. 아무리 긴 데이터나 아무리 짧은 길이의 데이터라 해도 고정 길이의 데이터로 변환
  - 스위프트에서 제공하는 모든 기본 타입은 기본적으로 해시 연산 가능하다.
  - 스위프트에서 기본으로 제공하는 타입 아닐 경우 Hashable 프로토콜을 구현해야한다.

- 인덱스가 없고, 넣는 순서대로 들어가지 않는다. (값이 해시연산되어 들어가기 때문)

- 사용법

  - 선언과 초기화

  ```swift
  var id: Set<String>			// 선언
  id = Set<String>				// 초기화
  ```

  ```swift
  var id = Set<String>()		// 선언과 초기화
  ```

  

  - 값

  ```swift
  var id: Set = [“Chamsol Kim”, “eujin811”, “hondonghyun”, “jisng”, “JoongChangYang”, “Lance-Ahn”, “Soohan Lee”, “wanderingfairy”, “you kyung”]
  ```

  

  - 아이템 추가

    - 한 번 추가된 아이템은 몇번을 다시 추가하더라도 처음 상태에서 더는 추가되지 않는다.
    - append는 불가능하다. (배열처럼 인덱스가 있는게 아니라 값을 넣을 때마다 해시 연산하여 순서를 정하기 때문)
    - insert(_:)

    ```swift
    id.insert("gitbot")
    ```

  - 크기확인

  ```swift
  id.count
  ```

  - 아이템확인 : true, false

  ```swift
  id.contains("jisong")		// true
  ```

- 순회탐색

  ```swift
  for i in id {
    print(i)
  }
  
  // [“you kyung”, “eujin811”, “hondonghyun”, “jisng”, “JoongChangYang”, “Lance-Ahn”, “Soohan Lee”, “Chamsol Kim”, “wanderingfairy”, ]
  ```

- 정렬 -> sort()

  - 정렬된 결과를 받을 수 있다. 단, 집합 자체에 순서를 적용하는 것이 아닌 메소드의 반환값을 정렬하는 것에 지나지 않는다.

  ```swift
  for i in id.sorted() {
    print(i)
  }
  
  // [“Chamsol Kim”, “eujin811”, “hondonghyun”, “jisng”, “JoongChangYang”, “Lance-Ahn”, “Soohan Lee”, “wanderingfairy”, “you kyung”]
  ```

- 아이템 삭제

  - .removeAll() 일괄삭제

  ```swift
  id.removeAll()
  ```

  - .remove() 일치항목 삭제
    - 일치항목 삭제후 삭제 아이템 반환
    - 일치항목 없을 경우 nil을 반환한다.

  ```swift
  id.remove("jisng")			// jisng반환
  id.remove("jisong")			// nil 반환
  ```

- 집합관련 메소드

- insersection(_:) 

  - 양쪽 집합에서 공통되는 아이템만 선택해 새로운 집합 만들어주는 메소드

- symmetricDifference(_:) 

  - 양쪽 집합 중에서 어느 한쪽에만 있는 아이템 선택해 새로운 집합 만들어 주는 메소드

- union(_:) 

  - 양쪽 집합에 있는 모든 아이템을 선택하여 새로운 집합을 만들어주는 메소드

- subtract(_:) 

  - 한쪽 집합에 있는 모든 아이템에서 다른 쪽 집합에도 속하는 공통 아이템 제외한 새로운 집합 만들어주는 메소드

  ```swift
  var odd: Set = [1,3,5,7,9]
  var num: Set = [1,2,3,4]
  odd.subtract(num)		// 5,7,9
  ```

  ![IMG_3476](https://user-images.githubusercontent.com/53036267/74744501-b94af400-52a5-11ea-91aa-584f66444c4f.jpeg)

- isSubset(of:) 

  - 주어진 집합의 값 전체가 특정 집합에 포함되는지 판단하여 true, false 반환

- isStrictSubset(of:)

  -  isSubset(of:)와 비슷하지만 주어진 두 집합이 일치할 경우 false

![IMG_3475](https://user-images.githubusercontent.com/53036267/74744873-5148dd80-52a6-11ea-937e-65a178cc953c.jpeg)

- isSuperset(of:) 
  - 주어진 집합이 특정집합의 하위 집합이면 true 반환
- isStrictSuperset(of:) 
  - isSuperset(of:) 와 비슷하지만 주어진 두 집합이 같으면 false반환

![IMG_3474](https://user-images.githubusercontent.com/53036267/74744899-5efe6300-52a6-11ea-9720-f04782ca5b35.jpeg)

- isDisjoint(with:) 
  - 두 집합 사이의 공통 값이 없을 때 true 반환

![IMG_3477](https://user-images.githubusercontent.com/53036267/74744937-70e00600-52a6-11ea-9469-b3bc79b66d5d.jpeg)



## C. Tuple 


- 타입과 상관없이 데이터들을 모은 자료형

- 수정, 추가, 삭제 등 변경이 불가능하다. (상수와 비슷한 성격)

- 값이 바뀔 가능성을 근본적으로 제거하고 싶을 때 사용

- 튜플 내에서 저장되는 데이터들이 모두 달라도 상관없음

- index갖는다. 

  - 속성 형식으로, index 내부 값 확인시 .index로 확인

- 순회의 특성을 지원하지 않는다. 

  - (for ~ in 구문의 조건에 넣어서 사용 불가. 
  - index가 속성 형식으로 있기 때문

- 함수나 메소드에서 둘 이상의 값 반환할 때 튜플을 사용하여 전달하면 전달 용이

  

- 사용법

  - []이 아닌 ()을 이용
  - [index]형식이 아닌 .index형식

```swift
let tupleValue = (“A”, “b”, 1,  2.5, true)	// 

tupleValue.0		// A
tupleValue.1		// b
```

- 튜플은 별도의 선언구문이 없다. 하지만 타입 어노테이션으로 타입 지정이 가능하다.

  - 들어갈 아이템 개수와 순서에 맞게 타입을 선언해야 한다.
  - 소수점이 있는 숫자의 경우 따로 어노테이션 하지 않으면 Double타입으로 추론된다 
    - Double타입이 Float보다 상위 타입이라

  ```swift
  let first:  (Int, String, Character) = (1, “ab”, “c”) 
  
  ```

- 하나의 타입만 있는 튜플은 아이템 타입의 일반 자료형이 된다.

  ```swift
  var third : (String) = (“test”)
  type(of: third)				// String
  ```

- Binding (바인딩 방식)

  - 가독성 높이기 위해 튜플 아이템을 개별 변수나 상수로 각각 할당 받는 방식

  - '_' 사용해 아이템 중 일부는 받지 않을 수 있다.

    - 컴파일러가 해당 아이템을 할당하지 않고 패스한다.

    ```swift
    let tupleValue:(String, Character, Int, String) = (“김유진”, “M”, “27”, “jinjin”)
    let (name, gender, age, _) = tupleValue		// jinjin 할당 안하고 패스
    
    type(of: name)			// String 
    ```

  - 함수나 메소드에서 둘 이상의 값 반환할 때 튜플을 사용하여 전달

    ```swift
    func getTupleValue() -> (String, Character, Int) { 			return (“김유진”, “M”, “27”)
    }
    
    let (name, gender, age) = getTupleValue()
    ```

  

## D. Dictionary



- 배열과 유사하지만 index 대신 고유의 key 사용
- Key - value 형식
- 연관된 데이터를 순서 없이 모은 자료형
- 순서는 있으나 Set과 같이 해시 연산에 의해 저장되므로 넣는 순서대로 들어가지 않는다.



- 딕셔너리는 배열과 달리 키 자체가 일련의 순서를 갖지 않는다. 

- 타입은 알 수 있느나 실제 어떤 데이터가 키로 사용될지 미리 알 수 없으므로 기존에 사용된적 없던 새로운키가 입력되면 키와 값을 저장하기 위한 튜플을 하나 만들어 저장하면 된다.

- 새로운 인덱스 공간을 확보하고 크기를 늘릴 필요가 없다. (단, 딕셔너리 변수가 초기화 되 있을 경우)

  - 위 와 같은 특성으로 키와 값에 대한 보장이 없다. 때문에 프로그램에서 딕셔너리로부터 키를 호출해서 저장된 값을 불러올 때 없는 키 호출 가능성 때문에 값을 옵셔널 타입으로 반환한다.
  - (해시 연산에 의한 결과 값 역시 연속되는 값은 아니다.)

- value가 옵셔널 타입으로 들어있다.

- 주의점

  - 하나의 키는 하나의 데이터에만 연결된다.
  - key는 중복이 불가능하다. 
    - key중복 선언 시 아이템 수정이 이루어진다.
  - 저장할 수 있는 데이터 타입에는 제한이 없다. (단, 저장 데이터 타입은 일치해야 한다.)
  - 딕셔너리의 아이템 순서는 없지만 내부적 순서는 있다. (해시 연산을 통해 순서가 저장된다.)

- 사용법

  - 선언

  ```swift
  var user: Dictionary<String, Int>
  var user2: [String: String]
  var user3: [String: Int]
  var user4: [String: Int]
  ```

  - 초기화 

  ```swift
  user = Dictionary<String, Int>()
  user2 = [String: String]()
  user3 = Dictionary()		// 타입 어노테이션을 통해 딕셔너리 타입을 명시적으로 선언한 경우에만 사용 가능
  user4 = [:]							// 빈 딕셔너리를 넣어준 것, 타입 어노테이션을 통해 딕셔너리 타입을 명시한 경우에만 사용가능
  
  ```

  - 아이템 추가, 수정

    - 없는 키 적고 바로 값 넣어서 아이템 추가하는 경우

    ```swift
    var mascot = [String: String]()
    mascot["EBS"] = "뽀로로"			// 추가 (없는 키에 값을 넣어 추가)
    mascot["EBS"] = "펭수"			//	수정 
    ```

    

    - .updateValue(<저장데이터>, forKey:<저장데이터>)
      - 수정, 추가 전 값을 반환

    ```swift
    mascot.updateValue("미키마우스", forKey: "디즈니")	// 추가, nil반환
    
    mascot.updateValue("엘사", forKey: "디즈니")		// 수정, 수정전 value반환 -> 미키마우스
    
    ```

  - 아이템 삭제

    - nil값 넣는 방법
    - removeValue(forKey:)
      - 삭제한 값 반환, 없는 키 삭제시 nil값 반환

  ```swift
  mascot["EBS"] = nil
  
  mascotValue(forKey: "디즈니")		// 엘사
  mascotValue(forKey: "디즈니")		// nil
  ```

  - 순회 탐색

  ```swift
  let mascot: [String: String] = ["EBS": "펭수", "디즈니": "엘사"]
  for row in mascot {
  	let(key, value) = row
  	print(“현재 \(key): \(value) ”) }
  }
  // 현재 EBS: 펭수
  // 현재 디즈니: 엘사
  
  for (key, value) in mascot {
    print(“현재 \(key): \(value) ”) }
  }
  // 현재 EBS: 펭수
  // 현재 디즈니: 엘사
  ```

  

  

  



