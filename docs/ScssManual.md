# SCSS

- ## 정의

  - 컴파일이 되는 CSS.
  - SASS 프로그램을 사용한다.
  - SCSS는 기존 CSS 문법과 거의 동일하다는 차이점이 있다.
  - 대부분 케밥케이스를 사용한다.

- ## 데이터 타입

  - `Numbers` 1, .82, 20px, 2em…
  - `Strings` bold, relative, "/images/a.png", "dotum"
  - `Colors` red, blue, #FFFF00, rgba(255,0,0,.5)
  - `Booleans` true, false
  - `Nulls` null
  - `Lists` $list: apple, orange, banana
  - `Maps` $map: (apple: a, orange: o, banana: b);

- ## 문법

  - ### Variable

    - #### 선언 : $변수명 : 속성값;
    - #### 사용 : $변수명
    - 대체로 파일 최상단에 선언함.
    - constants 폴더 내에 타입별로 파일을 생성해서 사용함. (colors, typography 등)
    - 문자열 내에 변수를 넣고 싶을 때는 `#{$변수명}` 으로 사용 가능함.

  - ### Extend

    - #### 사용 : @extend 선택자;
    - 선택자에 해당되는 스타일이 재활용된다.
    - 별개의 스타일로 만들어지지 않고, 선택한 선택자 옆에 추가된다. (ex: .circle, .face { })

  - ### Mixin

    - #### 선언 : @mixin mixin-name ($param1, $param2) { }
    - #### 사용 : @include mixin-name(param);
    - mixins 폴더 내에 타입별로 파일을 생성해서 사용함. (flexbox, text-style 등)

  - ### Function

    - #### 선언 : @function function-name($param1, $param2) { @return return-value; }
    - #### 사용 : function-name(param);
    - 리턴값이 존재함.

  - ### Placeholder

    - #### 선언 : %style { }
    - #### 사용 : @extend %style;
    - 해당 Placeholder를 Import했을 경우, 선택자 별로 스타일이 생성되지 않고 통합되어 생성된다. (ex: .circle, .face { })

  - ### Condition

    - #### 삼항 연산자 : if (조건문, 참, 거짓)
    - #### if-else : `@if () { }` `@else if () { }` `@else { }`

  - ### For

    - @for $i from 1 through 3 { } : 1 이상, 3 이하
    - @for $i from 1 to 3 { } : 1 이상, 3 미만

  - ### Debug
    - $debug $i : 컴파일 시 $i의 값을 콘솔에 찍어줌

- ## 린팅

  - ### [stylelint](https://stylelint.io/)

    - npm install 및 Extension install 후 사용 가능
    - stylelint의 추가기능을 지원하는 lib들이 많아 원하는 기능을 찾아 모두 설치해주어야 함
    - 다양하게 커스텀 가능하지만 오류도 많고 다루기 까다로움.

  - ### scss-lint

    - Extension 및 Ruby Sass install 후 사용 가능

  - ### sass-lint
    - npm install 및 Extension install 후 사용 가능
