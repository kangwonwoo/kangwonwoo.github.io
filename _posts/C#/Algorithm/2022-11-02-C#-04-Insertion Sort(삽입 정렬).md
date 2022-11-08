---
title:      C#4 | Insertion Sort
date:       "2022-11-02"
categories: ["C#", "03.Algorithm"]
tags:       ["C#", "Algorithm"]
# pin:        true
---

# 정렬 알고리즘 (Algorithm)

## 삽입 정렬 (Insertion Sort)
- 각 숫자를 적절한 위치에 삽입하는 방법으로 문제 해결
- 필요할 때만 위치를 바꾸게 된다

```c#
Cycle 1

기본
1 10 5 8 7 6 4 3 2 9

첫번째
1 5 10 8 7 6 4 3 2 9
  ↑ 


두번째
1 5 8 10 7 6 4 3 2 9
    ↑
·
·
·

아홉번째
1 5 8 7 6 4 3 2 9 10
                ↑
```

```c#
Cycle 2

기본
1 5 8 7 6 4 3 2 9 10

첫번째
1 5 7 8 6 4 3 2 9 10
    ↑ 


두번째
1 5 7 6 8 4 3 2 9 10
      ↑
·
·
·

다섯번째
1 5 7 6 4 3 2 8 9 10
            ↑
```

```c#
버블 정렬 공식

int main (void)
{
  int i, j, temp;
  int array[10] = {1, 10, 5, 8, 7, 6, 4, 3, 2,9};
  for(i = 0; i < 10; i++)
  {
    for(j = 0; j < 9 - i; j++)
    {
      if(array[i] > array[j + 1])
      {
        temp = array[i];
        array[j] = array[j + 1];
        array{j + 1} = temp;
      }
    }
  }
  for(i = 0; i < 10; i++)
  return 0;
}
```




---

# 참고 사이트
- [동빈나](https://www.youtube.com/watch?v=8ZiSzteFRYc&list=PLRx0vPvlEmdDHxCvAQS1_6XV4deOwfVrz&index=4)