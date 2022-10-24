담당: 여울님


# PX, 웨 않돼?
---
기본적으로 px와 em, rem의 정의에 대해서는 길게 적기 보다는 간단하게 적고

 **왜 px보다는 rem을 활용하는 것이 좋은지**에 대해 알아보기로 한다.

 <br>

### 픽셀을 사용했을 때 문제점
---
픽셀은 모두가 아시다시피 **절대값**을 말한다.

모든 브라우저에는 루트 글꼴 크기 설정이 되어있다.

스타일을 지정하지 않은 텍스트는 일반적으로 16px로 표시된다.
사용자 브라우저 설정에서 루트글꼴 크기를 변경 할 수도 있다.
- 루트글꼴맞춤방법
```
크롬 > 더보기 메뉴(오른쪽 상단 작은 점3개) > 설정 > 모양 > 글꼴 크기 변경 또는 글꼴 맞춤설정 에서 원하는 크기 지정
```

하지만 px로 크기를 고정 하는 순간 모든 브라우저의 설정을 덮어버린다. 이렇게 될 경우 사용자가 원하는 글씨 크기로 설정을 해 둔 것을 개발자가 원하는 크기로 바꾸는 꼴이 되어버린다.

![img](https://velog.velcdn.com/images/wool/post/12038631-a80d-46cb-84a5-96ca93b7240a/image.png)

출처 : https://yozm.wishket.com/magazine/detail/1410/

기본 글씨 크기를 크게 설정을 해 두어도 어떤 사이트의 크기가 작은 픽셀로 지정 되어 있다면 사용자는 작은 사이즈의 폰트로 접근 할 수 밖에 없다는 것이다. 

이렇게 되면 사용성에 큰 제약이 발생한다.

 <br>

### 여기서 등장하는 rem!
---

**rem은 루트 글꼴 크기에 비례하여 상대적으로 바뀌는 단위이다**

rem에서 r은 root를 의미한다.

대부분 1rem = 16px이지만 루트 글꼴 크기를 24px로 설정 할 경우 1rem = 24px이 된다.

**1rem = 루트 글꼴 크기 설정값**

![img](https://velog.velcdn.com/images/wool/post/93ecfcfa-b679-4070-9340-10bf1f1375ba/image.png)

출처 : https://yozm.wishket.com/magazine/detail/1410/

rem은 고정값이 아니며 px로 직접 변환 할 수는 없지만 루트 글꼴 크기를 기반으로 px값을 계산 할 수 있다. 때문에 디자이너가 화면 계층 구조 내에서 다른 요소들과 어우러 질 수 있도록 원하는 글꼴 크기를 지정하면서 화면의 크기 변경에도 유연하게 반응 할 수 있다는 장점이 있다.

 <br>

### em도 상대적인 단위인데 rem과 무엇이 다를까?
---

![img](https://velog.velcdn.com/images/wool/post/517caa23-b3e8-42a5-8e2d-0cbe60bf302b/image.png)

출처 : https://yozm.wishket.com/magazine/detail/1410/

- **rem**
    브라우저의 루트 글꼴 즉 최상위요소(html) 크기의 배수로 적용된다

    예시) 루트 글꼴이 16px일 경우 1rem = 16px

- **em**
    텍스트를 포함하는 엘리먼트에 배수로 적용된다
    
    예시) 컨테이너의 글꼴 크기가 2rem = 32px일 경우 컨테이너 내부에서 1em = 32px

 <br>

### 정리
![img](https://velog.velcdn.com/images/wool/post/5dcfd05a-6d4f-405e-9ac0-7fca35392ba0/image.png)

출처 : https://yozm.wishket.com/magazine/detail/1410/

이러한 속성들을 파악하여 폰트크기 뿐만 아니라 패딩과 마진값을 설정 할 때 참고 하는 것이 좋다!

 <br>

# margin padding

![img](https://velog.velcdn.com/images/wool/post/1dc6068b-9c56-495e-89ec-7fcddd7c70bd/image.png)

개발자도구를 열면 이렇게 요소의 박스모델을 확인 할 수 있다.
 <br>

**padding**

Padding은 Content와 Border 사이의 여백을 나타낸는 영역이다. 

Content 영역이 배경색이나 배경 이미지를 가질 때, 이 Padding 영역까지도 영향을 미친다. 즉, Padding 영역도 Content의 연장으로 볼 수 있다.
 <br>

**margin**

Margin은 Border 바깥쪽을 차지한다. 주변 요소와 거리를 두기 위한 영역이다.
 <br>

### margin과 padding의차이점

![img](https://velog.velcdn.com/images/wool/post/15b69b40-a15a-4b03-8f6d-f10472947597/image.png)

출처 : https://enai.tistory.com/49

1. **음수값 적용여부**

    margin은 음수 값이 적용된다.
    padding은 음수 값이 적용되지 않는다.

2. **auto**

    auto는 브라우저에 의해 계산이 되는 값이다. 0이나 해당 요소가 사용 가능한 공간과 같은 값을 가지게 된다.

    만약 좌우 margin이 모두 auto면, 해당 요소가 가질 수 있는 가로 영역 중 자신의 width를 제외한 나머지 여백 크기를 균등 분할하여 적용한다. 그래서 수평으로 가운데 정렬이 된다.

    즉, 가운데 정렬을 위해 margin: auto; / margin: 0 auto; 이렇게 사용하는 것을 많이 보았을 것이다.

    이렇게 margin은 auto 값으로 선언할 수 있다.

    하지만 padding은 auto로 선언할 수 없다.


3. **collapse**

    margin은 둘 이상의 요소의 margin 값이 둘 중 더 큰 margin 값으로 합쳐지는 특징이 있다.

    **margin collapse(마진 병합)**

    ![img](https://velog.velcdn.com/images%2Fursr0706%2Fpost%2F67d3104c-5e30-4421-8b82-52ea208318d1%2F%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-07-19%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2010.24.56.png)

    출처 : https://velog.io/@ursr0706/%EB%A7%88%EC%A7%84margin


    - 두 요소가 상하로 인접했을 때, 위 요소의 하단 margin과 상단 margin의 병합이 일어난다.
    - 내용이 없는 빈 요소의 경우, 해당 요소의 상단 margin과 하단 margin의 병합이 일어난다.
    - 인접하는 두 블록요소에 각각 margin:20px;의 속성을 줬을 때,위의 그림을 보면 section1의 하단 마진부분과 section2의 상단 마진부분이 서로 겹쳐져서
    그 사이의 마진이 총 40px이 아닌 20px이 되는 것을 볼 수 있다.


    - margin collapse가 일어나지 않는 상황

        수직 방향으로만 이루어지며, 좌우에 대해서는 일어나지 않는다.

        margin이 맞닿은 상황에서 발생하는 것이기 때문에, padding과 border가 있으면 일어나지 않을 수도 있다.
        플로팅 요소와 절대 위치를 지정한 요소는 collapse가 일어나지 않는다


    **padding은 collapse가 발생하지 않는다.**

    margin은 두 요소 바깥쪽의 간격을 나타내는 속성이며, padding은 요소의 border와 content 사이를 나눠주는 즉, 요소 내부의 간격을 나타내기 때문이라고 한다.

    

### 참고
---
https://yozm.wishket.com/magazine/detail/1410/

https://inpa.tistory.com/entry/CSS-%F0%9F%93%9A-%EA%B0%92%EC%9D%98-%EB%8B%A8%EC%9C%84-px-em-rgb-viewport

https://enai.tistory.com/49

https://velog.io/@ursr0706/%EB%A7%88%EC%A7%84margin