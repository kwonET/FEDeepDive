# JS DEEP DIVE STUDY

[도서] <strong>모던 자바스크립트 Deep Dive</strong> 도서의 학습한 내용을 정리합니다. <br />
매주 학습한 내용을 정리하고, 월요일 22:00 디스코드에서 발표 및 토의를 진행합니다.

## 1주차

#### Chapter1. 프로그래밍

#### Chapter2. 자바스크립트란?

#### Chapter3. 자바스크립트 개발 환경과 실행 방법

<details>
<summary>펼쳐보기</summary>
<div markdown="1">

### 3.1 자바스크립트 실행 환경

- js는 브라우저 환경/ Node.js 환경에서 동작한다.
  - 브라우저 환경 : js를 실행해 웹을 브라우저 화면에 렌더링하는 게 목적 / 따라서 클라이언트 사이드 Web API (ex. DOM API)를 기본 제공한다.
  - Node.js : 브라우저 외부에서 js 실행 환경을 제공하는 게 목적 / 파일 시스템(고유의 api)을 제공, 서버 단이기 때문

### 3.3 Node.js

- node.js : 크롬 v8 js 엔진으로 빌드된 js 런타임 환경
- npm : js 패키지 매니저. node.js에서 사용할 수 있는 모듈을 패키지화해서 모아둔 저장소이자, 패키지 설치와 관리를 위한 cli이다.

</div>
</details>

#### Chapter4. 변수

<details>
<summary>펼쳐보기</summary>
<div markdown="1">

### 4.1 변수란?

- 메모리(1바이트 단위)에 데이터를 저장
- 메모리 셀은 각자 메모리 주소를 가짐.
- 해당 메모리 주소의 값을 CPU가 읽어서 표현식의 연산 수행
- 이러한 메모리 공간을 재사용하기 위해, 변수가 만들어짐

- 변수 : 하나의 값을 저장하기 위해 확보한 메모리 공간 자체, 혹은 그 공간을 식별하기 위한 이름
  - 할당 : 변수에 값을 저장
  - 참조 : 변수에 저장된 값을 읽어들임

### 4.2 식별자

- 식별자 : 어떤 값을 구별해서 식별할 수 있는 고유한 이름

  - 값이 저장되어있는 메모리 주소와 매핑관계
  - 매핑 정보도 메모리에 저장됨
  - 즉, 식별자는 값이 아니라 메모리 주소를 기억함

- 함수, 클래스, 변수 모두 고유한 메모리 공간을 가지고 식별할 수 있으므로 식별자에 해당한다.

### 4.3 변수 선언

- 변수를 선언한다 == 변수를 생성한다. 메모리 공간을 확보하고 변수 이름과 공간을 연결해 저장할 수 있게 준비하는 것

  - var, let, const(ES6) 활용

  * 키워드: var과 같이, js엔진이 수행할 동작이 규정되어있는 명령어

- 암묵적으로 선언과 동시에 undefined값이 할당됨

  - 그렇기에 이전에 다른 application에서 사용했던 값이 남아있는 garbage value 문제를 막을 수 있음

- Reference Error : 식별자를 통해 값을 참조하려 했지만 js엔진이 등록된 식별자를 찾을 수 없을 때 발생하는 에러
- 식별자와 스코프는 실행 context에서 관리된다.

### 4.4 변수 선언의 실행 시점과 변수 호이스팅

```
console.log(score); //undefined
var score =1;
```

- js 코드는 인터프리터에 의해 한줄 씩 순차적으로 실행된다.
- 변수 선언은 런타임(소스코드가 한 줄씩 실행되는 시점)이 아니라, 그 이전 단계에서 먼저 실행된다.
  - 변수 선언이 다른 코드보다 먼저 실행된다.
  - js 엔진은 런타임 전에 소스코드의 평가 과정을 거친다.
  - 이때 변수 선언을 포함한 모든 선언문을 먼저 실행한다.
- 변수 호이스팅 : 변수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작하는 특징

