## CSS IN JS는 무엇인가요?

!()[https://postfiles.pstatic.net/MjAyMjEwMjRfMTAx/MDAxNjY2NTc4OTIzOTk0.IH7cQtyQ12hKKm6hzk7DGHm6cerOOBkYf2gTQ3tUcikg.scFXdQ4YFB9ppOiK2V2BTGVAnbxme4GRJjOIABwsPvog.PNG.dsilver0818/image.png?type=w966]

1996년 CSS가 발표된 이후, 웹이 점점 복잡해지고 동적 기능 요구가 증가하면서 HTML과 CSS만으로는 화면의 모든 스타일을 제어할 수 없는 상황에 이르게 됨.
이를 해결하기 위한 여러 가지 웹 애플리케이션 스타일 구성 방식이 나타났다

- CSS-in-CSS
- CSS-in-JS

</br>

### CSS IN CSS

!()[https://www.javascriptstuff.com/static/css-modules-diagram-incomplete-f2ff456c36a0f2ca41509827cc937eb2-f7c8c.png]

CSS 모듈은 CSS를 모듈화 하여 사용하는 방식
CSS 클래스를 만들면 자동으로 고유한 클래스네임을 만들어서 scope를 지역적으로 제한
모듈화된 CSS를 번들러로 불러오면 위와 같이 사용자가 정의했던 클래스네임과 고유한 클래스네임으로 이뤄진 객체가 반환

### CSS IN JS

**CSS-in-JS는 단어 그대로 자바스크립트 코드에서 CSS를 작성하는 방식**
**JavaScript 를 사용하여 구성 요소의 스타일 을 지정하는 스타일링 기술**

2014년 페이스북 개발자인 Christopher Chedeau aka Vjeux가 처음 소개하였다

Vjeux는 CSS를 작성하는 어려움을 다음과 같이 설명하였으며 CSS-in-JS로 이들 이슈를 모두 해결할 수 있다고 강조했습니다.

- Global namespace: 글로벌 공간에 선언된 이름의 명명 규칙 필요
- Dependencies: CSS간의 의존 관계를 관리
- Dead Code Elimination: 미사용 코드 검출
- Minification: 클래스 이름의 최소화
- Sharing Constants: JS와 CSS의 상태 공유
- Non-deterministic Resolution: CSS 로드 우선 순위 이슈
- Isolation: CSS와 JS의 상속에 따른 격리 필요 이슈

이러한 어려움을 해결한 사례로 페이스북의 예시를 들었습니다

그 이후, 저희가 처음 본 그래프처럼 수많은 CSS 라이브러리들이 등장했습니다.
이 중 가장 대표적인 것은 Styled Components 이기에, 이 CSS IN JS가 진짜 Christopher의 말처럼 좋은지 살펴보겠습니다

### CSS IN JS vs. CSS IN CSS

!()[https://image.samsungsds.com/kr/insights/web_component_img05.jpg?queryString=20221013055322]

!()[https://image.samsungsds.com/kr/insights/web_component_img06.jpg?queryString=20221013055322]

**CSS in JS의 장점**

- CSS 모델을 문서 레벨이 아닌 컴포넌트 레벨로 추상화하는 모듈성
- CSS-in-JS는 JavaScript 환경을 최대한 활용
- 자바스크립트와 CSS 사이의 상수와 함수를 공유
- 현재 사용 중인 스타일만 DOM에 포함
- 짧은 길이의 유니크 한 클래스를 자동으로 생성하는 코드 경량화

  **CSS in JS 단점**

- 러닝 커브(Learning Curve), 새로운 의존성 발생
- 별도의 라이브러리 설치에 따른 번들 크기 증대
- CSS-in-CSS에 비해 느린 속도, CSS in CSS는 JS 해석 과정이 없기 때문에 페이지 전환이 빠르다

### 마치며

!()[https://image.samsungsds.com/kr/insights/web_component_img09.jpg?queryString=20221013055322]

"CSS는 CSS에 작성하고 끝내세요."

그렇지만 현대 웹은 다릅니다. 현대 웹은 페이지가 아니라 컴포넌트 별로 작성이 되어 있습니다.
CSS는 컴포넌트 기반을 위해 만들어진 것이 아니기 때문에, CSS in JS가 만들어진 것입니다.

_JSS는 CSS보다 더 강력한 추상화입니다. JavaScript를 사용하여 스타일을 선언적이고, 유지보수 가능한 방식으로 설명합니다. JS를 CSS로 전환하는 고성능 컴파일러로, 런타임 및 서버 사이드에서 작동합니다. 이 코어 라이브러리는 낮은 레벨이며, 프레임워크에 구애받지 않습니다. 약 6KB(gzip압축과 minify함)이며 플러그인 API를 통해 확장 가능합니다._
(by https://cssinjs.org/?v=v10.9.2)
</br>

이 발표는 CSS in CSS는 이제 버리라는 것이 아닙니다. CSS in JS가 필요하게 된 경위와 지금 널리 쓰이게 된 배경을 다시 한 번 살펴보면, 현대에서의 웹에서의 효율이 더 좋기 때문에 나타난 것이란걸 말하고 싶었습니다. 여러분들이 만드는 홈페이지가 사용자의 편의가 더 중요한지, 아니면 개발에서의 효율성이 중요하고 컴포넌트 별로 구별이 지어지는지에 따라 선택을 하시기를 요합니다.

### 출처

https://www.samsungsds.com/kr/insights/web_component.html
</br>
https://d0gf00t.tistory.com/22
</br>
https://medium.com/object-partners/css-in-js-benefits-drawback-and-tooling-80286b03f9aa
</br>
https://hackernoon.com/all-you-need-to-know-about-css-in-js-984a72d48ebc
