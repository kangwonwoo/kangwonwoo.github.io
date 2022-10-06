---
title:      C# Grammar#02 | enum
date:       "2022-09-08"
categories: ["C#", "01.Structure"]
tags:       ["C#", "Grammar", "Unity"]
# pin:        true
---

# enum
> 열거형 -> 같은 종류의 상수 모음

- 상수나 변수를 사용하는 이유
  - 상수 리터럴을 통한 하드 코딩은 그 의미를 알기 쉽지 않고 리팩토링이 어렵기 때문에.
- ```enum``` **열거형을 사용하는 이유**
  1. 상수이므로 의미를 알기 쉽다.
  2. 연관된 것들을 하나의 ```enum``` 으로 묶기 때문에 그룹화를 할 수 있다.
  3. 상수나 변수가 굉장히 많아지면 이름이 중복될 우려도 있는데 서로 다른 ```enum```에 속하면 이름이 동일해도 전혀 다른 것으로 간주되기 때문에 이름 중복 우려를 방지할 수 있다.s

```c#
       enum Choice
        {
            Rock,
            Paper,
            Scissors
        }

        static void Main(string[] args)
        {
```

- 열거형 선언은 클래스처럼 함수 밖에서 선언되야 한다.
- **내부적으론 정수가 저장된다.**
  - 값이 입력 안되면 디폴트 값 0 에서 출발하여 0, 1, 2, 3, 이런식으로 저장된다. 이전 값에서 +1 한 값으로 설정된다.
  - 아래와 같이 직접 값을 명시해줄 수도 있다.

  ```c#
      enum Choice
    {
        Rock = 1,
        Paper,  // 자동으로 2가 된다. 이전 값이 1 이어서.
        Scissors = 0
    }
  ```

- ```enum```은 상수의 모음이기 때문에 ```case```문에 사용할 수 있다.
- ```Choice.Rock```, ```Choice.Paper``` 이거 자체로는 정수타입이 아니라 ```enum``` 타입이기 때문에 ```(int)```로 형 변환 해주어야 한다. ✔현재 switch 조건문의 ```choice```가 ```int```형이니까 !!!
  - ```(int)Choice.Rock```, ```(int)Choice.Paper```

  ```c#
  int choice = 2;
  switch(choice)
  {
        case (int)Choice.Rock: 
            break;  
        case (int)Choice.Paper: 
            break;
  }
  ```

열거형 변수는 초기화 하지 않으면 자동으로 첫번째 값으로 초기화 한다.

```c#
      enum Choice
        {
            Rock = 1,
            Paper,  // 자동으로 2가 된다. 이전 값이 1 이어서.
            Scissors = 0
        }

        static void Main(string[] args)
        {
            Choice choice;  // 초기화 안했지만 자동으로 choice = Choice.Rock 이 됨.
        }
```
  
  

---

# 참고 사이트
- [공부하는 식빵맘](https://ansohxxn.github.io/c%20sharp/ch2-1/)