---
title:      C# Self Study#01 | 슬라이더를 이용한 음량 조절, 키(신체) 조절과 게임 종료 버튼 구현
date:       "2022-09-22"
categories: ["C#", "01.Data SelfStudy"]
tags:       ["C#", "SelfStudy", "Unity"]
# pin:        true
---

# 음량 조절 (Script없이 구현하는 법)
![image](https://user-images.githubusercontent.com/106725953/191684360-5031773b-3bb4-4096-9844-56f8cae31a1d.png)
![image](https://user-images.githubusercontent.com/106725953/191685442-cff23944-ba2f-4671-a743-0f2379e253b0.png)

1. 음량을 조절할 슬라이더에 현재 유니티 Scene에서 사용중인 Light를 On Value Changed에 목록을 추가한 뒤 
드래그해서 끌어다 놓는다.
2. No.Function을 클릭후 Light에서 intensity를 찾아 넣어준다.
3. 슬라이더에 값이 제대로 작동하는지 확인해본다.

# 키(신체) 조절
![image](https://user-images.githubusercontent.com/106725953/191684545-b44293bf-1e67-49ef-bfc9-309cec2df7c1.png)

1. Main Camera를 Camera Offset 하위에 넣어둔 상태로 진행
2. Camera Offset 스크립트를 이용해서 Main Camera의 Y 값을 가져온다.
3. 카메라의 높이를 조절할 슬라이더에 현재 유니티 Scene에서 사용중인 Camera Offset를 On Value Changed에 목록을 추가한 뒤 드래그해서 끌어다 놓는다.
4. No.Function을 클릭후 에서 CameraOffset안의 cameraYOffset을 찾아 넣어준다.
5. 슬라이더에 값이 제대로 작동하는지 확인해본다.

# 게임 종료 버튼
![image](https://user-images.githubusercontent.com/106725953/191684713-90ad8651-2f06-4694-9259-fc964bf8a491.png)

1. 게임 종료 버튼을 만들어준다.
2. 위의 스크립트를 넣어준다
3. 버튼이 제대로 작동하는지 확인해본다.


---

# 참고 사이트
- [3D Client Programmer](https://grandstayner.tistory.com/entry/Unity-%EA%B2%8C%EC%9E%84-%EC%A2%85%EB%A3%8C%ED%95%98%EA%B8%B0)