---
title:      C# Grammar#08 | IEnumerator, IEnumerable 및 yield
date:       "2022-09-30"
categories: ["C#", "01.Structure"]
tags:       ["C#", "Grammar", "Unity"]
# pin:        true
---


# IEnumerator(열거자) : 열거자를 구현하는데 필요한 인터페이스
- 데이터를 리턴(```Getter```)하는 열거자
- 클래스 내부의 컬렉션에 대해 반복할 수 있도록 도와준다.
```c#
public interface IEnumerator
{
    object Current { get; }
    bool MoveNext();
    void Reset();
}
```
- 반복자 구현에 필요한 함수 3 가지를 구현하게 강제하는 인터페이스다. 
- 인터페이스는 텅텅 비어있고 아무것도 기능하는게 없다. 
- 그 자체로는 반복자를 구현하기 위해선 최소한 저 위의 3 개 함수를 알아서 구현하면 된다. 라고 틀을 잡아주는 것 뿐이다.

# IEnumerable : 열거자 IEnumerator를 리턴
- 열거자를 리턴하는 ```Getter```의 ```Getter```
- 열거자 ```IEnumerator```를 ```Get```하는데 필요한 인터페이스
- 클래스 내부의 컬렉션에 대해 반복할 수 있도록 도와주는 IEnumerator를 노출시킨다. 
- 열거할 수 있는 제네릭이 아닌 모든 컬렉션에 대 한 기본 인터페이스.
```c#
public interface IEnumerable
{
    IEnumerator GetEnumerator();
}
```
- 객체로 ```foreach```문을 돌리기 위해서는 그 객체 타입이 ```IEnumerable```을 상속받은 클래스여야 한다. 
- ```IEnumerable```을 상속받아 ```GetEnumerator```()을 구현한 클래스이어야 ```foreach```로 내부 데이터를 열거할 수 있다.
- 이렇게 ```IEnumerable``` 로 각각의 독립적인 ```IEnumerator``` 객체들을 관리할 수도 있다

# 예제
- ```IEnumerable``` 상속 및 구현
```c#

// Simple business object.
public class Person
{
    public Person(string fName, string lName)
    {
        this.firstName = fName;
        this.lastName = lName;
    }

    public string firstName;
    public string lastName;
}
```

- ```IEnumerator``` 상속 및 구현
```c#
// When you implement IEnumerable, you must also implement IEnumerator.
public class PeopleEnum : IEnumerator
{
    public Person[] _people;

    // Enumerators are positioned before the first element
    // until the first MoveNext() call.
    int position = -1; // 👉 _people 배열 인덱스로 활용할 것.

    public PeopleEnum(Person[] list)
    {
        _people = list;
    }

    public bool MoveNext()
    {
        position++;
        return (position < _people.Length);
    }

    public void Reset()
    {
        position = -1;
    }

    object IEnumerator.Current
    {
        get
        {
            return Current;
        }
    }

    public Person Current
    {
        get
        {
            try
            {
                return _people[position];
            }
            catch (IndexOutOfRangeException)
            {
                throw new InvalidOperationException();
            }
        }
    }
}
```
- ```IEnumerator``` 상속받고
  - ```MoveNext``` 구현
    - _```people```의 인덱스 ```position```를 증가시킨다.
    - ```position```가 _```people``` 배열 크기를 넘어버리는데 도달했다면 더 이상 ```MoveNext```가 불가능하므로 ```false``` 리턴
  - ```Reset``` 구현
    - _```people```의 인덱스 ```position```를 -1 로 초기화
  - ```Current``` 구현
    - 2 가지 ```Current```를 구현했다.
      - ```public Person Current```
        - ```Person```객체인 _```people```[```position```]를 리턴함.
        - 이건 ```IEnumerable``` 인터페이스를 구현한 프로퍼티가 아니다. ```Person``` 리턴이니까..!!
      - object ```IEnumerator.Current```
        - 위의 ```Current``` 을 실행시켜서 리턴받은 ```Person``` 객체를 ```object```(```System.Object```)로 업캐스팅 형변환해 리턴함


# yield
- ```IEnumerable```, ```IEnumerator``` 를 상속받는 객체를 간단하게 구현할 수 있는 것이나 마찬가지다. 마치 일시정지와 같은 기능이다.
- ```IEnumerable``` 클래스에서 ```GetEnumerator```() 메서드를 구현하는 한 방법으로 yield 를 사용할 수 있다.
  - 즉, ```GetEnumerator```() 메서드에서 ```yield return```를 사용하여 컬렉션 데이타를 순차적으로 하나씩 넘겨주는 코드를 구현하고, 리턴타입으로 ```IEnumerator``` 인터페이스를 리턴할 수 있다.
  - ```C#```에서 ```Iterator``` 방식으로 ```yield``` 를 사용하면, 명시적으로 별도의 ```Enumerator``` 클래스를 작성할 필요가 없다. 컴파일러가 알아서 만들어주기 때문이다!


# Result
- C#의 모든 ```Collections``` 컬렉션은 ```IEnumerable```, ```IEnumerator```를 상속받아 구현하고 있다.
- 그래서 ```List```, ```Array``` 같은 컬렉션 클래스 객체들을 ```foreach```문에서 돌릴 수 있는 것

---

# 참고 사이트
- [공부하는 식빵맘](https://ansohxxn.github.io/c%20sharp/enumerate/)