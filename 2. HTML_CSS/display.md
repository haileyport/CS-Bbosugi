## 📚 Display

<br/>

### display 속성이란 ?

- 요소의 내부와 외부 디스플레이 유형을 설정하는 속성
  - 외부 디스플레이 유형으로는 요소를 화면에 어떻게 드러나게 할 것인지(block or Inline)에 대한 방법을 나타내며,
    내부 디스플레이 유형으로는 자식의 레이아웃 방식(flow, flex, grid)을 설정한다.

<br/>

### display 사용하기

- `display` 키워드 값을 이용해 디스플레이를 지정한다.

```jsx
.container {
	display : <display-keyword>;
}
```

<br/>

### Display 속성 분류하기

<details markdown="1">
<summary>display 유형은 6가지로 분류가능하다 </summary>

- 외부 디스플레이 유형
- 내부 디스플레이 유형
- 리스트 항목
- 내부용
- 박스
- 레거시

</details>

<br/>

### ☝️ 외부 디스플레이 유형(display-outside)

- 요소의 외부 디스플레이 유형을 설정하는 키워드로, 플로우 레이아웃에서 요소 자신의 역할과 같다.

  1️⃣ `display : block;`

  - 흐름에따라 위치한 라인 전체를 차지하고자 하는 성질을 가지는 속성
  - width 속성을 부여해주면 너비만큼 그 영역을 차지한다.
    ![block level elements](https://velog.velcdn.com/images/rachelyu1025/post/0b309cf4-6913-4371-bd96-3a0301e7aa12/image.png)

  2️⃣ `display : inline;`

  - 컨텐츠 만큼의 크기만 차지하는 성질을 가진 속성으로, 요소의 다음 요소는 차지할 수 있는 공간이 있는한 같은 라인에 위치한다.
  - width, height, margin-top,margin-bottom 속성이 적용되지 않는다.
    ![inline level elements](https://velog.velcdn.com/images/rachelyu1025/post/4a08e17b-82c3-46c8-97be-c509077ac36b/image.png)

💡 유형의 두 값을 지원하는 브라우저는 키워드가 block, inline으로 지정 되었을 때, 내부 요소들이 플로우 레이아웃에 속하도록 설정합니다.즉, 어떤 요소를 블록으로 지정하면, 해당 요소의 자식이 플로우 레이아웃에 참여하는 것으로 간주한다.

<br/>

### ✌️ 내부 디스플레이 유형(display-inside)

- 요소의 내부 디스플레이 유형을 설정하는 키워드로, 대체 요소가 아닌 요소의 컨텐츠 서식(formatting context)과 배치 방법을 나타낸다.

💡 컨텐츠 서식이란? https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Flow_Layout/Intro_to_formatting_contexts

<br/>

1️⃣ flow

⇒ 외부 디스플레이 유형이 inline 또는 run-in 일 경우, 요소의 서식이 block 또는 inline 이라면 inline box를 생성하며 이외의 경우, block box를 생성한다.

다른 속성(position, float, overflow 등..)의 값과 요소 자체가 block 또는 Inline 인지에 따라 새 block formatting context(BFC)를 설정하거나 콘텐츠를 상위 서식에 통합한다.

💡 BFC(Blcok Formatting Context)가 뭐죠?

- 웹페이지에 나타나있는 block들이 보여지는 CSS 렌더링의 일부

- 요소에 BFC를 적용하면 하위 요소를 대상으로 한 독립적인 레이아웃 환경을 만들 수 있고 다른 주변 요소와도 레이아웃 관계를 형성할 수 있다.

  ⇒ block의 속성이 다시 부여되어 다르게 렌더링 되는 현상 또는 컨텐츠로 block 컨텐츠의 서식 모델을 의미한다.

<details markdown="2">
  <summary> BFC 조건 (하나라도 포함하는 요소들은 모두 BFC라고 할 수 있다.) </summary>

- 문서의 루트 요소(`<html>`)일 때

- 플로팅(Floating) 되었을 때 ⇒ float이 none이 아닌 경우

- [position](https://developer.mozilla.org/ko/docs/Web/CSS/position) 속성이 absolute 또는 fixed로 적용된 경우

- [display](https://developer.mozilla.org/ko/docs/Web/CSS/display)가 inline-block으로 적용된 경우

- [display](https://developer.mozilla.org/ko/docs/Web/CSS/display)가 table-cell, HTML 표 칸의 기본값인 경우

- [display](https://developer.mozilla.org/ko/docs/Web/CSS/display)가 table-caption, HTML 표 주석의 기본값인 경우

- [display](https://developer.mozilla.org/ko/docs/Web/CSS/display)가 table, table-row, table-row-group, table-header-group, table-footer-group (HTML 표에서, 각각 표 전체, 행, 본문, 헤더, 푸터의 기본값) 또는 inline-table인 요소가 암시적으로 생성한 무명 칸.

- [overflow](https://developer.mozilla.org/ko/docs/Web/CSS/overflow)가 visible이 아닌 블록 요소인 경우

- [display](https://developer.mozilla.org/ko/docs/Web/CSS/display)가 flow-root.

- [contain](https://developer.mozilla.org/ko/docs/Web/CSS/contain)이 layout, content, paint.

- 스스로 플렉스, 그리드, 테이블 컨테이너가 아닌 경우의 플렉스 항목([display](https://developer.mozilla.org/ko/docs/Web/CSS/display)가 flex 또는 inline-flex인 요소의 바로 아래 자식)

- 스스로 플렉스, 그리드, 테이블 컨테이너가 아닌 경우의 그리드 항목([display](https://developer.mozilla.org/ko/docs/Web/CSS/display)가 grid 또는 inline-grid인 요소의 바로 아래 자식)

- 다열 컨테이너([column-count](https://developer.mozilla.org/ko/docs/Web/CSS/column-count) 또는 ([column-width](https://developer.mozilla.org/ko/docs/Web/CSS/column-width)가 auto가 아닌 경우. column-count: 1 포함).

- [column-span](https://developer.mozilla.org/ko/docs/Web/CSS/column-span)이 all인 경우. 해당하는 요소가 다열 컨테이너 안에 위치하지 않아도 항상 새로운 블록 서식 맥락을 생성해야 합니다.

</details>

<br/>

2️⃣ flow-root

⇒ 요소는 서식 루트가 있는 위치를 정의하는 새 BFC를 설정하는 block box를 생성한다.

3️⃣ table

⇒ HTML 요소(`<table>`) 처럼 작동하며, block 레벨이다.

4️⃣ flex

⇒ block 요소 처럼 작동하며, flexbox model에 따라 배치된다.

5️⃣ grid

⇒ block 요소 처럼 작동하며, grid moedel에 따라 배치된다.

💡 display: flex 또는 display: grid 가 지정된 경우와 같이 내부 값만을 찾을 때, 요소들의 외부 디스플레이 유형은 block이 되기 때문에 flex 또는 grid 컨테이너에 생성된 box 들이 block level을 가질 것을 예상할 수 있다.

6️⃣ ruby

⇒ inline 요소 처럼 작동하며, ruby formatting model에 따라 배치된다.

HTML 요소(`<ruby>`) 처럼 작동한다.

![ruby 속성](https://velog.velcdn.com/images/rachelyu1025/post/7b4eb34b-3dc5-45f1-95fe-da3178978a1a/image.png)

<br/>

### 🤟 박스 (`<display-box>`)

- 요소가 디스플레이 박스를 생성해야 하는지를 설정

  1️⃣ contents
  ⇒ 요소 자체 박스를 생성하지 않고, 요소의 자식들이 생성한 박스로 대체한다.

  2️⃣ none
  ⇒ 요소가 레이아웃에 영향을 주지 못하도록 설정한다(= 요소가 아예 존재하지 않는 것처럼 렌더링)
  `display : none;` 요소의 모든 자손 요소도 보이지 않다.

  💡 요소가 보이지 않아야하지만, 레이아웃에 참여해 자신의 공간은 차지해야한다면?

  => `visibility: visible | hidden | collapse` 속성을 이용할 수 있다.

<br/>

### 💡 레거시 (`display : inline-block` )

- 요소가 block level의 box를 생성하지만, 마치 하나의 인라인 박스처럼 주변 컨텐츠와 함께 flow 레이아웃의 흐름에 참여한다. (inline flow-root와 같다.)

  => 쉽게 inline 속성과 block 속성이 합쳐진 속성으로 이해할 수 있다.

- 기본적으로는 inline 속성을 지니지만, 임의로 크기를 바꿔줄 수 있다.

<br/>

✨ Reference

- [MDN Display](https://developer.mozilla.org/ko/docs/Web/CSS/display)

- [CSS display 유형 ](https://sorto.me/docs/Web/CSS/display)
- [BFC](http://www.devdic.com/css/reference/documents/document:1971/%EB%B8%94%EB%A1%9D-%EC%96%91%EC%8B%9D%ED%99%94-%EB%AC%B8%EB%A7%A5)
- [css ruby](https://www.w3.org/TR/css-ruby-1/#ruby-def)