### 4.5 값의 할당

- 선언과 다르게 할당은 런타임에 실행됨
- 선언 이후 값을 할당될 때는 선언된 메모리 주소의 값이 변경되는 것이 아니다. 새로운 메모리 공간을 확보하고 할당 값을 넣는다.

```
console.log(score); //undefined
score =1;
var score;
console.log(score); //1
```

### 4.6 값의 재할당

- 상수는 재할당할 수 없다.
- 재할당되면 이전에 할당되었던 메모리 공간은 garbage가 된다. 메모리에서 언제 해제될지는 알 수 없다. garbage collector가 수행한다.
  - 따라서 메모리의 할당과 해제를 관여할 수 없기에 js는 unmanaged language다.

### 4.7 식별자 네이밍 규칙

- 카멜 케이스 : firstName
- 스네이크 케이스 : first_name
- 파스칼 케이스 : FirstName
- 헝가리언 케이스 : strFirstName

</div>
</details>

#### Chapter5. 표현식과 문

#### Chapter6. 데이터 타입

#### Chapter7. 연산자

#### Chapter8. 제어문

#### Chapter9. 타입 변환과 단축 평가

#### Chapter10. 객체 리터럴

#### Chapter11. 원시 값과 객체의 비교

#### Chapter13. 스코프

<details>
<summary>펼쳐보기</summary>
<div markdown="1">

### 13.1 스코프란?

- 함수의 매개변수가 함수 몸체 내부에서만 참조할 수 있는 유효범위와 관련이 있다
- 변수, 함수, 클래스 이름 (모든 식별자) : 자신이 선언된 위치에 의해 유효범위 (다른 코드가 변수를 참조할 수 있는 범위)가 결정됨

  - 이를 스코프라 한다.
  - 스코프 : 식별자가 유효한 범위

- 식별자 결정: js엔진이 스코프를 통해 어떤 변수를 참조해야할지 결정하는 것
  - 스코프란, js엔진이 식별자를 검색할 때 사용하는 규칙이기도 하다.
  * 코드 context는 lexical 환경으로 이루어진다. 이를 실행 context로 구현하였으며, 모든 코드가 실행 context에서 실행된다.
  - 스코프를 통해 같은 이름의 변수를 구분한다. 즉, 스코프는 네임스페이스다.

### 13.2 스코프의 종류

- 코드의 구분 - 전역 코드 / 지역 코드 - 변수는 자신이 선언된 위치에 따라 스코프가 결정됨 - 전역에서 설정된 전역 스코프를 갖는 전역 변수 / 지역에서 설정된 지역 스코프를 갖는 지역 변수
  지역 스코프

      - 전역 : 코드의 가장 바깥 영역
      - 지역 : 함수 몸체 내부

- 지역 변수는 자신의 지역 스코프와 하위 스코프에서 유효함
- 참조할 변수를 검색하는 것은 스코프 체인에 따라서.

### 13.3 스코프 체인

- 중첩 함수 형태에서는 스코프가 계층적 구조를 갖게 된다
- 모든 지역 스코프의 최상위 스코프는 전역 스코프

#### 13.3.1 스코프 체인과 변수 검색

- 변수 참조시, js엔진은 스코프 체인에 따라 변수를 참조하는 스코프에서 시작해 상위 방향으로 이동하며 선언된 변수를 검색(identifier resolution)함.
- 물리적 실체

  - js엔진이 코드 실행 전 {식별자 : 렉시컬 환경} [자료구조]을 만든다

- 하위 스코프의 유효변수를 상위 스코프에서는 참조할 수 없음
  - 상속에서, 자식의 자산을 부모가 사용할 수 없는 것과 유사한 개념

#### 13.3.2 스코프 체인과 함수 검색

- 함수 선언문 시, 런타임 이전에 함수 객체가 생성
  js엔진이 함수이름의 식별자를 만듦 ->
  그 후 만들어진 함수 객체가 식별자에 할당됨.
