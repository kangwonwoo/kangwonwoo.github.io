---
title:      C#2 | Algorithm
date:       "2022-11-01"
categories: ["C#"]
tags:       ["C#", "Algorithm"]
# pin:        true
---

# 정렬 알고리즘 (Algorithm)

## 선택 정렬 (Selection Sort)
- 가장 작은 숫자부터 순차적으로 선택해서 제일 앞으로 보낸다.

```c#
기본
1 10 5 8 7 6 4 3 2 9


첫번째
1 2 5 8 7 6 4 3 10 9
  ↑ 


두번째
1 2 3 8 7 6 4 5 10 9
    ↑
·
·
·

아홉번째
1 2 3 4 5 6 7 8 9 10
```

```c#
선택 정렬 공식

int main (void)
{
  int i, j, min, index, temp;
  int array[10] = {1, 10, 5, 8, 7, 6, 4, 3, 2,9};
  for(i = 0; i < 10; i++)
  {
    min = 9999;
    for(j = i; j < 10; j++)
    {
      if(min > array[j])
      {
        min = array[j];
        index = j;
      }
    }
    temp = array[i];
    array[i] = array[index];
    array{index} = temp;
  }
  for(i = 0; i < 10; i++)
  {
    printf("%d ", array[i]);
  }
  return 0;
}
```




---

# 참고 사이트
- [동빈나](https://www.youtube.com/watch?v=8ZiSzteFRYc&list=PLRx0vPvlEmdDHxCvAQS1_6XV4deOwfVrz&index=2)