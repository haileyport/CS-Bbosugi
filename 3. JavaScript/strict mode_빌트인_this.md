# Strict mode

## Strict mode란?

ECMA Script 5에서 처음으로 소개된 모드이며, 자바스크립트 코드에서 **더욱 엄격한 오류 검사를 수행**합니다.

## Strict mode를 설정하는 법

스크립트나 함수의 맨 처음에 "use strict" 지시어를 사용해 선언합니다.

```javascript
'use strict'; // 전체 스크립트를 strict 모드로 설정함.

try {
  num = 3.14; // 선언되지 않은 변수를 사용했기 때문에 오류를 발생시킴.
} catch (ex) {
  document.getElementById('text').innerHTML = ex.name + '<br>';

  document.getElementById('text').innerHTML += ex.message;
}
```

이렇게 선언된 strict 모드는 해당 블록의 코드를 strict 모드의 문법에 따라 엄격하게 검사합니다.

```javascript
str = '실수!'; // 선언되지 않은 변수를 사용했지만 자동으로 전역 변수로 선언됨.

document.getElementById('noStrict').innerHTML = str + '<br>';

function StrictBlock() {
  'use strict'; // 함수 블록만을 strict 모드로 설정함.

  try {
    num = 123; // 선언되지 않은 변수를 사용했기 때문에 오류를 발생시킴.
  } catch (ex) {
    document.getElementById('funcStrict').innerHTML = ex.name + '<br>';

    document.getElementById('funcStrict').innerHTML += ex.message;
  }
}

StrictBlock();
```

strict 모드가 아닌 경우는 선언되지 않은 변수를 사용해도 *자동으로 전역 변수로 인식*합니다.
그러나 strict 모드에서는 *선언되지 않은 변수를 사용하면 오류*가 발생합니다.

## Strict 모드의 특징

기존 자바스크립트의 문법과 strict모드의 문법은 다음과 같은 차이가 있습니다.

1. 실수로 생성된 글로벌 변수 차단

```javascript
'use strict';
// 전역 변수 mistypedVariable 이 존재한다고 가정
mistypedVaraible = 17; // 변수의 오타때문에 이 라인에서 ReferenceError 를 발생시킴
```

2. 쓸 수 없는 변수 or 프로퍼티에 할당, 읽기 전용 프로퍼티에 할당, 확장 불가 객체에 새 프로퍼티 할당 차단

```javascript
'use strict';

// 쓸 수 없는 프로퍼티에 할당
var undefined = 5; // TypeError 발생
var Infinity = 5; // TypeError 발생
// undefined와 Infinity는 기존에 정의된 변수/프로퍼티

// 쓸 수 없는 프로퍼티에 할당
var obj1 = {};
Object.defineProperty(obj1, 'x', { value: 42, writable: false });
obj1.x = 9; // TypeError 발생
// writable false로 읽기 전용이기 때문

// getter-only 프로퍼티에 할당
var obj2 = {
  get x() {
    return 17;
  },
};
obj2.x = 5; // TypeError 발생
// 읽기 전용 프로퍼티

// 확장 불가 객체에 새 프로퍼티 할당
var fixed = {};
Object.preventExtensions(fixed);
fixed.newProp = 'ohai'; // TypeError 발생
// Object.preventExtensions는 새로운 속성이 객체에 추가되는 것을 금지합니다.
```

3. 삭제할 수 없는 프로퍼티를 삭제하려고 할 때 예외 발생

```javascript
'use strict';
delete Object.prototype; // TypeError 발생
// Object.prototype은 자바스크립트 내장 프로퍼티라서 삭제가 불가능
```

4. 객체의 모든 프로퍼티가 unique하도록 제어

```javascript
'use strict';
var o = { p: 1, p: 2 }; // !!! 구문 에러
```

5. 유니크한 함수 파라미터 이름 요구

```javascript
function sum(a, a, c) {
  // !!! 구문 에러
  'use strict';
  return a + b + c; // 코드가 실행되면 잘못된 것임
}
```

6. 8진수 금지

```javascript
var a = 0o10; // ES6: 8진수
```

7. primitive값(원시값)에 프로퍼티 설정 금지

```javascript
(function () {
  'use strict';

  false.true = ''; // TypeError
  (14).sailing = 'home'; // TypeError
  'with'.you = 'far away'; // TypeError
})();
```

\*원시값: string, number, bigint, boolean, undefined, symbol, null

# 빌트인 객체

브라우저의 자바스크립트 엔진에 내장되어 사용자의 환경에 상관 없이 즉시 사용할 수 있는 객체

## 자바스크립트 객체의 분류

### 1. 표준 빌트인 객체

- ECMAScript 사양에 정의된 객체로, 실행환경과 관계없이 항상 사용 가능하다.
- 자바스크립트 실행 환경에 관계없이 언제나 사용 가능하다.
- 전역 객체의 프로퍼티로서 제공된다(별도 선언 없이 언제나 참조 가능)

Number, String, Object, Boolean, Array, Function, Math, Date, JSON, RegExp, Global 등 40여개의 표준 빌트인 객체가 있다.

### 2. 호스트 객체

