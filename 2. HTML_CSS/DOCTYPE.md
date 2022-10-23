# DOCTYPE

문서 형식 선언(Document Type Declaration, DTD)
브라우저가 문서를 렌더링할 때 [quirks mode](https://developer.mozilla.org/ko/docs/Web/HTML/Quirks_Mode_and_Standards_Mode)로 바뀌지 않도록 하는 것을 가장 큰 목적으로 합니다.

- 호환 모드(quirks mode): 기존 방식으로 제작된 웹사이트들을 표현하기 위해 내비게이터 4(Navigator 4)와 인터넷 익스플로러 5의 비표준 동작들을 에뮬레이션한다.
- 완전 표준 모드(표준모드) : HTML과 CSS에 의해 웹 페이지가 표시된다.

`<!DOCTYPE html>` : HTML 태그는 아니지만, 선언된 페이지의 HTML 버전이 무엇인지 웹 브라우저에 알려주는 역할을 하는 선언문

오늘날 *현존하는 모든 브라우저들이 완전표준모드로 렌더링하는 것이 권장*된다. 만약 다른 DOCTYPE을 사용하게 된다면, 페이지가 일부 표준 모드나 호환모드로 렌더링 될 위험이 있다.

##### 문서 형식을 선언하는 이유?

자바스크립트도 그렇듯 HTML 또한 버전마다 적용되는 태그와 그렇지 않은 태그가 있다. 구버전에서 신버전의 HTML을 사용한다면, 웹 브라우저에서 문법 오류로 간주될 것이다. 선언을 통해 이 문법을 알맞게 검사하도록 지시한다.

##### 참고

HTML의 버전별로 DOCTYPE을 쓰는 방법이 다르다.
`<!DOCTYPE html>` 은 HTML5에서 사용하는 방법이고, 4.01에서는 세 가지 방법이 있다.

# meta tag

HTML의 <meta> 요소는 `<base>, <link>, <script>, <style>, <title>`과 같이 다른 메타관련 요소로 나타낼 수 없는 메타데이터를 나타냅니다.

##### 메타데이터?

- 데이터를 설명하는 데이터

### 메타 속성

1. `name` : meta 정보의 이름을 지정할 수 있습니다. 지정하지 않으면 http-equiv와 같은 기능을 합니다.

- `http-equiv` : 웹 브라우저가 서버에 명령을 내리는 속성입니다. name 대신 사용할 수 있고, HTML 문서가 응답 헤더와 함께 웹 서버로부터 웹 브라우저에 전송되었을 때에만 의미를 갖습니다.
- `content` : meta 정보의 내용을 지정합니다.

### 메타 태그 종류

- 검색엔진에 의해 검색되는 단어를 지정
  `<meta name="Keywords" content="Web, html, 웹 표준" />`

- 검색 결과에 표시되는 문자 지정
  `<meta name="Description" content="Web, html, 웹 표준" />`

- 검색 로봇 제어
  `<meta name="Robots" content="noindex, nofollow" />`

- 문자 코드의 종류 설정
  `<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />`

- 날짜(제작일)
  `<meta name="Date" content="2016-02-15T07:45:37+09:00" />`

- 웹 페이지에 쓰인 언어 지정
  `<meta http-equiv="Content-Script-Type" content="text/javascript" />`
  `<meta http-equiv="Content-Style-Type" content="text/css" />`

- 브라우저 호환성 지정
  `<meta http-equiv="X-UA-Compatible" content="IE=edge" />`

- 홈페이지 주제 지정
  `<meta http-equiv="Subject" content="웹 표준을 위한 사이트" />`

- 제목 지정
  `<meta http-equiv="Title" content="웹 표준" />`

이외에도 더 많은 meta 요소가 있으니 ref에 작성된 메타태그 종류를 참고해주세요!

---

[DOCTYPE](https://developer.mozilla.org/ko/docs/Glossary/Doctype)
<br/>
[DOCTYPE2](https://developer.mozilla.org/ko/docs/Web/HTML/Quirks_Mode_and_Standards_Mode)
<br/>
[meta](https://developer.mozilla.org/ko/docs/Web/HTML/Element/meta)
<br/>
[메타태그 종류](https://webclub.tistory.com/354)
