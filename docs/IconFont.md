# 아이콘 폰트

- ## 사용 이유

  1. `SVG` 소스를 `HTML`에 직접 넣어 이용하면 `fill` 속성에 `currentColor` 라는 값을 사용할 수 있음.
  2. 해당 값은 `부모의 color`를 받아와서 사용하여 컨트롤이 편함.
  3. 위와 같이 `color` 외에도 다른 속성들을 `css`로 간편하게 다룰 수 있게 되는 장점이 있음.
  4. 다만 `HTML`에 `SVG` 소스를 많이 넣을 수록 관리하기도 어려워지고 라인수가 길어지기에 아이콘 폰트를 사용함.

- ## 제작 방법
  1. [icomoon](https://icomoon.io/app/#/select)에서 제작 가능하다.
  2. 위 링크 접속 후, `Import Icons` 로 `SVG` 파일을 `Import` 한다.
  3. 이후, `Font`로 제작할 `Item`들을 선택하여 `Generate Font`를 클릭한다.
  4. 각 `Item`들의 `Class`를 원하는 대로 네이밍하고, `Settings`를 통해 `Font Name`과 `Class Prefix` 등을 설정한다.
  5. 이후 `Download`를 누르면 `Icon Fonts`가 다운로드 된다.
  6. 압축 파일 내 `fonts 폴더`와 `style.css`를 프로젝트로 옮겨오면 완성.