- 실행 환경에서 추가적으로 제공하는 객체
- 브라우저에서는 DOM, XMLHttpRequest, fetch, SVG와 같은 클라이언트 사이드 Web API를 제공한다.
- Node.js 환경에서는 Node.js 고유의 API를 제공한다.

### 3. 사용자 정의 객체

- 기본 제공 객체가 아닌 사용자가 직접 정의한 객체

# this

## this란?

자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기참조 변수

![this?](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FIr9Wv%2FbtqDMj83j3v%2FAhHYBHS48NKIsF9AIWJJeK%2Fimg.png)

자바스크립트 내에서 this는 '누가 나를 불렀냐'를 뜻한다고 합니다.
선언이 아닌 호출에 따라 달라지는 값인 셈입니다.
따라서 상황별로 this가 바인딩되는 곳을 알아야 합니다.

1. 단독으로 쓴 this
   아묻따 this를 호출하는 경우는 `global object`를 가리킵니다.
   브라우저에서 호출 시 [object Window]가 됩니다!
   ![image](https://user-images.githubusercontent.com/50188104/198816876-2a75b1f9-3b61-47b1-b4d8-3a2bf887d659.png)

2. 함수 안에서 쓴 this
   함수 안에서 this는 함수의 주인에게 바인딩됩니다.
   함수의 주인 === window 객체

```javascript
function myFunction() {
  return this;
}
console.log(myFunction()); //Window
```

```javascript
var num = 0;
function addNum() {
  this.num = 100;
  num++;

  console.log(num); // 101
  console.log(window.num); // 101
  console.log(num === window.num); // true
}

addNum();
```

위 코드에서 this.num의 this는 window 객체를 가리킵니다.
따라서 num은 전역 변수를 가리키게 됩니다.

다만 앞서 소개한 strict mode 에서는 조금 다릅니다.
함수 내에 this에 디폴트 바인딩이 없기 때문에 undefined가 됩니다.

```javascript
'use strict';

function myFunction() {
  return this;
}
console.log(myFunction()); //undefined
```

```javascript
'use strict';

var num = 0;
function addNum() {
  this.num = 100; //ERROR! Cannot set property 'num' of undefined
  num++;
}

addNum();
```

따라서 this.num은 undefined.num과 동일하기 때문에 에러가 납니다.

3. 메서드 안에서 쓴 this
   메서드 호출 시 메서드 내부 코드에서 사용된 this는 해당 메서드를 호출한 객체로 바인딩 됩니다.

```javascript
var person = {
  firstName: 'John',
  lastName: 'Doe',
  fullName: function () {
    return this.firstName + ' ' + this.lastName;
  },
};

person.fullName(); //"John Doe"
```

```javascript
var num = 0;

function showNum() {
  console.log(this.num);
}

showNum(); //0

var obj = {
  num: 200,
  func: showNum,
};

obj.func(); //200
```

4. 이벤트 핸들러 안에서 쓴 this
   이벤트를 받는 HTML 요소를 가리킵니다.

```javascript
var btn = document.querySelector('#btn');
btn.addEventListener('click', function () {
  console.log(this); //#btn
});
```

5. 생성자 안에서 쓴 this
   생성자 함수가 생성하는 객체로 바인딩 됩니다.

```javascript
function Person(name) {
  this.name = name;
}

var kim = new Person('kim');
var lee = new Person('lee');

console.log(kim.name); //kim
console.log(lee.name); //lee
```

하지만 new 키워드가 빠지면 일반 함수 호출과 동일해져서, 이 경우는 this가 window에 바인딩됩니다.

```javascript
var name = 'window';
function Person(name) {
  this.name = name;
}

var kim = Person('kim');

console.log(window.name); //kim
```

6. 화살표 함수로 쓴 this
   화살표 함수는 전역에서 실행되더라도 this를 새로 정의하지 않고, 바로 바깥 scope의 함수나 클래스의 this를 사용한다.
   **아니 왜 함수 안에서 this가 전역이 되는건데** 싶을 때 사용합니다.

[함수 적용]

```javascript
var Person = function (name, age) {
  this.name = name;
  this.age = age;
  this.say = function () {
    console.log(this); // Person {name: "Nana", age: 28}

    setTimeout(function () {
      console.log(this); // Window
      console.log(this.name + ' is ' + this.age + ' years old');
    }, 100);
  };
};
var me = new Person('Nana', 28);

me.say(); //global is undefined years old
```

[화살표 함수 적용]

```javascript
var Person = function (name, age) {
  this.name = name;
  this.age = age;
  this.say = function () {
    console.log(this); // Person {name: "Nana", age: 28}

    setTimeout(() => {
      console.log(this); // Person {name: "Nana", age: 28}
      console.log(this.name + ' is ' + this.age + ' years old');
    }, 100);
  };
};
var me = new Person('Nana', 28); //Nana is 28 years old
```

---

[Strict Mode](http://www.tcpschool.com/javascript/js_exception_strict)
<br/>
[Strict Mode 제한사항 예시](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Strict_mode)
<br/>
[빌트인 객체](https://serzhul.io/JavaScript/21.%EB%B9%8C%ED%8A%B8%EC%9D%B8-%EA%B0%9D%EC%B2%B4/)
<br/>
[this](https://nykim.work/71)
