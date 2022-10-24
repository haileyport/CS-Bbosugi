## CSS IN JS

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

참고 : 오은님의 발표

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

일반적으로 CSS in css보다 css in js는 더 높은 퍼포먼스를 보이고 있습니다.

!()[https://image.samsungsds.com/kr/insights/web_component_img09.jpg?queryString=20221013055322]

https://www.samsungsds.com/kr/insights/web_component.html
