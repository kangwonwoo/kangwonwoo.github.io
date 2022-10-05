---
title:      C# Grammar#10 | Struct
date:       "2022-09-30"
categories: ["C#", "01.Data Structure"]
tags:       ["C#", "Grammar", "Unity"]
# pin:        true
---

# Struct(구조체)
- 구조체란 클래스와 같은 사용자 정의 데이터형입니다.
- 사용자 정의 데이터형란 기본 데이터 형식과 메소드로 구성 된 복합 데이터형을 의미합니다.
- 구조체는 클래스와 비슷한 부분이 많다.
- 하지만, 가장 큰 차이는 클래스는 참조 형식이고, 구조체는 값 형식입니다.
- 구조체는 클래스와 같이 메서드, 프로퍼티 등 거의 비슷한 구조를 가지고 있습니다.
- 새로운 연산자를 사용하지 않고 인스턴스화 할 수 있습니다.
- 생성자를 선언할 수 있으나 반드시 파라미터가 있어야 합니다.
- 하지만, 상속은 할 수 없습니다.
- 인터페이스(```interface```)를 구현할 수는 있습니다.
```c#
접근-제한자 struct 구조체-이름
{
    생성자(프로퍼티)
    멤버 변수
    맴버 메서드
}
```
```c#
using UnityEngine; 

public class StructExample : MonoBehaviour 
{ 
    public struct Struct 
    { 
        public int a, b; 

        public Struct(int a, int b) 
        { 
            this.a = a; 
            this.b = b; 
        } 

        public void DebugLog() 
        { 
            Debug.LogFormat("a = {0} b = {1}", a, b); 
        } 
    } 

    void Start() 
    { 
        Struct str1;  // new 사용하지 않고 선언 
        str1.a = 10; 
        str1.b = 20; 
        str1.DebugLog(); // 출력 : a = 10 b = 20  

        Struct str2 = new Struct(1, 2); // new 사용하여 선언 
        str2.DebugLog(); // 출력 : a = 1 b = 2  
    } 
}
```
- 구조체는 스택이 바로 할당되기 때문에 가비지 컬렉션이 발생하지 않아서 속도면에서 시스템에 부하를 적게 주나,구조체 내에 변수가 많으면, 크기가 제한적인 스택에 저장되기 때문에, 스택 오버플로우가 발생할 수 있습니다.

---

# 참고 사이트
- [코더 제로](https://coderzero.tistory.com/entry/%EC%9C%A0%EB%8B%88%ED%8B%B0-C-%EA%B0%95%EC%A2%8C-14-%EA%B5%AC%EC%A1%B0%EC%B2%B4Struct)