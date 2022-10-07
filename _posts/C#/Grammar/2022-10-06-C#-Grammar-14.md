---
title:      C# Grammar#14 | Reflection
date:       "2022-10-06"
categories: ["C#", "01.Structure"]
tags:       ["C#", "Grammar", "Unity"]
# pin:        true
---

# Reflection(리플렉션)
- Unity를 C#으로 개발하다보면 “리플렉션”, 즉 ```reflection``` 이라는 단어를 종종 듣는다. 이는 C/C++에서 넘어온 개발자들이라면 다소 생소한 단어일 수 있다. 
- Java는 ```java.lang.reflection``` 이라는 패키지로 ```reflection```을 지원하고, C#에서는 ```System.reflection``` 네임스페이스를 통해서 지원한다
- 프로그래밍 언어에서 ```Reflection```이라는 말은 **```Runtime``` 시에 ```Object``` 객체의 형태나 타입에 대한 정보를 읽어 내는 것**을 말한다.
- C#을 사용하는 유니티에선 실행 중에도 멤버에 무엇이 있는지를 체크하고 이에 접근할 수 있는 UI를 열어 주는 등등 C#의 리플렉션 기능을 활용한다.

## .NET Reflection 
- .NET 객체의 클래스 타입, 메서드, 프로퍼티 등의 메타 정보를 런타임 중에 알아내는 기능을 제공한다.
- 이러한 메타 정보를 얻은 후, 직접 메서드를 호출하거나 프로퍼티를 변경하는 등의 작업도 가능하다.
- 객체에서 메서드를 직접 호출하는 경우가 더 빠르겠지만, 어떤 경우는 런타임중에 이런 메타 정보가 동적으로 알아낼 필요가 있다. 예를 들어, 테스트 어셈블리에 있는 테스트 클래스들의 ```Public``` 메서드를 선별해서 이를 동적으로 호출하는 경우라든가, 특정 클래스 안에 지정된 이름의 멤버가 있는지 판단하는 경우 등등에 ```.NET Reflection```이 활용될 수 있다.

```c#
using System;
using System.Collections.Generic;
using System.Reflection; /// 

namespace CSharp
{
    class Program
    {
        class Monster
        {
            public int hp;

            protected int attack;
            private float speed;

            void Attack() { }
        }

        static void Main(string[] args)
        {
            Monster monster = new Monster();
            Type type = monster.GetType(); 

            // moster가 참조하는 객체에 대한 정보들을 보고싶어요
            FieldInfo [] fields = type.GetFields(System.Reflection.BindingFlags.Public
                | System.Reflection.BindingFlags.NonPublic
                | System.Reflection.BindingFlags.Static
                | System.Reflection.BindingFlags.Instance);  

            foreach (FieldInfo field in fields)
            {
                string access = "protected";
                if (field.IsPublic)
                    access = "public";
                else if (field.IsPrivate)
                    access = "private";

                Console.WriteLine($"{access} {field.FieldType.Name} {field.Name}");
            }
        }
    }
}
```
```c#
< 출력 값 >

public Int32 hp
protected Int32 attack
private Single speed
```

- ```Object``` 클래스의 ```GetType()``` 함수
  -  해당 객체의 정보를 담은 ```Type```을 반환한다. 리턴 받은 이 ```Type```을 통해 ```GetType()```을 호출한 객체의 모든 세세한 정보들을 다 알 수 있다.
```c#
Monster monster = new Monster();
Type type = monster.GetType(); 
```
- ```Type``` 클래스의 ```GetFields``` 함수
  - 현재 ```type```에는 ```monster```가 참조하는 객체의 모든 정보가 들어있다.
    - ```type```은 객체의 여러가지 정보를 열람할 수 있는 함수와 프로퍼티를 가지고 있다. 멤버 변수(=필드)들의 정보를 배열로 리턴하는 ```GetFields()``` 함수, 객체의 생성자 목록을 배열로 리턴하는 ```GetConstructors()``` 함수, 멤버 함수들의 목록을 리턴하는 ```GetMethods()``` 함수 등등 정말 수~~~많은 함수들을 가지고 있다.
  - ```GetFields``` 함수는 해당 객체의 멤버 변수(=필드)들을 ```FieldInfo``` 타입의 배열로 리턴한다. ```FieldInfo```타입은 해당 멤버 변수의 정보를 담은 클래스다. 각각의 원소에는 멤버 변수 + 그의 정보가 각각 들어간다. (C# 문서에서 보니 원소의 순서는 꼭 멤버 변수가 선언된 순서와 일치하는 것은 아니라고 한다.)
    - ```GetFields()``` 매개 변수 없다면 자동으로 모든 ```public``` 멤버 변수(=필드)들의 정보(```FieldInfo```타입 객체)를 ```FieldInfo``` 타입의 배열에 담아 리턴한다.
- ```FieldInfo``` 타입의 객체 또한 해당 멤버 변수의 정보를 열람할 수 있는 여러 함수와 프로퍼티들을 가지고 있다.
  - ```IsPublic``` : 해당 멤버 변수가 ```public```이면 ```True```
  - ```IsPrivate``` : 해당 멤버 변수가 ```private```이면 ```True```
  - ```field.FieldType.Name``` : 해당 멤버 변수의 자료형 이름

## GetType() 과 typeof 의 차이
```c#
Monster monster = new Monster();
Type type = monster.GetType(); 

typeof(Monster);
enum Temp {}
typeof(Temp);
typeof(int);
```
- ```GetType()```
  - 런타임 시점. ```Object```를 상속받는 객체 인스턴스의 ```Type```을 알려준다.
- ```typeof```
  - 컴파일 시점. 클래스 자체의 ```Type```을 알려준다.


---

# 참고 사이트
- [RAPAPA DEV STORY](http://rapapa.net/?p=2550)
- [공부하는 식빵맘](https://ansohxxn.github.io/c%20sharp/ch9-8/)