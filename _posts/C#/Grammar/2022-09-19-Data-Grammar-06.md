---
title:      C# Grammar#06 | Convert.Toint32()
date:       "2022-09-19"
categories: ["C#", "01.Data Structure"]
tags:       ["C#", "Grammar", "Unity"]
# pin:        true
---

# Convert
- 먼저 ```Convert``` 의 정의는 "기본 데이터 형식을 다른 기본 데이터 형식으로 변환한다." 라고 합니다. ```Boolean```, ```Char```, ```Byte```, ```Int```, ```Double```, ```Decimal```, ```String```, ```DateTime``` 등등.. 이러한 형식들을 지원한다고 합니다. 

## Convert.ToInt32(string s) 
- 메소드는 문자열로 표현된 수를 그에 상응하는 32비트 부호있는 정수로 변환한다.
- ```s```가 ```null```이라면, ```ArgumentNullException```을 던지지 않고 0을 반환한다.
- ```s```가 정수 형태가 아닌 값이라면, ```FormatException```을 던진다.
  - ( ```FormatException``` : 인수의 형식이 올바르지 않거나 합성 서식 문자열이 잘못 만들어진 경우 예외가 throw )
- ```s```가 32비트 부호있는 정수의 최소값보다 작거나 최대값보다 크다면, ```OverflowException```을 던진다.

# Parse
- ```Parse``` 는 "문자열 표현을 해당하는 형 으로 변환한다." 라고 되어있네요. ```ToString``` 과 비슷한 표현중 하나인 것 같습니다. 예를 들어 문자열을 ```Int``` 형 으로 변환하고 싶다면 ```Int32.Parse```("문자열") 이렇게 사용하면 됩니다.

## Int32.parse(string)
- Int32.Parse (string s) 메소드는 문자열로 표현된 수를 그에 상응하는 32비트 부호있는 정수로 변환한다.
- ```s```가 ```null```이라면, ```ArgumentNullException```을 던진다.
  - ( 메서드에 제공된 인수 중 하나가 유효하지 않을 때 예외가 throw )
- ```s```가 정수 형태가 아닌 값이라면, ```FormatException```을 던진다.
- ```s```가 32비트 부호있는 정수의 최소값보다 작거나 최대값보다 크다면, ```OverflowException```을 던진다.

## TryParse
- ```TryParse``` 는 "문자열 표현을 해당하는 형 으로 변환한다. 반환 값은 변환의 성공 여부를 나타낸다." 라고 되어있습니다. ```Convert``` 와 ```Parse``` 는 단순한 값만 변환하고 반환했는데, 정의에 나와있는 것 처럼 변환의 성공 여부 즉, ```true``` 와 ```false``` 값을 반환한다는 것을 알 수 있습니다.



---

# 참고 사이트
- [Human & ATmega128](https://blog.daum.net/hugerock70/590)
- [이난의 개발자 블로그](https://2-nan.tistory.com/43)