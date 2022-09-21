# 마구잡이 팁 정리

## 퍼블리싱 순서

1. #### 피그마 분석

- 에셋 추출
- 공통 스타일, 그리드, 컴포넌트 등 제작 (base, constants, layouts, mxins, modules)
- 제작하며 테스트용 컴포넌트 페이지 제작하면 더 좋음.

2. #### 시맨틱 태그 작성

- 제작해둔 스타일들을 기반으로 시맨틱 태그 작성.
- `div` 사용해도 내부 태그들만 생각하며 만들면 문제 없음 (스크린 리더기가 어떻게 읽을지 생각해볼 것)
- `button` 같이 여러 동작을 할 수 있는 태그에는 `aria-label`을 통해 선언
- 의미없는 아이콘은 `aria-hidden` 처리
- 안내하기 위한 태그들은 `visually-hidden` 클래스 추가
- `button`의 경우 `type="button"`을 꼭 넣어 줄 것

3. #### 그리드 시스템 적용

> 해당 강의에서는, 그리드 시스템을 Bootstrap에서 차용해옴. Bootstrap은 그리드 시스템 사용 시 .container>.row>.col-\* 의 형태를 권장함.

- 반응형에서 모든 width가 100%일 경우에는, md-12, lg-12로 `재정의 할 필요 없음`

```html
<div class="col-sm-4 col-md-12 col-lg-12"></div>
```

> 100% 인 이유 : 피그마를 보면, 그리드 시스템에 딱딱 맞아 떨어지게 되어있지 않음. 이런 경우, 컬럼으로 해결하려 하지 않아도 됨. 이번같은 경우에는 좌/우로 나누어서 해결하였음.

- 그리드 시스템으로 선언해둔 태그에는 `그리드 시스템 외 클래스를 부여하지 않는 것을 권장`.

4. #### 스타일링

- 모바일부터 순서대로 스타일을 입히며 레이아웃 배치
- block: 별도의 width/height값을 주지 않을 경우, width/height는 부모의 컨텐츠 width/height의 100%
- inline-block: 별도의 width/height값을 주지 않을 경우, width/height는 자신의 컨텐츠 width/height
- overflow: visible하면 넘쳐도 보임, overflow의 속성값은 무조건 width/height이 지정되어있어야만 작동할 수 있음.
- inline 요소에는 transform이 적용되지 않음. inline-block에는 적용됨.
- z-index는 부모사이의 z-index가 먼저 적용됨. 부모의 z-index가 더 높으면 자식의 z-index가 낮아도 위에 표시됨.
- transform의 translate3d 속성을 이용하면 위치 이동이 가능하며, 해당 옵션엔 transition 적용 가능 (일반 left, top등의 옵션으로는 transition 적용 불가능)
