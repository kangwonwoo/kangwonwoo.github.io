---
title:      C# Grammar#13 | Exception
date:       "2022-09-30"
categories: ["C#", "01.Structure"]
tags:       ["C#", "Grammar", "Unity"]
# pin:        true
---

# Exception(예외처리)
- 게임에선 예외처리를 잘 하지 않는 편이다. 그냥 크래쉬 된 체로 냅두고 문제가 되는 코드 자체를 나중에 수정하는게 보통이다. 
- 예외처리가 큰 의미가 없기 때문이다. 그래도 게임이라도 네트워크 오류 같은 문제는 예외 처리가 필요함!
- 예외가 발생하는 상황 예시
  - 0 으로 나눌 때
  - 잘못된 메모리를 참조할 때
  - 오버플로우 등등…

- 모든 종류의 예외 클래스들의 조상이다. 따라서 모든 예외를 다 받을 수 있다.
  - 위와 같이 순서를 바꾸면 모든 예외를 ```catch``` (```Exception e```)에서 다 처리할 수 있기 때문에 ```catch``` (```DivideByZeroException e```)는 절대 쓰일일이 없다는 것을 컴파일 타임에도 알 수 있다. 
  - 따라서 이렇게 순서를 짜면 컴파일 오류가 발생한다.

# 예외 클래스
- ```Exception```을 상속 받는 예외 클래스를 직접 만들 수도 있다
```c#
class TestException : Exception { }
```
- 이렇게 정의해둔 후, 어떤 상황에선 내가 만든 예외 클래스 타입의 객체가 던져지도록 할 수 있다. ```throw```를 사용.

- catch (TestException e) 혹은 catch (Exception e)에서 이를 처리할 수 있다.
```c#
throw new TestException();
```

- 이렇게 함수 안에서도 던질 수 있다. 꼭 ```try```문 안에서만 가능한 것은 아니다.
```c#
static void TestFunc()
    {
        throw new TestException();  // 함수 안에서 던져도 잡아준다. 
    }
```

---

# 참고 사이트
- [공부하는 식빵맘](https://ansohxxn.github.io/c%20sharp/ch9-7/)