- 즉 함수도 식별자에 해당하고, 그렇기에 스코프를 가짐.
- 따라서 스코프는 '변수를 검색하는 규칙'이라기 보다 더 범용적으로 '식별자를 검색하는 규칙'이 맞음.

### 13.4 함수 레벨 스코프

- 코드 블록이 아닌 함수에 의해 지역 스코프가 생성됨.
- var : 함수의 코드 블록을 지역 스코프로 인정
  - const, let : 블록 스코프 지원

### 13.5 렉시컬 스코프

```
var x = 1
function foo(){
    var x = 10;
    bar()
}
function bar(){
    console.log(x)
}
foo(); //1
bar(); // 1
```

bar 함수의 상위 스코프는?

1. 함수가 어디서 호출됐는지 (동적 스코프)
   - 선언되는 시점이 아닌 호출되는 시점에 동적으로 추적
2. 함수가 어디서 정의됐는지 (렉시컬, 정적 스코프)
   - 함수 정의가 평가되는 시점에서 정적으로

- 함수의 상위 스코프는 자신이 정의된 스코프이다.
- 그렇기에 bar함수의 상위 스코프는 전역 스코프이다.

</div>
</details>

#### Chapter14.

<br/>

## 2주차

#### Chapter17. 생성자 함수에 의한 객체 생성

<details>
<summary>펼쳐보기</summary>
<div markdown="1">

### 17.1 Object 생성자 함수

- 생성자 함수
  - New 연산자와 함께 호출
  - 객체(인스턴스)를 생성
  - 생성자함수에 의해 생성된 객체가 인스턴스.
  - Object 외에 다양한 생성자 함수를 제공한다. 이때 반환 인스턴스의 타입은 object(Function 제외) - String, Number, Boolean, Function

## 17.2 생성자 함수

### 17.2.1 객체 리터럴에 의한 객체 생성 방식의 문제점

- 프로퍼티를 통해 객체의 상태를 표현, 메서드를 통해 프로퍼티를 참조하고 조작하는 동작을 표현
- 프로퍼티 구조가 동일함에도 매번 같은 프로퍼티&메서드를 반복해야함.

### 17.2.2 생성자 함수에 의한 객체 생성 방식의 장점

- 객체를 생성하는 템플릿처럼 활용 가능
- 일반 함수로서 호출된 생성자 함수 내의 this는 전역 객체를 가리킴

### 17.2.3 생성자 함수 인스턴스 생성 과정

```js
function Circle(radius) {
  // 1. 암묵적으로 인스턴스가 생성되고 this에 바인딩된다.

  // 2. this에 바인딩되어 있는 인스턴스를 초기화한다.
  this.radius = radius;
  this.getDiameter = function () {
    return 2 * this.radius;
  };

  // case1. nothing: 완성된 인스턴스가 바인딩된 this가 암묵적으로 반환된다.
  // case2. 명시적인 객체 반환 : 암묵적인 this 반환이 무시된다.
  return {};
  // case3. 명시적인 값 반환 : 원시값 반환은 무시된다.
  return 100;
}
```

- 인스턴스를 생성하는 것
  - 암묵적으로 빈 객체 생성 -> 인스턴스가 this와 바인딩
  - 런타임 이전에 실행
- 생성된 인스턴스를 초기화하는 것
  - 인스턴스 프로퍼티에 할당해 초기화
- 인스턴스 반환 - 기본적으로 this를 반환 - 명시적 객체 반환은 인정되지만, 원시값은 반환 안됨. - 생성자 함수 내부에서 return은 반드시 생략해야.

### 17.2.4 내부 메서드, [[Call]] [[Constructor]]

