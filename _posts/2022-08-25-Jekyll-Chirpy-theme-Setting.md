---
title:      Jekyll Chirpy theme Setting
date:       "2022-08-25"
categories: ["Tech Tip", "Github Pages"]
tags:       ["jekyll", "Github Pages", "Chripy"]
# pin:        true
---

# 참고 사이트
- [Chirpy 테마 커스터마이징](https://www.irgroup.org/posts/Chirpy-%ED%85%8C%EB%A7%88-%EC%BB%A4%EC%8A%A4%ED%84%B0%EB%A7%88%EC%9D%B4%EC%A7%95/) By 하얀눈길

---

<br>

> # 푸쉬 전 로컬에서 확인하기
>
> ```
> ＃Git Bash
> $ jekyll serve
> 
> ＃Web Browser
> http://localhost:4000/
> ```

> # GitHub Pages Source
>
> - _config.yml : 블로그 기본 환경세팅
>
> - _data : 왼쪽 사이드바 / 포스트 하단의 공유하기 버튼등의 구성을 변경, 언어 설정에 따라 기본적으로 화면에 나오는 단어들이 변경
>
> - _include : Side-Bar / toc / Google Analytics / footer / comments 등 **모듈형으로** 삽입되는 UI를 변경하는 공간
>
> - _layout : 블로그 전역에 적용되는 기본 형식, 카테고리, 포스트 등에 적용되는 형식등을 변경할 수 있습니다.
>
> - _posts : 내가 작성한 블로그 글을 저장해 두는 곳입니다.
>
> - _sass : css 파일을 커스터마이징 할 수 있습니다.
>
> - _site : 로컬에서 실행할 때, 화면 UI를 구성하는 모든 내용이 들어 있습니다. 이곳의 내용을 변경하면 로컬에는 잘 반영되지만, git에는 올라가지 않습니다. 또한 다른 기본 디렉토리의 내용을 변경하고 빌드하게 되면 이곳의 내용이 바뀌게 됩니다.
>
> - _tabs : 왼쪽 사이드바의 기본 탭메뉴들에 대한 랜딩페이지가 들어 있습니다.
>
> - assets : css, img등이 있습니다. 포스팅에 들어갈 이미지는 assets/img 아래에 넣으면 됩니다.
> 
> - tools : github에서 자동 배포를 위한 코드가 들어 있습니다. 이곳은 아예 건들지 맙시다