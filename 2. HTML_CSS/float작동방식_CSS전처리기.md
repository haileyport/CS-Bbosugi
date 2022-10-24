# float가 어떻게 작동하는가 🔥
## float
문서의 흐름에서 제외되지만 공간은 차지한다.
부모 영역의 **왼쪽** 혹은 **오른쪽**으로 **띄움**
absolute 포지션에는 영향을 주지 않습니다.

- 기본값은 none
- left : 왼쪽에 떠있습니다
- right : 오른쪽에 떠있습니다
- none : 안 떠있습니다
- inherit : 부모의 float 값을 상속합니다

### 옛날 옛적 바다 속에 삼형제가 살았어요!
`float: none`
첫째 형 물고기와 둘째 형 게는 서로 사이가 좋지 않았답니다. 셋째는 혼자 평화로웠어요!
![image](https://user-images.githubusercontent.com/100553086/197390380-75666cc7-bf9e-435e-b40a-d175ae66b74c.png)

### 그래서 첫째와 둘째는 float 속성을 써서 서로 제일 먼 곳에 살기로 했어요
`#fish { float: left}`

`#crab { float: right}`

두 형제는 용케 찢어졌는데....
![image](https://user-images.githubusercontent.com/100553086/197390220-89967e7d-955f-4c1b-9509-ef0fd95cb108.png)

셋째가 갑자기 둘 사이에 껴버렸네요? 이런... 셋째는 별로 좋아하지 않아보이네요. 어떻게 하면 좋을까요?
![image](https://user-images.githubusercontent.com/100553086/197390799-d33f141b-29d5-4fdb-9c19-e9262afd794f.png)

## clear
- 형이 float를 받았을 때 따라올라갈지 안갈지를 지정하는 속성
- 선행 floating 요소를 해제할지 결정하는 속성

float 속성은 유용하지만 문제를 일으킬 수 있습니다! float 요소가 포함하는 경계를 넘어서 다른 부분을 방해할 수 있기 때문에 clear 속성을 통해 float 속성을 해결할 수 있습니다.
- none : 요소의 양쪽에 float 허용 (float 때문에 아래로 이동하지 않는다)
- left : 왼쪽 float를 해제하기 위해 아래로 이동한다
- right : 오른쪽 float를 해제하기 위해 아래로 이동한다
- both : 양쪽 float를 해제하기 위해 아래로 이동한다
- inherit : 부모로부터 상속
![image](https://user-images.githubusercontent.com/100553086/197390990-5c70e0ea-a1a1-4d55-9090-c256898cd512.png)

## 주황이와 파랭이로 알아보기
![image](https://user-images.githubusercontent.com/100553086/197395965-6152b505-cd19-4b88-a0be-b73aeb40d078.png)
![image](https://user-images.githubusercontent.com/100553086/197396141-4b91e0bb-695a-4d39-ab97-6b075c4ffeea.png)

# CSS 전처리기(CSS preprocessors) 🔥
CSS 전처리기는 일반 프로그래밍 언어처럼 다양한 논리 구문을 활용하여 기본 CSS 기능을 확장하는 것입니다.

👍 CSS 전처리기를 사용하면 반복 작업을 쉽게 자동화하고 오류 수와 코드 팽창을 줄이고 재사용 가능한 코드 조각을 만들고 이전 버전과의 호환성을 보장할 수 있습니다.

## 왜 CSS 전처리기를 사용해야 하나요?
1. 코드를 더 쉽게 유지할 수 있습니다.
2. CSS DRY(Don't Repeat yourself)
  - 개발자는 코드를 다시 작성하지 않도록 노력해야 함.
  - CSS 전처리기에서는 변수, mixin, extend와 같은 항목으로 DRY를 유지한다.
3. 중첩으로 조직화 할 수 있다.


## SCSS (Sassy CSS)
- 중괄호 + 세미콜론

## SASS (Syntactically Awesome Style Sheets)
- 들여쓰기 + 줄 바꿈
- $ 재사용하려는 값을 저장할 수 있다.
- mixin과 includes규칙을 사용한다.
- @if, @for, @each, @while 등으로 조건문과 반복문을 사용할 수 있다.
- @extend, @media 및 @content

### 중첩
- &로 상위 선택자 참조

### 중첩된 속성
- font- border-과 같은 비슷한 이름 스페이스를 가지는 속성 중첩 사용 가능

### SCSS와 SASS는 compile시 같은 CSS
- 차이는 
```
/* SCSS */

$primary-color: seashell;
$primary-bg: darkslategrey;

body {
  color: $primary-color;

  background: $primary-bg;

}
```

```
/* Sass */

$primary-color: seashell
$primary-bg: darkslategrey

body
  color: $primary-color
  background: $primary-bg
```

모두 같은 CSS 파일로 compile 됩니다.
```
/* Compiled CSS */

body {
  color:seashell;
  background: darkslategrey;
}
```
### mixedin과 includes 예제
```
/* SCSS */

@mixin card($width, $height, $bg, $border) {
  width: $width;

  height: $height;

  background: $bg;

  border: $border;

}
```

```
/* SCSS */
.card-1 {
  @include card(300px, 200px, yellow, red 2px solid);
}
.card-2 {
  @include card(400px, 300px, lightblue, black 1px dotted);
}
```

#### 컴파일되면 다음과 같아집니다
```
/* Compiled CSS */
.card-1 {
   width: 300px;
   height: 200px;
   background: yellow;
   border: red 2px solid;
   padding: 20px;
}
.card-2 {
   width: 400px;
   height: 300px;
   background: lightblue;
   border: black 1px dotted;
   padding: 20px;
}
```


## LESS (Leaner Style Sheets)
- 간결한 스타일
- javascript 라이브러리
- @로 변수를 초기화합니다
- &으로 중첩

### 중첩
```
.clearfix {
  display: block;
  zoom: 1;

  &:after {
    content: " ";
    display: block;
    font-size: 0;
    height: 0;
    clear: both;
    visibility: hidden;
  }
}
```

## Stylus
### 특징
- node.js에서 사용 가능
- Sass의 논리구문과 Less의 간단한 설정 같은 특징이 결합되어있음.
- 간결 & 유연
- useselect를 만들고 원하는만큼 재사용 가능함.

### Syntax
- 대괄호, 콜론 및/또는 세미콜론을 생략하거나 모든 구두점을 모두 생략 가능
- 할당 연산자(=)는 새 변수를 선언하므로 제거할 수 없다.
- 파이썬 기반 언어이므로 들여쓰기를 제대로 하지 않으면 컴파일되지 않는다.
```
/* Stylus syntax without punctuation */

primary-color = seashell
primary-bg = darkslategrey

body
  color primary-color
  background primary-bg
```

---
# 참고자료
- https://developer.mozilla.org/en-US/docs/Web/CSS/float
- https://www.youtube.com/watch?v=JP_I3hz55hk
- https://www.w3schools.com/cssref/pr_class_float.asp
- https://www.w3schools.com/css/css_float.asp
- https://blog.hubspot.com/website/css-float
---
- https://developer.mozilla.org/en-US/docs/Glossary/CSS_preprocessor
- https://raygun.com/blog/css-preprocessors-examples/
- https://sherocommerce.com/what-is-a-css-preprocessors-why-use-them/
- https://medium.com/@sedwardscode/css-preprocessors-what-why-how-7bc5a7a564de
- https://www.geeksforgeeks.org/css-preprocessor-less/
---
- https://sass-lang.com/guide
- https://lesscss.org/
- https://stylus-lang.com/docs/executable.html
