---
title:      C# Grammar#0x | Dictionary
date:       "2022-09-16"
categories: ["C#", "01.Structure"]
tags:       ["C#", "Grammar", "Unity"]
# pin:        true
---

# Dictionary

# Dictionary를 List로 변환
- 먼저 ```Dictionary```를 ```List```로 변환하는 방법
- ```Dictionary```는 키(```Key```)와 값(```Value```)로 구성되어 있습니다.
- ```Dictionary```를 리스트로 변환하려면 ```Dictionary```의 키를 담을 ```List```와 ```Dictionary```의 값을 담을 ```List```가 필요합니다.

# Dictionary를 List로 변환 예제
```c#
using System.Collections.Generic;

namespace Sample
{
	class Sample
	{
		static void Main()
		{
			var myTable = new Dictionary<string, string>();
			myTable.Add("Korea", "Seoul";);
			myTable.Add("Japan", "Tokyo";);
			myTable.Add("America", "Washington";);

			var kList = new List<string>(myTable.Keys);
			var vList = new List<string>(myTable.Values);

			Console.WriteLine("[{0}]", string.Join(", ", kList));
			Console.WriteLine("[{0}]", string.Join(", ", vList));

			Console.ReadKey();
		}
	}
}

결과

[Korea, Japan, America]

[Seoul, Tokyo, Washington]
```
- 리스트 변수인 kList에는 키만 저장하였고, vList 리스트 변수에는 값만 저장

# List를 Dictionary로 변환
- 이번에는 ```List```에서 ```Dictionary```로 변환하는 방법
- ```Dictionary```로 변환하기 위해서는 2개의 리스트가 필요합니다.

```c#
using System;
using System.Collections.Generic;
using System.Linq;

namespace Sample
{
	class Sample
	{
		static void Main()
		{
			var kList = new List<string>();
			kList.Add("Korea";);
			kList.Add("Japan";);
			kList.Add("America";);

			var vList = new List<string>();
			vList.Add("Seoul";);
			vList.Add("Tokyo";);
			vList.Add("Washington";);

			Dictionary<string, string> myTable = 
			kList.Zip(vList, (k, v) => new { k, v }).ToDictionary(a => a.k, a => a.v);

			foreach(KeyValuePair<string, string> item in myTable) {
				Console.WriteLine("[{0}:{1}]", item.Key, item.Value); 
			}

			Console.ReadKey();
		}
	}
}

결과

[Korea:Seoul]

[Japan:Tokyo]

[America:Washington]
```
- 2개의 리스트를 ```LINQ```의 ```Zip``` 메서드를 사용하여 ```Dictionary``` 타입으로 변환
- ```Dictionary```는 키와 값으로 구성되어 있기 때문에 2개의 리스트가 필요 또한 2개의 리스트 요소 개수는 동일해야 합니다.

# 정리
- ```Dictionary```를 ```List```로, ```List```를 ```Dictionary```로 변환하는 방법
- 개인적으로는 ```List```를 ```Dictionary```로 변환하는 경우는 많지 않지만 ```Dictionary```를 ```List```로 변환하는 경우가 종종 있습니다.
- 키만 필요하던지, 또는 값만 필요한 경우만도 있기 때문에 가끔씩 변환 작업을 하기도 합니다.
- 필요한 처리에 맞게 변환을 할 수 있기 때문에 알아두면 유용하게 사용하실 수 있습니다.


---

# 참고 사이트
- [포뇨아빠](https://ponyozzang.tistory.com/329)