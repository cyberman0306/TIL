xcode를 연결할때는
xcode 내부 git 설정을 하고 나서
git hub와 연결해야한다


# 1월 9일 오늘의 배움
## 열거형이란?

`열거형`이란 같은 주제로 연관된 데이터들을 멤버로 구성한 자료형, 연관성이 있는 값들을 모아놓은 것을 말한다. 

## 열거형 왜 쓰는데?
개발자가 일일이 "apple"을 변수의 값으로 집어넣는다고 해보자, 순간의 실수로 "apple" 대신 "applee" 라고 변수값을 넣으면 오류가 발생하게 된다.  
따라서 `개발자의 오류를 줄이고` `가독성을 높이기 위해` 열거형이 사용된다.

## 열거형 예시

```swift
@State var menu: Menu = .beef

enum Menu {
	case beef, pork, chicken
}

if menu == .beef { }
else if menu == .chicken { }
```
```swift
let menus: [Food] = [.apple, .banana, .pineapple]
enum Food: String {
	case apple = "사과" //케이스 내부는 '.' 사용하지 않는다
	case banana = "바나나"
	case pineapple = "파인애플"
}
```
switch와 같이 사용하면 효율적인 코딩이 가능해진다
## enum을 사용한 switch문
```swift

struct MyEnum: View {
    @State var menu: Menu = .pork

    enum Menu {
        case beef, fork, chicken
    }
    var body: some View {
        switch menu {
            case .pork:
                Text("돼지고기")
            case .beef:
                Text("소고기")
            case .chicken:
                Text("치킨")
//            default:
//                Text("뭐고...?")  // enum에 있는 모든 것을 case로 해줬으면 default를 생략해주어도 된다!
        }
    }
}
```

---
## 옵셔널이란?
`옵셔널`이란 어떤 자료형에 대해서 그 값이 있을수도 있고 없을 수도 있음을 나타내는 타입

## 옵셔널 왜 쓸까?
1. 0 과 nil은 다르다
2. ""과 nil은 다르다  

따라서 값이 없을 수도 있음을 나타내는 자료형이 필요하다

## 어떻게 쓰는데?
`옵셔널`은 자료형 뒤에 `"?"`를 붙이면 옵셔널이 된다.

옵셔널이 붙은 자료형을 사용하고 싶으면 변수명 뒤에 `"!"`를 통한 옵셔널 강제해제를 해주거나 `"??"`를 사용하여 변수의 값이 있으면 그 값을 사용하고 값이 없으면 `"??"` 뒤의 값을 사용하도록 해주면 된다.

---
## closure - 이름이 없는 함수
`closure` 는 `익명함수`라고 한다.  
흔히 우리가 사용하는 함수도 `closure` 의 일종이다.
## 그래서 왜 쓰나요?
"왠지 이 함수는 한번 밖에 사용안할 것 같은데...?" 할때 사용한다.

## 클로저 표현식
```swift
{ (매개 변수) -> 리턴 타입 in
	실행 구문
}
```
- 클로저 예시
```swift
let hello = { () -> () in
	print("hello")
}
hello() // "hello"
```
- 클로저는 함수 파라미터 타입으로 클로저를 전달할 수 있다

## 후행 클로저 - 클로저를 읽기 쉽게?!
```swift
func doSomething(closure: (Int, Int, Int) -> Int) {
    closure(1, 2, 3)
}

doSomething(closure: { (a, b, c) in return a+b+c})

doSomething(closure: {
    return $0+$1+$2
})

doSomeThing(closure: {
    $0+$1+$2
})

doSomething() {
    $0+$1+$2
}

doSomething {
    $S0+$S1+$S2
}
// $0 -> 약식인수!
```
