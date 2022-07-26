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
- block 요소의 height: auto는 자식 요소 크기를 기준으로 설정, width: auto의 경우에는 부모 요소 크기를 기준으로 설정.
- inline-block: 별도의 width/height값을 주지 않을 경우, width/height는 자신의 컨텐츠 width/height
- inline-block의 width: auto는 자식 요소의 크기를 기준으로 너비를 설정하는 반면, width: 100%는 부모 요소의 크기를 기준으로 너비를 설정하기에, 부모가 auto고 자식이 100%면 오작동함.
- overflow: visible하면 넘쳐도 보임, overflow의 속성값은 무조건 width/height이 지정되어있어야만 작동할 수 있음.
- inline 요소에는 transform이 적용되지 않음. inline-block에는 적용됨.
- z-index는 부모사이의 z-index가 먼저 적용됨. 부모의 z-index가 더 높으면 자식의 z-index가 낮아도 위에 표시됨.
- z-index를 모두 선언 안했을 경우, 나중에 선언된 요소가 더 높은 우선순위를 갖게 됨.
- transform의 translate3d 속성을 이용하면 위치 이동이 가능하며, 해당 옵션엔 transition 적용 가능 (일반 left, top등의 옵션으로는 transition 적용 불가능)
- tab-button과 tab-panel의 관계처럼 마크업 구조 상 서로의 연관관계를 엮을 수 없을 때 WAI ARIA ROLE을 이용 가능하다. 태그에 role 속성값을 주는 것이다(role=tablist, tab, tabpanel). 추가로 input과 label의 관계처럼, id와 aria-labelledby로 버튼과 패널을 묶어줄 수 있다.
- display: inline 인 애들끼리 붙어있으면, 서로간에 간격이 생긴다. 그럴땐 부모에게 flex나 inline-flex를 주면 해결됨.
- display: inline 인 애들은 padding,margin의 top/bottom 이 적용되지 않음. 줄 흐름이 방해되기 때문.
- Table 추천 스타일 : border-collapse: collapse; table-layout: fixed;
- Grid 시스템보다 범위를 넓게 하려면, (물론 Container를 안써도 되긴하지만) 클래스에 width를 별도 선언하지않고, margin에 -px를 주면 width가 넓어진다.
- CSS 속성 브라우저별 사용 가능 여부는 [여기](https://caniuse.com/)에서 확인 가능하다. <sub><sup>\* 검색 후, 각 영역에 마우스 올리면 해당 버전의 업데이트 날짜도 보인다.</sup></sub>
- flex-box의 자식에게는 order 속성을 부여할 수 있다. order를 통해 마크업순서와 상관없이 표시할 순서를 변경할 수 있다.
- `이미지의 종횡비를 맞출 때` (정사각형을 만들 때), 보통 wrapper의 width/height를 px로 고정하고 img에 w100%, h100%, object-fit:cover로 해결할 수 있다. 다만 `반응형일 경우` 부모의 width/height에 px를 줄 수 없고 %만 줘야하는데, width/height는 `서로의 기준점이 다르기 때문에 문제가 발생한다`. 그러나 padding, margin은 width와 기준점이 같기에, height을 0으로 주고 padding-bottom 100%를 주면 width값만큼 y축의 padding이 생기기때문에 정사각형이 완성된다. 이로써 wrapper의 스타일은 완성되었고, img에는 w100%, h100%, object-fit:cover, `left: 50%; position: absolute; top: 50%; transform: translate(-50%, -50%);` 를 주면 된다. position이 static일 경우에는 부모에 명시된 w/h값을 이용하여 안되고, absolute일 경우에는 부모의 실제 크기(패딩 포함)를 이용하기에 absolute를 써야한다. (`product-card.scss, product-recommendation.scss`)
- 글자가 길어질 때 "..." 처리를 할 때, 1줄일 경우 truncate (sidebar.scss), 2줄일 경우 lineClamp (product-card.scss)를 사용한다.