- 내부 슬롯([[Environment], [[FormalParameters]]), 내부 메서드([[Call]] [[Constructor]])
- 일반 함수는 객체이다. 하지만 일반 객체와 다르게 일반 함수는 호출 가능하다.
- [[Call]] : 함수가 일반 함수로서 호출될 때
  - Callable, 호출할 수 있는 객체
- [[Constructor]] : new 연산자와 함께 생성자로 호출될 때

  - Contructor, 호출할 수 없는 객체

- 함수 객체는 Callable이면서 constructor(일반 함수이면서 생성자 함수)이거나, callable이면서 non-contractor(일반함수로만 호출하는 객체)이다.

### 17.2.5 constructor VS non-constructor

- constructor를 구분하는 방법
  - ES6의 메서드 축약 표현
  - 함수 선언문, 함수 표현식

```js
// 일반 함수 정의: 함수 선언문, 함수 표현식
function foo() {}
const bar = function () {};
// 프로퍼티 x의 값으로 할당된 일반 함수로 정의된 함수. 이는 메서드가 아니다.
const baz = {
  x: function () {},
};
// 일반 함수로 정의된 것만이 constructor이다.
new foo();
new bar();

new baz.x();

//화살표 함수 정의
const arrow = () => {};

new arrow(); // TypeError : arrow is not a constuctor

// 메서드 정의 : ES6의 메서드 축약 표현에서만 메서드로 인정
const obj = {
  x() {},
};

new obj.x(); // TypeError : arrow is not a constuctor
```

- non-constructor 함수 객체를 생성자 함수로 호출하면 에러가 발생한다.

### 17.2.6 new 연산자

- New 연산자와 함께 호출하면 -> 생성자 함수로 동작
  - 이때엔 함수 객체의 내부 메서드 중 [[Call]]이 아니라 [[Constructor]]가 호출된다.
  - 함수 내부의 this 또한 생성자 함수가 생성할 인스턴스를 가리킴
- 일반 함수로 호출 시엔 this는 전역 객체 window를 가리키게 된다.

```js
// 생성자 함수
function Circle(radius) {
  this.radius = radius;
  this.getDiameter = function () {
    return 2 * this.radius;
  };
}

//new 연산자 없이 생성자 함수를 호출하면 일반 함수로 호출됨
const circle = Circle(5);
console.log(circle); // undefined (return 값이 없으므로)

//일반 함수 내부의 this는 전역 객체 window를 가리킨다.
console.log(radius); //5
console.log(getDiameter()); //10

circle.getDiameter(); // TypeError : Cannot read property 'getDiameter' of undefined
```

### 17.2.7 new.target

- 생성자 함수가 new 연산자 없이 호출되는 걸 방지하기 위한 ES6의 지원
- Constructor 모든 함수 내부에서 암묵적인 지역 변수처럼 사용되는 메타 프로퍼티
  - New 연산자와 함께 사용되는 경우
    - New.target 은 함수 자신을,
  - New 연산자 없이 일반 함수로 호출된 경우
    - Undefined 이다.

```js
// 생성자 함수
function Circle(radius){
    // 이 함수가 new 연산자와 함께 호출되지 않았다면 undefined
    if(!new.target){
	    // new 없이 호출된다면
        // new 연산자와 함께 생성자 함수를 재귀 호출해, 생성된 인스턴스를 반환한다
        return new Circle(radius);
    }
    this.radius = radius;
    this.getDiameter = function(){
        return 2*this.radius;
    };
}

// new 연산자 없이 생성자 함수를 호출해도 new.target을 통해 생성자 함수로 호출된다.
const circle = Circle(5);
console.log(circle.getDiameter()); // 올바른 값 5 호출
```

</div>
</details>

#### Chapter18. 함수와 일급 객체

<details>
<summary>펼쳐보기</summary>
<div markdown="1">

### 18.2 함수 객체의 프로퍼티

#### arguments 프로퍼티

- argument 객체 : length 프로퍼티가 있는 유사 배열 객체 (배열 메서드는 사용 불가, 간접 호출 사용)

```js
function sum(){
	// argument 객체를 배열로 반환
	const array = Array.prototype.slice.call(argument);
	return array.reduce(function(pre, cur){
		return pre+cur;
	},0);
}

console.log(sum(1,2)); //3

//ES6 Rest parameter
function sum(...args){
	return args.reduce((pre, cur)=> pre + cur, 0);
}
console.log(sum(1,2,3,4,5)); //15
```

#### __proto__ 접근자 프로퍼티
- [[Prototype]] 내부 슬롯이 가리키는 프로토타입 객체에 접근하기 위해 사용하는 접근자 프로퍼티

```js
const obj = { a:1 };

// 객체 리터럴 방식으로 생성한 객체의 프로토타입 객체는 Object.prototype
console.log(obj.__proto__ === Object.prototype); // true

console.log(obj.hasOwnProperty('a')); //true
```

#### prototype 프로퍼티
- 생성자 함수가 생성할 인스턴스의 프로토타입 객체를 가리킴

```js
// 함수 객체는 prototype 프로퍼티를 소유한다.
(function(){}).hasOwnProperty('prototype') //true
// 일반 객체는 prototype 프로퍼티를 소유하지 않는다.
({}).hasOwnProperty('prototype') //false
```

</div>
</details>


## 3주차

#### Chapter19 프로토타입
 
<details>
<summary>펼쳐보기</summary>
<div markdown="1">

- 원시 타입을 제외하고는 모두 객체이다. (함수, 배열, 정규표현식)

### 19.1 객체 지향 프로그래밍

#### arguments 프로퍼티

### 19.2 상속과 프로포타입

### 19.3 프로토타입 객체
#### 19.3.1 __proto__ 접근자 프로퍼티

### 19.4 리터럴 표기법에 의해 생성된 객체의 생성자 함수와 프로토타입
### 19.5 프로토타입의 생성 시점
### 19.6 객체 생성 방식과 프로토타입의 결정
### 19.7 프로토타입 체인
### 19.8 오버라이딩과 프로퍼티 섀도잉
### 19.9 프로토타입의 교체
### 19.10 instanceof 연산자
### 19.11 직접 상속
### 19.12 정적 프로퍼티 / 메서드
### 19.13 프로퍼티 존재 확인
### 19.14 프로퍼티 열거

</div>
</details>


#### Chapter20 strict mode

<details>
<summary>펼쳐보기</summary>
<div markdown="1">


</div>
</details>

#### Chapter21

<details>
<summary>펼쳐보기</summary>
<div markdown="1">



</div>
</details>

#### Chapter22 this

<details>
<summary>펼쳐보기</summary>
<div markdown="1">

### 22.1 this 키워드
- 메서드는 자신이 속한 객체의 상태, property를 참조할 수 있어야 한다.
- 이를 위해 자신이 속한 객체를 가리키는 식별자를 참조해야한다.

```js
function Circle(radius){
	// 이 시점에서는 생성자 함수 자신이 생성할 인스턴스를 가리키는 식별자를 알 수 없다.
	????.radius = radius;
}

Circle.prototype.getDiameter = function(){
	// 이 시점에는 생성자 함수 자신이 생성할 인스턴스를 가리키는 식별자를 알 수 없다
	return 2 * ????.radius;
}

// 생성자 함수로 인스턴스를 생성하려면 먼저 생성자 함수를 정의해야한다.
const circle = new Circle(5);
```
- 생성자 함수를 정의하는 시점에서는 인스턴스를 가리키는 식별자를 알 수 없다.

- this : 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수 (self-referencing variable)
	- this 바인딩은 함수 호출 방식에 의해 동적으로 결정된다.

```js
// 전역 this는 전역 객체 window를 가리킨다.
console.log(this); // window

function square(number){
	// 일반 함수 내부에서 this는 전역 객체 window를 가리킨다.
	console.log(this); // window
	return number * number;
}
square(2);

const person = {
	name:'Lee',
	getName(){
		// 메서드 내부에서 this는 메서드를 호출한 객체를 가리킨다.
		console.log(this); // {name:"Lee", getName: f}
		return this.name;
	}
}
console.log(person.getName()); //Lee


function Person(name){
	this.name = name;
	// 생성자 함수 내부에서 this는 생성자 함수가 생성할 인스턴스를 가리킨다. 
	console.log(this); // Person {name:"Lee"}
}
const me = new Person("Lee"); 
```

- this 바인딩은 함수가 호출되는 방식에 따라 결정된다.
- strict mode가 적용된 일반 함수 내에서는 this에 undefined가 바인딩된다.


### 22.2 함수 호출 방식과 this 바인딩
 * 렉시컬 스코프 vs this 바인딩 결정 시기
	- 렉시컬 스코프 (함수의 상위 스코프를 결정) : 함수 정의가 평가 되어 함수 객체가 생성되는 시점
	- this 바인딩 : 함수 호출 시점에 결정

#### 22.2.1 일반 함수 호출
- this에는 `전역 객체`가 바인딩된다. (중첩 함수도 마찬가지)

```js
// var 키워드로 선언한 전역 변수 value는 전역 객체 프로퍼티이다.(const는 아님)
var value = 1;

const obj = {
	value : 100,
	foo(){
		console.log("foo's this:", this); // {value:100, foo:f}
		console.log("foo's this.value:", this.value); // 100

		// 메서드 내에서 정의한 중첩 함수
		function bar(){
			console.log("bar's this:", this); //window
			console.log("bar's this.value:", this.value); //1
		}
		
		// 메서드 내에서 정의한 중첩 함수도 일반 함수로 호출되면 중첩 함수 내부의 this에는 전역 객체가 바인딩된다.
	}
}

obj.foo();
```
- 콜백함수가 일반함수로 호출되면, 콜백 함수 내부에서 this도 전역 객체가 바인딩된다.


```js
var value = 1;

const obj = {
	value : 100,

	// 방법 1
	foo(){
		// this 바인딩을 변수 that에 할당한다.
		const that = this;

		// 콜백 함수 내부에서 this 대신 that을 참조한다.
		setTimeout(function(){
			console.log(that.value); // 100
		}, 100);
	}

	// 방법 2
	foo(){
		// 콜백 함수에 명시적으로 this 바인딩
		setTimeout(function(){
			console.log(this.value); // 100
		}.bind(this), 100);
	}

	// 방법 3
	foo(){
		// 화살표 함수 내부의 this는 상위 스코프의 this를 가리킨다.
		setTimeout(()=>{
			console.log(this.value); // 100
		}, 100);
	}
}

obj.foo();
```

- 중첩함수, 콜백함수는 외부 함수를 돕는 헬퍼 역할을 하고, 일부 로직을 대체한다. 따라서 콜백 함수의 this 바인딩을 메서드의 this 바인딩과 일치시키기 위해 위와 같이 할 수 있다.


#### 22.2.2 메서드 호출
- 메서드 내부의 this에는 `메서드를 호출한 객체`(. 앞에 있는 객체)가 바인딩된다. (소유한 객체가 아님을 주의하자.)

```js
const person = {
	name : "Lee",
	getName(){
		// 메서드 내부의 this는 메서드를 호출한 객체에 바인딩된다.
		return this.name;
	}
}
// 메서드 getName을 호출한 객체는 person이다.
console.log(person.getName());
```
- 메서드는 프로퍼티에 바인딩된 함수이다. 즉, getName 프로퍼티가 가리키는 함수 객체는 person 객체에 포함된 것이 아닌 독립적으로 존대한다. 
	* person 객체의 getName 프로퍼티가 함수 객체를 point하고 있는 개념

- 따라서 메서드를 자유롭게 다른 곳에 할당할 수 있음 (객체 메서드, 일반 변수 등)
```js
const anotherPerson = {
	name: 'Kim'
};
//getName 메서드를 anotherPerson 객체의 메서드로 할당

// getName 메서드를 호출한 객체는 anotherPerson
console.log(anotherPerson.getName()); // Kim

// getName 메서드를 변수에 할당
const getName = person.getName;

// getName 메서드를 일반 함수로 호출
console.log(getName()); // ''
// this.name은 window.name과 같음
```

```js
function Person(name){
	this.name = name;
}
Person.prototype.getName = function(){
	return this.name;
}
const me = new Person("Lee");

// getName 메서드를 호출한 객체는 me
console.log(me.getName()); //Lee

Person.prototype.name = "Kim";

//getName 메서드를 호출한 객체는 Person.prototype
console.log(Person.prototype.getName()); //Kim
```
- Person.prototype도 객체이므로 메서드를 직접 호출 가능하다.


#### 22.2.3 생성자 함수 호출
- 생성자 함수(객체를 생성하는 함수) 내부의 this에는 `생성자 함수가 미래에 생성할 인스턴스`가 바인딩된다.


#### 22.2.4 Function.prototype.apply / call / bind 메서드에 의한 간접 호출
- Function.prototype의 메서드 apply, call, bind
- `첫번째 인수로 전달된 객체`가 this에 바인딩된다.
 
```js
function getThisBinding(){
	console.log(arguments);
	return this;
}

//this 로 사용할 객체
const thisArg = { a:1 };

//getThisBinding 함수를 호출하면서 인수로 전달한 객체를 함수의 this에 바인딩한다.
// apply 메서드는 호출할 함수의 인수를 배열로 묶어 전달한다.
console.log(getThisBinding.apply(thisArg, [1,2,3]));
// Arguments(3) [1,2,3, callee : f, Symbol(Symbol.iterator): f]

// call 메서드는 호출할 함수의 인수를 쉼표로 구분한 리스트 형식으로 전달한다.
console.log(getThisBinding.call(thisArg, 1,2,3));
// Arguments(3) [1,2,3, callee : f, Symbol(Symbol.iterator): f]
```
- apply, call 메서드의 본질적인 기능은 함수를 호출하는 것이다.
- 또한 arguments와 같은 유사 배열 객체에 배열 메서드를 사용할 때 사용하기도 한다.

```js
function getThisBinding(){
	return this;
}

//this로 사용할 객체
const thisArg = { a : 1 }

// bind 메서드는 첫번째 인수로 전달한 thisArg로 this 바인딩이 교체된
// getThisBinding 함수를 새롭게 생성해 반환한다.
console.log(getThisBinding.bind(thisArg)) // getThisBinding

// bind 메서드는 함수를 호출하지는 않으므로 명시적으로 호출해야한다.
console.log(getThisBinding.bind(thisArg)()); // {a:1}
```
- bind는 함수를 호출하지 않는다. 첫번째 인자값으로 전달한 값으로 this 바인딩이 교체된 함수를 새롭게 생성해 반환한다.

- 메서드의 this와 메서드 내부의 중첩/콜백 함수의 this가 불일치되는 문제를 해결할 수 있다.
```js
const person = {
  name:"Lee",
  foo(callback){
    setTimeout(callback, 100); // this는 foo를 호출한 person 객체를 가리킨다.
  }
};

person.foo(function(){
  console.log(`Hi! my name is ${this.name}`) // 그러나 콜백함수가 일반함수로 호출된 시점에서는 this는 전역 객체를 가리킨다
  // 따라서 undefined 호출
})
```
- bind를 활용해 아래처럼 사용할 수 있다.
```js
const person = {
  name:"Lee",
  foo(callback){
    setTimeout(callback.bind(this), 100); // bind 메서드로 callback 함수 내부의 this 바인딩을 전달
  }
};

person.foo(function(){
  console.log(`Hi! my name is ${this.name}`) // Hi! my name is Lee
})
```


</div>
</details>

#### Chapter23

<details>
<summary>펼쳐보기</summary>
<div markdown="1">



</div>
</details>


## 4주차

#### Chapter24

<details>
<summary>펼쳐보기</summary>
<div markdown="1">



</div>
</details>

## 5주차

## 6주차

## 7주차

## 8주차

## 9주차

## 10주차

## 11주차

## 12주차
```
