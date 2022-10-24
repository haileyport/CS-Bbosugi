<!-- 담당: 세린님 -->
# Position

## Position이란?
**문서상에 요소를 원하는 위치에 배치하기 위해서 사용하는 CSS 속성**

+ 대부분 요소의 정확한 위치를 지정하기 위해서 `top` `left` `bottom` `right` 속성과 함께 사용됩니다. (static 제외)
+ position 속성을 별도로 지정해주지 않으면, 기본값인 **static** 이 적용됩니다.

### position: static;
+ 요소가 겹치지 않고 문서의 흐름에 맞추어(상->하) 배치됩니다. (기본값!!)
+  `top`, `right`, `bottom`, `left`, `z-index` 속성은 효과가 없습니다. (float 속성은 가능!)

### position: relative;
+ 부모 요소 내에서 원래 있어야 할 위치를 기준으로 자신의 위치를 지정합니다.
+ (부모 요소의 padding 값도 적용함)
+ `top`, `right`, `bottom`, `left` 속성을 써서 요소의 지정할 수 있습니다.

### position: absolute;
+ 가장 가까운 상위 요소의 위치를 기준으로 자신의 위치를 지정합니다.
+ (`relative`와 달리 부모 요소의 padding 값 고려하지 않음)

```HTML
<div class='parent'>
  <div class='box static'>position: static</div>
  <div class='box relative'>position: relative</div>
  <div class='box absolute'>position: absolute</div>
</div>
```
```CSS
.static{
  position: static;
  left: 80px;
}
.relative{
  position: relative;
  left: 80px;
}
.absolute{
  position: absolute;
  left: 80px;
}
```
![relative/absolute 비교](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbDtsLQ%2FbtrPsNqPPP8%2FAQkCKsoqsz1JhqgNUmT3xK%2Fimg.jpg)

### position: fixed;
+ 웹브라우저 전체 화면을 기준으로 지정한 위치에 고정하여 배치됩니다. 
+ 프린트되는 모든 페이지에서 동일한 위치에 배치됩니다.(스크롤이 움직여도 동일한 위치에 고정됩니다.)

### position: sticky;
+ 위치에 따라서 동작방식이 달라집니다. 요소가 임계점(scroll 박스 기준) 이전에는 `relative`와 같이 동작하고, 그 이후에는 `fixed`와 같이 동작합니다.
- 고정 요소는 "scrolling mechanism"이 있는 가장 가까운 상위에 ( overflowis hidden, scroll, auto또는 인 경우 생성됨 overlay)에 "고정"된다는 점에 유의하세요.해당 조상이 가장 가까운 실제로 스크롤하는 조상이 아니더라도 마찬가지입니다.

## 성능 및 접근성

`fixed`또는 `sticky`는 성능 및 접근성 문제를 유발할 수 있습니다. 브라우저는 사용자가 스크롤할 때마다 고정된 콘텐츠를 새 위치에 다시 그려야 합니다. 표시해야 되는 내용의 양, 브라우저 및 기기의 성능에 따라 60 fps를 유지하지 못하는 일부 민감한 사용자에게는 접근성 문제가, 다른 모두에게는 버벅임으로 인한 사용자 경험 악화가 생깁니다. 한 가지 해결책은 `will-change: transform`를 추가하여 요소를 자신만의 레이어에서 렌더링 하여 페인트 속도를 향상하고, 나아가 성능과 접근성을 높일 수 있습니다.

---
Bonus! (함께 알면 좋은 내용) <br/>
#### z-index
+ 위치 지정 요소와, 그 자손 또는 하위 아이템의 Z축 순서를 지정합니다. 
+ 더 큰 z-index 값을 가진 요소가 작은 값의 요소 위를 덮습니다. (z-index값이 클수록 위에 배치됩니다!)

---
Reference <br/>
- [position_MDN](https://developer.mozilla.org/ko/docs/Web/CSS/position)
- [z-index_MDN](https://developer.mozilla.org/ko/docs/Web/CSS/z-index)