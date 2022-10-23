### UI/UX

다들 유어클래스에서도 배웠으니 간단하게만 말씀드리면

UI는 모니터 화면 뿐만 아니라 핸드폰,마우스 등의 물리적인 요소들과 사람 간의 상호 작용하는 시스템입니다. 그래서 UI를 User `Interface`라고 하는 것입니다.

제가 예전에 만들었던 계산기 목업..

<div align='center'><img src='https://camo.githubusercontent.com/9aba5087ef310d968fc0eb52c353458211e23524c10a5bb581b8d5515949a6ad/68747470733a2f2f76656c6f672e76656c63646e2e636f6d2f696d616765732f676b746d643635322f706f73742f35643932303630312d386236392d343931332d626164652d3161393961393330626231352f696d6167652e706e67' />
<img src='https://freefrontend.com/assets/img/css-calculators/2021-calculator-pure-css.png' /></div>

사용자가 한 눈에 보고 숫자가 들어간 동그라미 모양을 버튼이라고 인식할 수 있을까요?

반면에 UX는 내가 누른 숫자가 정상적으로 화면에 나오고 연산 등으 기능들이 제대로 동작만 한다면 그나마 낫겠죠?

그렇기 때문에 UI가 별로라고 해서 UX가 안좋다고 할 수도 없을 뿐더러 그 반대의 경우도 마찬가지입니다.(좋은 UX가 좋은 UI를 보장하지도 않음)

### SVG

~~이것도 유어클래스에 짧게 나왔지만~~ Scalable Vector Graphic의 약자로, 한마디로 벡터 그래픽입니다.

### 벡터 그래픽이란?

선이나 모양을 배치할 때 수학적인 형태로 그려진 것을 말합니다.

일반 래스터 이미지와는 달리 확대해도 잘 깨지지 않고 용량이 상대적으로 작다는 장점이 있습니다.

### 그럼 용량이 왜 작은가요?

svg 같은 벡터 그래픽은 선을 그리기 위한 비트가 저장되어 있는 대신에 연결될 **점**의 위치가 들어있기 때문에 그렇습니다.

<img src="https://ipx-cdn.lottiefiles.com/-YbZEr4f0G51dJTq4_5oW_Z3XA0ePCxZfAiTwmmqBVk/fill/1600/1000/no/0/aHR0cHM6Ly9kM2psNzY5b3k2OXk3Yi5jbG91ZGZyb250Lm5ldC8yMDIyLzA4L1Jhc3Rlci12cy1WZWN0b3IucG5n.jpg" />

```js
var NAMESPACE_IDENTIFIER = "___FONT_AWESOME___";
var UNITS_IN_GRID = 16;
var DEFAULT_CSS_PREFIX = "fa";
var DEFAULT_REPLACEMENT_CLASS = "svg-inline--fa";
var DATA_FA_I2SVG = "data-fa-i2svg";
var DATA_FA_PSEUDO_ELEMENT = "data-fa-pseudo-element";
var DATA_FA_PSEUDO_ELEMENT_PENDING = "data-fa-pseudo-element-pending";
var DATA_PREFIX = "data-prefix";
var DATA_ICON = "data-icon";
var HTML_CLASS_I2SVG_BASE_CLASS = "fontawesome-i2svg";
```

<small><p align='center'><strong>https://github.com/FortAwesome/Font-Awesome/blob/6.x/js-packages/%40fortawesome/fontawesome-free/js/fontawesome.js#L265-L274</strong></p></small>

일부만 가져왔지만 svg가 곳곳에 쓰여져 있는 것을 알 수 있습니다.(css 파일 등)

레퍼런스에는 XML 포맷으로 파일이 작성되기 때문에 JS나 CSS로 조작이 가능하다고 나와있는데.... 진짜 그런지 찾아봤습니다.

```js
<?xml version="1.0" encoding="UTF-8"?>
<!--!
Font Awesome Free 6.2.0 by @fontawesome - https://fontawesome.com
License - https://fontawesome.com/license/free (Icons: CC BY 4.0, Fonts: SIL OFL 1.1, Code: MIT License)
Copyright 2022 Fonticons, Inc.
-->
<svg xmlns="http://www.w3.org/2000/svg" style="display: none;">
  <symbol id="0" viewBox="0 0 320 512">
    <path d="M0 192C0 103.6 71.6 32 160 32s160 71.6 160 160V320c0 88.4-71.6 160-160 160S0 408.4 0 320V192zM160 96c-53 0-96 43-96 96V320c0 53 43 96 96 96s96-43 96-96V192c0-53-43-96-96-96z"></path>
  </symbol>
  ...생략
</svg>
```

<small><p align='center'><strong>https://github.com/FortAwesome/Font-Awesome/blob/6.x/js-packages/%40fortawesome/fontawesome-free/sprites/brands.svg</strong></p></small>

하지만 이미지가 복잡해질수록 svg만의 장점은 감소하게 됩니다.
그렇기 때문에 디테일을 표현하기에는 부족한 점이 있습니다.

### SVG 내부 도형

- `<rect>` : 사각형
- `<circle>` : 원
- `<path>` : 선과 곡선 등의 다양한 형태를 그릴 수 있음

### 이미지 렌더링 개선법

1. next/image 활용하기

```js
import Image from "next/image";

const myLoader = ({ src, width, quality }) => {
  return `https://example.com/${src}?w=${width}&q=${quality || 75}`;
};

const MyImage = (props) => {
  return (
    <Image loader={myLoader} src="me.png" alt="Picture of the author" width={500} height={500} />
  );
};
```

width,height는 필수 property이며, `myLoader`가 리턴하는 값에서 quality가 제공되지 않을때는 알아서 75로 맞춰주는걸보니 최적화 기능을 하고 있는 것으로 보입니다.

그리고 next/image는 이미지 파일을 webp와 같은 용량으로 변환해서 제공합니다.

또 하나로 그냥 리액트만 사용했을 때는 로딩 처리를 직접 해줘야 했던 반면에, next/image는 알아서 lazy loading 처리를 해줍니다.

2. 이미지 스프라이트

<img src='https://burchurl.files.wordpress.com/2014/11/sprite.png' />

위처럼 여러 개의 이미지를 모아서 `width`,`height`,`background-position` 등의 속성을 사용해서 로딩 시간을 해결할 수 있습니다.

3. 벡터 이미지 사용하기

간단한 이미지로만 사용할 경우에는 벡터 이미지를 사용하면 렌더링 속도를 개선시킬 수 있습니다.

Reference

- https://lottiefiles.com/kr/blog/about-lottie/kr-difference-png-svg-lottie
- https://nextjs.org/docs/api-reference/next/image
- https://burchurl.wordpress.com/2014/11/18/responsible-web-%EB%B0%98%EC%9D%91%ED%98%95-%EC%9B%B9%EC%97%90%EC%84%9C-image-sprite-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0/
- https://www.adobe.com/kr/creativecloud/file-types/image/vector/svg-file.html
- https://m.blog.naver.com/eg1616/150128475851
- https://brunch.co.kr/@dailyhotel/20
- https://bythem.net/2021/03/03/svg%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EC%9D%B4%EC%9C%A0/
- <a href='https://fe-developers.kakaoent.com/2022/220714-next-image/'>Next/Image를 활용한 이미지 최적화</a>
- <a href='https://freefrontend.com/css-calculators'>8 CSS Calculators</a>
