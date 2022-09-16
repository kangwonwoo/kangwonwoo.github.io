---
title:      C# Grammar#04 | while, do while
date:       "2022-09-08"
categories: ["C#", "04.Data Structure"]
tags:       ["C#", "Grammar", "Unity"]
# pin:        true
---

# while
C# while 문은 while 조건식이 true인 동안 계속 while 블럭을 실행할 때 사용한다. 다음 예제는 while문을 사용하여 1부터 10까지 숫자를 콘솔에 출력하는 코드이다. 아래에서 i가 11이 되면 while 조건식이 false가 되어 while 루프를 빠져나오게 된다.

```c#
static void Main(string[] args)
{
    int i = 1;

    // while 루프
    while (i <= 10)
    {
       Console.WriteLine(i);
       i++;
    }
}
```

---

# do while
do ~ while은 위의 while문과 거의 비슷하나, 마지막 while 조건식까지 가기 전에 do ~ while 사이의 블럭을 **미리 한 번 실행한다는 점에서 차이**가 있다.

```c#
static void Main(string[] args)
{
    int i=1;

    // do ~ while 루프
    do
    {
       Console.WriteLine(i);
       i++;
    } while (i < 10);
}
```

---

# C# 반복 구문 예제
아래 예제는 콘솔로부터 Q키가 입력되지 전까지 계속 키 입력을 받아들인 후, 그동안 입력된 키들을 foreach 루프를 써서 출력해 본 예이다.

```c#
using System;
using System.Collections.Generic;

namespace MySystem
{
    class Program
    {
        static void Main(string[] args)
        {
            List<char> keyList = new List<char>();
            ConsoleKeyInfo key;
            do
            {
                key = Console.ReadKey();
                keyList.Add(key.KeyChar);
            }
            while (key.Key != ConsoleKey.Q); // Q가 아니면 계속

            Console.WriteLine();

            foreach (char ch in keyList) // 리스트 루프
            {
                Console.Write(ch);
            }
        }
    }
}
```

---

# 참고 사이트
- [1commit1zerocoke](https://jinuk97-dev.tistory.com/4)
- [예제로 배우는 C# 프로그래밍](https://www.csharpstudy.com/CSharp/CSharp-looping.aspx)