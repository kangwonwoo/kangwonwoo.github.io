---
title:      C# Grammar#11 | Property
date:       "2022-09-30"
categories: ["C#", "01.Data Structure"]
tags:       ["C#", "Grammar", "Unity"]
# pin:        true
---

# Property(프로퍼티)
- 프로퍼티(```Property```)는 속성이라는 의미를 지니고 있다.
- 멤버 변수를 속성이라고도 하는데 정보 은닉을 위해 ```private```로 선언을 하면 ```get, set``` 메소드를 구현해야 한다. 이를 편리하게 해주는 것이 ```C#```의 ```property```이다.
- ```C#``` 프로퍼티는 간단하고 유연성있게 전용 필드의값을 읽거나 쓰는 메커니즘을 제공한다.
- ex)
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Property : MonoBehaviour
{
    private int salary;

    public int SalaryP { get { return salary; } 
                 private set { salary = value; } }

    void Start()
    {
        SalaryP = 50;

        print(SalaryP);
    }
}
```
- ```Salary``` 프로퍼티의 ```set``` 앞에 ```private``` 를 붙여 다른클래스에선 읽기만 가능하고 쓰기가 불가능하도록 했다.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Employee : MonoBehaviour
{
    Property property = new Property();

    void Start()
    {
        property.SalaryP = 30; // 액세스 오류

        print(property.SalaryP);
    }
}
```
- 다른 클래스에서 ```SalaryP```에 쓰기를 시도할경우 액세스 오류가 발생하며 값을 가져오는데에는 문제가 없는것을 확인할 수 있다.

# 간단한 Property
```c#
public float HP { get; set; }
```
---

# 참고 사이트
- [IT's me](https://grayt.tistory.com/68)
- [Slate Blog](https://lesslate.github.io/unity/Unity-C-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0/)