# Flex
정식 명칭은 Flexible Box module이지만 Flex, Flexible Box, Flexbox 라고 부르기도 합니다. Flex는 flexbox 인터페이스 내의 아이템 간 **공간 배분**  과 **강력한 정렬 기능**을 제공하기 위해 1차원 레이아웃 모델로 설계 되었습니다.

flex를 1차원이라 칭하는 것은, 레이아웃을 다룰 때 한 번에 하나의 차원(행이나 열)만을 다룬다는 의미입니다.


## Flex는 두 개의 축으로 다룹니다.
![](https://velog.velcdn.com/images/heojeong_/post/6d734252-3e28-42a8-8149-f4cf01e1c63a/image.png)

먼저, 주축과 교차축이라는 두 개의 축에 대한 정의를 알아보겠습니다.
flex를 잘 다루기 위해선 이 두 개의 축이 어떻게 동작하는지 처음부터 이해하는 것이 중요합니다.


### 주축
주축은 `flex-direction` 속성에 의해 지정되며 4개의 값을 가질 수 있습니다.
- `row`
- `row-reverse`
- `column`
- `column-reverse`

`row` 혹은 `row-reverse`를 부여하면 주축은 **인라인 방향**으로 행을 따르게 됩니다.
`column` 혹은 `column-reverse`을 부여하면 주축은 페이지 상단에서 하단으로 **블록 방향**을 따릅니다.

### 교차축
교차축은 **주축의 수직으로 지정**됩니다. 만약 주축이 `row` 혹은 `row-reverse` 라면 교차축은 **열 방향**을 따르게 됩니다.

주축이 `column` 혹은 `column-reverse` 라면 교차축은 **행 방향**을 따르게 됩니다.

위에서 flex는 강력한 정렬 기능을 제공한다고 말씀드렸습니다. flex로 아이템들을 정렬하고 끝을 맞추려면(justify) 어느 축이 어느 방향인지 이해하는 것이 중요합니다.

flex는 주측, 교차축을 따라 항목을 정렬하고 끝을 맞추는 각종 속성들을 적용하는 방식으로 동작합니다.
![](https://velog.velcdn.com/images/heojeong_/post/64c2dae4-2d88-463e-800b-9066465dbf56/image.png)

### 시작점과 끝점
flex에는 시작점(flex-start)과 끝점(flex-end)이라는 개념이 존재합니다.
이는 **두 축의 시작하는 지점과 끝나는 지점**을 말하며 방향에 따라 시작점과 끝점이 달라집니다.
![](https://velog.velcdn.com/images/heojeong_/post/29bcd735-e26c-4f0c-8933-730380801a32/image.png)

### 줄 바꿈
기본적으로 아이템은 한 줄로만 표시되고 줄 바꿈 되지 않습니다.
따라서 아이템을 줄 바꿈 하려면 `flex-wrap` 속성을 사용하여야 합니다.
#### flex-wrap 속성 값
|값|설명|
|--|--|
| nowrap | 모든 Item을 한 줄에 표시 |
|wrap|Items을 여러 줄로 묶음|
| wrap-revers |여러 줄로, wrap의 반대방향으로 묶음 |
![](https://velog.velcdn.com/images/heojeong_/post/f9d9af04-15a3-48ef-b03c-ac7997319d69/image.png)

## 정렬
### 주축의 정렬 방법
주축은 `justify-content` 속성을 사용하여 정렬 방법을 지정합니다.
#### justify-content 속성 값
|값|설명|
|--|--|
| flex-start | Items를 시작점(flex-start)으로 정렬 |
|flex-end|Items를 끝점(flex-end)으로 정렬|
|**center** |Items를 가운데 정렬 |
| space-between |시작 Item은 시작점에, 마지막 Item은 끝점에 정렬되고 나머지 Items는 사이에 고르게 정렬됨|
| space-around |Items를 균등한 여백을 포함하여 정렬됨 |
![](https://velog.velcdn.com/images/heojeong_/post/a5c5afa8-d79d-4b0e-a2ca-6f9292cf2815/image.png)

### 교차축의 정렬 방법

교차축은 상황에 따라 `align-content` 속성과, `align-items` 속성을 통해 정렬 방법을 지정합니다.
#### align-content 정렬
![](https://velog.velcdn.com/images/heojeong_/post/3862047f-fbe5-4a50-b42e-c4fac7453592/image.png)
#### align-itmes 정렬
![](https://velog.velcdn.com/images/heojeong_/post/ccdd8fd7-4390-4d46-9c0b-c5d75e7cbf20/image.png)


# CSS Grid
Grid는 2차원의 레이아웃 시스템을 제공합니다.
위에서 배운 1차원 레이아웃 시스템인 flex도 훌룡하지만, 조금 더 복잡한 레이아웃을 위해 Grid를 사용할 수 있습니다.

## Grid Properties
Grid는 Flex와 같이 Container와 Item이라는 두 가지 개념으로 구분되어 있습니다.
Container는 Item을 감싸는 부모 요소이며, 그 안에서 각 Item을 배치할 수 있습니다.

### Grid Container Properties
Gird Container를 위한 속성은 다음과 같습니다.

<table style="user-select: auto;"><thead style="user-select: auto;"><tr style="user-select: auto;"><th style="user-select: auto;">속성</th><th style="user-select: auto;">의미</th></tr></thead><tbody style="user-select: auto;"><tr style="user-select: auto;"><td style="user-select: auto;">display</td><td style="user-select: auto;">그리드 컨테이너(Container)를 정의</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">grid-template-rows</td><td style="user-select: auto;">명시적 행(Track)의 크기를 정의</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">grid-template-columns</td><td style="user-select: auto;">명시적 열(Track)의 크기를 정의</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">grid-template-areas</td><td style="user-select: auto;">영역(Area) 이름을 참조해 템플릿 생성</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">grid-template</td><td style="user-select: auto;"><code style="user-select: auto;">grid-template-xxx</code>의 단축 속성</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">row-gap(grid-row-gap)</td><td style="user-select: auto;">행과 행 사이의 간격(Line)을 정의</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">column-gap(grid-column-gap)</td><td style="user-select: auto;">열과 열 사이의 간격(Line)을 정의</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">gap(grid-gap)</td><td style="user-select: auto;"><code style="user-select: auto;">xxx-gap</code>의 단축 속성</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">grid-auto-rows</td><td style="user-select: auto;">암시적인 행(Track)의 크기를 정의</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">grid-auto-columns</td><td style="user-select: auto;">암시적인 열(Track)의 크기를 정의</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">grid-auto-flow</td><td style="user-select: auto;">자동 배치 알고리즘 방식을 정의</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">grid</td><td style="user-select: auto;"><code style="user-select: auto;">grid-template-xxx</code>과 <code style="user-select: auto;">grid-auto-xxx</code>의 단축 속성</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">align-content</td><td style="user-select: auto;">그리드 콘텐츠(Grid Contents)를 수직(열 축) 정렬</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">justify-content</td><td style="user-select: auto;">그리드 콘텐츠를 수평(행 축) 정렬</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">place-content</td><td style="user-select: auto;"><code style="user-select: auto;">align-content</code>와 <code style="user-select: auto;">justify-content</code>의 단축 속성</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">align-items</td><td style="user-select: auto;">그리드 아이템(Items)들을 수직(열 축) 정렬</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">justify-items</td><td style="user-select: auto;">그리드 아이템들을 수평(행 축) 정렬</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">place-items</td><td style="user-select: auto;"><code style="user-select: auto;">align-items</code>와 <code style="user-select: auto;">justify-items</code>의 단축 속성</td></tr></tbody></table>

#### Grid Item Properties
Grid Item을 위한 속성들은 다음과 같습니다.
<table style="user-select: auto;"><thead style="user-select: auto;"><tr style="user-select: auto;"><th style="user-select: auto;">속성</th><th style="user-select: auto;">의미</th></tr></thead><tbody style="user-select: auto;"><tr style="user-select: auto;"><td style="user-select: auto;">grid-row-start</td><td style="user-select: auto;">그리드 아이템(Item)의 행 시작 위치 지정</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">grid-row-end</td><td style="user-select: auto;">그리드 아이템의 행 끝 위치 지정</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">grid-row</td><td style="user-select: auto;"><code style="user-select: auto;">grid-row-xxx</code>의 단축 속성(행 시작/끝 위치)</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">grid-column-start</td><td style="user-select: auto;">그리드 아이템의 열 시작 위치 지정</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">grid-column-end</td><td style="user-select: auto;">그리드 아이템의 열 끝 위치 지정</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">grid-column</td><td style="user-select: auto;"><code style="user-select: auto;">grid-column-xxx</code>의 단축 속성(열 시작/끝 위치)</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">grid-area</td><td style="user-select: auto;">영역(Area) 이름을 설정하거나, <code style="user-select: auto;">grid-row</code>와 <code style="user-select: auto;">grid-column</code>의 단축 속성</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">align-self</td><td style="user-select: auto;">단일 그리드 아이템을 수직(열 축) 정렬</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">justify-self</td><td style="user-select: auto;">단일 그리드 아이템을 수평(행 축) 정렬</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">place-self</td><td style="user-select: auto;"><code style="user-select: auto;">align-self</code>와 <code style="user-select: auto;">justify-self</code>의 단축 속성</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">order</td><td style="user-select: auto;">그리드 아이템의 배치 순서를 지정</td></tr><tr style="user-select: auto;"><td style="user-select: auto;">z-index</td><td style="user-select: auto;">그리드 아이템의 쌓이는 순서를 지정</td></tr></tbody></table>

### Grid 예시
```css
.container {
  display: grid;
  grid-template-rows: repeat(3, 100px);
  grid-template-columns: repeat(3, 1fr);
  grid-template-areas:
    "header header header"
    "main main aside"
    "footer footer footer";
}
header { grid-area: header; }
main   { grid-area: main;   }
aside  { grid-area: aside;  }
footer { grid-area: footer; }
```
![](https://velog.velcdn.com/images/heojeong_/post/534cef43-39b7-47ee-8c48-5299250d07ca/image.png)




# 그럼 언제 Flex와 Grid를 사용하나요?
> “플랙스박스는 좀 더 콘텐츠에 초점이 맞춰져 있습니다. 플랙스박스의 이상적인 사용 사례는 여러 아이템을 컨테이너에 고르게 배치하려는 경우입니다. 여기서 콘텐츠의 크기가 각 아이템이 차지하는 공간을 결정합니다. 아이템이 새로운 줄로 줄 바꿈 되면, 아이템의 크기와 해당 줄의 사용 가능한 공간에 따라 간격이 조정됩니다.
그리드는 레이아웃을 먼저 고려하게 됩니다. CSS 그리드 레이아웃을 사용할 때는 우선 레이아웃을 작성한 다음 그 위에 아이템을 배치하거나, 자동 배치 규칙을 통해 견고하게 짜인 그리드 위에 놓인 그리드 셀에 아이템을 배치하게 됩니다.” -MDM

위의 말을 한마디로 정리를 해보자면, flex는 콘텐츠 위주의 정렬에 적합하고, grid는 레이아웃 위주의 정렬에 적합합니다.

---
Reference. </br>
[MDN](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox) </br>
[heropy's blog](https://heropy.blog/) </br>
[flex와 grid 차이점](https://www.rory-dev.com/css/flex-vs-grid/)
