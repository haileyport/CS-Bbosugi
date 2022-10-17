담당: 혜정

### 질문 리스트

- ✅HTTP란 뭔가요?
- ✅HTTP 프로토콜의 가장 큰 특징은 뭔가요?
- ✅URL은 뭔가요?
- ✅HTTP/1.1 과 HTTP/2.0의 차이는 뭔가요?
- ✅HTTPS는 HTTP랑 뭐가 다른가요?
- ✅심화) 공개키 (비대칭키) 방식이 뭔가요?

---

### HTTP란 무엇인가요?

> Hypertext Transfer Protocol

인터넷상에서 데이터를 주고받을 수 있는 프로토콜, 즉 규칙을 의미합니다.
![HTTP 네트워크 계층](https://t1.daumcdn.net/cfile/tistory/2137653E5816076413)

네트워크 모델의 최상위 계층인 응용 계층에서 클라이언트와 서버간 요청과 응답을 주고받을 때 HTTP 프로토콜로 정해진 HTTP 메시지를 주고받게 됩니다. HTTP 메시지에는 요청과 응답에 관련된 메타 정보와 요청 데이터, 응답 데이터가 함께 포함됩니다.

HTTP는 응용 계층에서 사용되는 프로토콜이기 때문에, 네트워크 통신은 가장 대중적이고 신뢰성이 있는 TCP/IP 프로토콜을 기반으로 합니다. TCP/IP 프로토콜을 기반으로 정상적인 데이터 전송을 보장받기 때문에 데이터 손실에 대한 걱정 없이 기능 개발에 집중할 수 있다는 이점이 있습니다.

### +) HTTP 메시지란 어떤 역할을 하나요?

HTTP 메시지는 요청과 응답에 대한 정보, 그리고 함께 전송되는 데이터를 포함합니다. HTTP 요청 메시지를 전송해 서버에서 액션이 일어나도록 하고, HTTP 응답 메시지에 요청에 대한 서버의 답변을 실어 전송합니다.

![HTTP 메시지](https://t1.daumcdn.net/cfile/tistory/21282E3B554A0A1B2C)

HTTP 메시지는 여러 줄의 문자열로 구성이 되어 있고, 요청 메시지와 응답 메시지의 구성이 비슷합니다. 스타트 라인, 헤더, 본문 3가지로 구분할 수 있습니다.

스타트 라인 - 시작 줄은 메시지의 첫 줄로 요청이라면 어떤 요청을 어디로 보내는지, 응답이라면 요청에 대한 처리 결과를 의미합니다.

헤더 - 요청에 대한 설명 혹은 메시지 본문에 대한 설명이 포함됩니다.

본문(body) - 요청과 응답에 관련된 데이터를 포함합니다. 요청 및 응답의 유형에 따라 선택적으로 사용됩니다.

### HTTP 프로토콜의 가장 큰 특징은 무엇인가요?

HTTP 프로토콜의 특징으로는 무상태성과 비연결성이 있습니다. 무상태성은 서버에서 클라이언트의 상태를 저장하지 않는 것을 의미하고, 비연결성은 하나의 요청에 대해서 응답이 종료되었을 때 TCP/IP 연결이 끊어지는 것을 의미합니다.

![HTTP 메시지](https://i0.wp.com/hanamon.kr/wp-content/uploads/2021/09/HTTP-%E1%84%86%E1%85%AE%E1%84%89%E1%85%A1%E1%86%BC%E1%84%90%E1%85%A2%E1%84%89%E1%85%A5%E1%86%BC.png?w=689&ssl=1)

무상태성을 기반으로 하기 때문에 클라이언트 측에서 요청을 보낼 때 필요한 모든 정보를 포함한 HTTP 요청을 보내야 합니다. 로그인과 같이 클라이언트의 상태를 저장해 유지할 필요가 있을 경우에는 쿠키, 세션, 토큰과 같은 추가적인 인증 데이터를 사용할 수 있습니다.

비연결성을 기반으로 하기 때문에 통신이 이루어지지 않을 때는 서버 자원을 아낄 수 있다는 장점이 있지만, 리소스에 대한 모든 요청마다 연결을 새롭게 해야한다는 단점도 있습니다.

### URL은 무엇인가요?

![HTTP 메시지](https://www.beusable.net/blog/wp-content/uploads/2021/02/image-6.png)

Uniform Resource Locator 의 약자로, 서버 내에 존재하는 리소스의 구체적인 위치를 표현하는 리소스 식별자입니다.

스킴과 호스트(도메인 주소), 리소스로 이루어져 있는데, 각각 리소스에 접근을 위한 프로토콜과 인터넷 상에서의 서버 주소 그리고 웹서버의 리소스를 가리킵니다.

클라이언트에서 서버에 위치한 특정 자원에 대해 요청을 보낼 때 사용할 수 있으며, path parameter와 query string을 활용해 서버 내의 리소스의 위치를 특정짓고, 원하는 데이터를 필터링하여 요청할 수 있습니다.

### HTTP/1.1 과 HTTP/2.0의 차이는 뭔가요?

HTTP는 하나의 연결에서 하나의 요청과 응답밖에 처리하지 못하는 비연결성을 특징으로 합니다.

![HTTP 메시지](https://blog.kakaocdn.net/dn/bpdV4n/btrub9VkLO4/2UHDW7xWK6x9RIKKorkkQ0/img.png)

HTTP/1.1 에서는 이러한 문제를 해결하기 위해 지정한 시간동안 커넥션을 끊지 않는 지속적 연결 상태(presistent connection) 를 도입했고, 파이프라이닝을 도입해 응답 지연 속도와 효율성 문제를 개선했습니다. 파이프라이닝이란 하나의 커넥션에서 요청을 보내고 응답을 기다리는 것이 아니라, 순차적으로 여러 요청을 보낸 뒤 해당 순서에 맞게 응답을 받는 방식입니다.
결국은 응답을 미루는 것이고, 순차적으로 처리되기 때문에 후순위의 응답은 지연될 수밖에 없는 문제점이 있습니다.

HTTP/2.0 에서는 기존 HTTP/1.1의 문제점을 해소하여 속도와 성능을 향상시키기 위해서 만들어졌습니다.

![HTTP 메시지](https://miro.medium.com/max/720/1*rf2AnDQyHfGO_ThYfb-hWA.png)

HTTP/2.0은 아래와 같은 특징을 가지고 있습니다.

- Multiplexed Streams : 하나의 커넥션에서 여러개의 메시지를 동시에 주고받을 수 있습니다.
- Stream Prioritization : 먼저 응답받고 싶은 요청에 대해서 우선순위를 지정할 수 있습니다.
- Header Compression : Header 정보를 HPACK 방식으로 압축 전송합니다. 헤더의 크기가 줄어서 페이지 로드 시간을 줄여줍니다.
- Server Push : HTML 문서상에 필요한 리소스를 클라이언트 요청 없이 보내줄 수 있습니다.

동시에 여러 메시지를 주고 받을 수 있기 때문에, 순차적으로 처리하는 것에 비해 전송 지연에 대한 속도 문제를 해결할 수 있습니다.

### HTTPS는 HTTP랑 뭐가 다른가요?

![HTTP 메시지](https://joongbu.raonctf.com/static/essential/images/protocol/ssl_tls_01.jpg)

HTTPS 란 암호화를 통해 HTTP를 더 안전하게 사용할 수 있도록 하는 프로토콜입니다. 기존 HTTP에서는 전송 데이터를 암호화하지 않습니다. 따라서 요청과 응답 데이터가 전송되는 도중에 쉽게 도난당할 수 있습니다.

이 문제를 해결하기 위해 HTTPS 에서는 SSL(Secure Sockest Layer - 보안 소켓 계층)을 사용하여 요청과 응답 데이터를 전송하기 전 암호화를 합니다.

### +) SSL/TLS는 무엇인가요?

SSL과 TLS 는 기존 통신 프로토콜에 암호화를 적용할 수 있는 보안 프로토콜입니다. SSL과 TLS 는 거의 동일한 프로토콜이며, SSL를 기반으로 표준화 된 것이 현재의 TLS 프로토콜 입니다.
SSL/TLS는 암호화 방식 중 대칭 키, 공개 키 암호화 방식을 모두 사용한다는 특징이 있습니다.

대칭 키 암호화 방식이란 하나의 동일한 키를 가지고 암호화와 복호화를 하는 방식이고, 공개 키 방식이란 두 개의 다른 키를 사용해 암호화와 복호화를 하는 방식입니다. 공개 키 방식은 비대칭 키 방식이라고도 하며, 두 개의 키에는 공개되는 키와 공개되지 않는 비밀 키가 있습니다.

![HTTP 메시지](https://devwhkang.gatsbyjs.io/static/f1b5cb1c3ea0cd98b3fbed37b0e42f09/dc9b9/public-key-send.webp)

SSL/TLS 프로토콜에서는 인증 기관에서 발급된 인증서를 통해 서버 신뢰 여부가 결정됩니다. 인증서는 서버 공개 키와 서버 정보가 암호화된 내용이고, 클라이언트에서 이 인증서를 복호화 합니다.

![HTTP 메시지](https://devwhkang.gatsbyjs.io/static/fc205b16f24e887c673368324139ad0c/dc9b9/symmetric-key-share.webp)

복호화가 성공적으로 진행되면 클라이언트는 서버 정보와 서버 공개키를 갖게 되고, 이 때 비대칭 키 방식으로 요청과 응답 암호화,복호화에 사용될 대칭키를 암호화하여 전달합니다.

이렇게 클라이언트와 서버의 대칭키 발급이 완료되면, HTTPS 에서 요청과 응답 데이터를 주고받을 때 이 대칭키로 암호화, 복호화를 하여 안전하게 통신할 수 있게됩니다.

---

### 참고자료

[[도서] HTTP 완벽 가이드](http://www.yes24.com/Product/Goods/15381085)
[https://hanamon.kr/네트워크-http-메세지-message-요청과-응답-구조/](https://hanamon.kr/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-http-%EB%A9%94%EC%84%B8%EC%A7%80-message-%EC%9A%94%EC%B2%AD%EA%B3%BC-%EC%9D%91%EB%8B%B5-%EA%B5%AC%EC%A1%B0/)
[https://joshua1988.github.io/web-development/http-part1/](https://joshua1988.github.io/web-development/http-part1/)
[https://developer.mozilla.org/ko/docs/Web/HTTP/Messages](https://developer.mozilla.org/ko/docs/Web/HTTP/Messages)
[https://jins-dev.tistory.com/m/entry/HTTP11-의-HTTP-Pipelining-과-Persistent-Connection-에-대하여](https://jins-dev.tistory.com/m/entry/HTTP11-%EC%9D%98-HTTP-Pipelining-%EA%B3%BC-Persistent-Connection-%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC)
[https://haengsin.tistory.com/m/74](https://haengsin.tistory.com/m/74)
[https://scshim.tistory.com/m/502](https://scshim.tistory.com/m/502)
