먼저 CORS가 무엇인가?

뜻만 번역해보자면 일단 **교차 출처 리소스 공유**다.

## **여기서 출처란?**

출처는 여러 구조로 되어있는데, **`https://google.com`** 를 예로 들면

`https` 가 출처, `ttps://google.com` 이 host인데, 이 이외에 `path`, `query string`, `fragment` 그리고 :80, :443 같은 포트 번호로 구성되어 있다.

포트 번호까지 명시되어 있는 경우 서로 포트 번호까지 동일해야만 같은 출처로 인정이 된다.

<img src='https://s3.us-west-2.amazonaws.com/secure.notion-static.com/213e877c-d313-4710-b0fa-24f1a8d8f6a0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221014%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221014T105026Z&X-Amz-Expires=86400&X-Amz-Signature=34b342d7d7c031124f69c2b91ebd7a680ed8091d6fb220b6cdfccdc1a1026b55&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject'/>

### SOP

Same Origin Policy의 준말로 `같은 출처의 리소스`만 공유가 가능하다는 정책이다.

서로 다른 출처로 리소스를 주고 받을 경우 이 SOP 정책을 위반하여 CORS 에러가 나게 된다.

물론 예외 사항으로 “**CORS 정책을 지킨 리소스 요청**”이 있다고는 한다.

아무튼 서로 다른 출처끼리 리소스를 자유롭게 공유할 수 있다면 어떻게 될까?

악의를 가진 사용자가 CSRF나 XSS 같은 걸 통해서 내가 애써 만든 프로젝트가 없어질 수도 있는 것이다.

### 그럼 같은 출처인지 다른 출처인지 어떻게 구분하는가?

두 URL 간의 `Scheme`, `Host`, `Port` 를 비교했을 때 서로 동일하면 같은 출처로 인정이 된다.

그런데 이렇게 비교하는 로직이 서버에 있는 게 아니라 브라우저에 구현되어 있다.

우리가 CORS 정책을 위반하는 리소스 요청을 했다 하더라도 같은 출처만 받겠다는 요청만 아니라면 서버는 정책 위반을 했다는 걸 모른채 정상적으로 로그에 찍히지만 브라우저에서는 에러가 발생하기 때문에 곤란한 점이 있다.

그래서 서버에서 정상적인 응답을 하여 상태코드가 200이 나오더라도, 브라우저가 응답을 CORS정책 위반이라고 분석하면 그 응답은 사용하지 않는다.

### CORS는 어떻게 동작하는가?

먼저 클라이언트의 HTTP 요청 헤더 안에 `Origin` 을 넣어서 전달한다.

서버는 응답 헤더에 `Access-Control-Allow-Origin`을 담아서 클라이언트로 전달한다.

이후에 클라이언트 쪽에서는 자신이 보냈던 요청과 들어온 응답이 유효한지 확인한다.

## **CORS의 3가지 시나리오**

### **1. Preflight**

<img src='https://evan-moon.github.io/static/c86699252752391939dc68f8f9a860bf/6af66/cors-preflight.png' style='background-color:white' />

브라우저가 본 요청을 보내기 전 예비로 보내는 요청으로 이 요청이 보내는 것이 안전한지 확인하는 과정을 거친다.

`fetch`를 사용해서 브라우저한테 리소스를 받아오라는 명령을 내리면 브라우저는 서버에 예비 요청을 먼저 보내면,

서버는 이에 대한 응답으로 어떤 것들을 수용하거나 금지하는 지에 대한 정보를 응답 헤더에 담아서 보내게 된다.

이후 브라우저는 예비 요청과 서버로부터 받아온 응답 헤더 정보를 비교해서 이 예비 요청을 보내는 것이 안전하다고 판단될 경우

같은 엔드포인트로 다시 본 요청을 보낸다.

### **2. Simple Request**

<img src='https://evan-moon.github.io/static/d8ed6519e305c807c687032ff61240f8/6af66/simple-request.png' style='background-color:white' />

예비 요청을 보내지 않고 서버에게 본 요청부터 보낸 후, 서버가 이에 대한 응답 헤더 **`Access-Control-Allow-Origin`** 과 같은 값을 보내주면 브라우저가 CORS를 위반하는지 검사하는 방식이다.

이 요청을 보내기 위해서는 조건이 필요한데, 다음과 같다.

- 요청 메소드는 `GET`, `POST`, `HEAD` 중 하나여야 한다.
- **`Accept`**, **`Accept-Language`**, **`Content-Language`**, **`Content-Type`**, **`DPR`**, **`Downlink`**, **`Save-Data`**, **`Viewport-Width`**, `Width`를 제외한 헤더를 사용하면 안된다.
- 만약 `Content-Type`를 사용하는 경우에는 **`application/x-www-form-urlencoded`**, **`multipart/form-data`**, `text/plain`만 허용된다.

### **3. Credential Request**

인증된 요청을 사용하는 방법으로 다른 출처 간 통신에서 보안 강화를 위해 쓰는 방법이다.

기본적으로 fetch API 같은 걸로 서버에 요청을 보낼 때 인증이나 쿠키에 관련된 헤더 정보를 담는건 위험하다.

그렇기 때문에 인증과 관련된 정보를 담을 수 있게 해주는 `credential`이라는 옵션이 존재한다.

이 때 프론트에서는 `credentials`를 true로 설정하고 서버에서는

`Access-Control-Allow-Credentials`를 true로 설정한다.

Reference

- https://evan-moon.github.io/2020/05/21/about-cors/
