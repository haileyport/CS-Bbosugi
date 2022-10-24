담당: 지수님
<img width="761" alt="스크린샷 2022-10-23 오후 8 03 37" src="https://user-images.githubusercontent.com/102123710/197388579-d0b49c15-137d-4c56-8722-6114de2438b6.png">

---

# 1. CSS selector의 작동 원리
### 🔎 CSS selector란?
selector, 즉 선택자란 말 그대로 선택을 해주는 요소입니다. 이를 통해 특정 요소들을 선택하여 스타일을 적용할 수 있게 됩니다 
### 📍그럼 CSS selector는 어떠한 원리로 동작할까?
먼저, 선택자는 크게 4가지로 분류할 수 있습니다. 

* `ID` : #header, #footer
* `Class` : .container
* `Tag` : div, p, a
* `Universal` : *
![](https://velog.velcdn.com/images/fejigu/post/31957534-7140-4692-824c-d8d6fa137709/image.png)

👉🏻 **`스타일 엔진은 키 셀렉터로부터 시작하여 왼쪽으로 이동하면서 엘리먼트가 규칙에 적합한지 확인합니다. 만약 엘리먼트가 이 규칙에 적합하거나 적합하지 않다는게 확인되면 멈추게 되는 것입니다.`**

---

# 2. CSS 적용 우선순위


### 📍CSS 적용 우선순위는 크게 2가지
**1. 기본적으로 뒤에 나오는 css가 우선순위가 높습니다.<br>
2. `!important` > `inline style attribute` > `id` > `class`, 다른 attribute, 수도클래스(:first-child같은 것) > `tag element`, 수도엘레먼트(::before같은 것) 순으로 우선순위가 높습니다.<br>**

---

![](https://images.velog.io/images/khsfun0312/post/1dd50153-6f75-4173-9aa9-bd6b7e0a2072/image.png)

#### 1. !important
우선순위를 무시하고, 꼭 적용 시키고 싶은 속성이 있다면, 속성 값 뒤에 !important 를 붙여서 적용시켜주면 됩니다.<br>
**`!important 는 우선순위 뿐만 아니라 디자이너-개발자간커뮤니케이션시 중요한 속성임을 알리는 뜻을 나타내기도 합니다.`**

🔎**이해 해보는 시간**<br>

1)
```
p {
  color: red;
}
p {
  color: blue;
}
```
![스크린샷 2022-10-24 오후 9 22 57](https://user-images.githubusercontent.com/102123710/197524614-ece6d4a5-50d7-43df-baf4-8ce15aaff260.png)


2)
```
p {
  color: red !important;
}
p {
  color: blue;
}
```
![스크린샷 2022-10-24 오후 9 22 19](https://user-images.githubusercontent.com/102123710/197524527-c3290606-12d9-42fe-9941-112726ade3e8.png)


3)다시 속성값을 재설정하고 싶으면 !important를 다시 붙입니다.
```
p {
  color: red !important;
}
p {
  color: blue;
}
p {
  color: green !important;
}
```
![스크린샷 2022-10-24 오후 9 23 37](https://user-images.githubusercontent.com/102123710/197524732-84bd8d4a-4707-4d36-ac16-30679a3b2f07.png)


👉🏻!important은 CSS 코드를 혼란스럽게 만들고 특히 큰 스타일 시트가 있는 경우 디버깅이 어렵습니다.<br>
**꼭 필요한 경우가 아니라면 남발하지 않아야합니다.**

---


#### 2. inline 스타일 속성
html 문서에서 tag 내에 style를 정의하는 것
```javascript
<p style="color: red">
```
#### 3. id 선택자
tag 내에 id를 정의한 후 #id 이름
```javascript
<p id="abc">서울<p/>
#abc{color: red;}
```
#### 4. class 선택자
tag 내에 class를 정의한 후 .class 이름
```javascript
<p class="def">부산</p>
.def{color: red;}
```
#### 5. tag 선택지
tag를 바로 선택자로 사용
```javascript
p{color: red}
```
#### 6. 전체 선택자
요소 전체
```javascript
*{color: red}
```

---

### 🔎 만약 같은 우선 순위에 있다면?
같은 우선 순위에 있는 경우, <br>
**`부모-자식 관계가 많은 경우가 우선되며, 모든 설정이 같은 경우 나중에 선언한 것이 우선되어 적용됩니다`**
### ❓CSS 적용 우선순위를 알아둬야 하는 이유
**`CSS 스타일을 적용하는데는 다양한 방법이 있으며, 동시에 여러가지 방법을 사용할 수도 있기 때문에 엘리먼트에 적용되는 스타일이 충돌할 수도 있습니다.`**<br>

따라서, 스타일 적용의 우선 순위 규칙을 알아둘 필요가 있는 것입니다.
