# 튜토리얼

교재를 읽어나가기 위해 JavaScript 언어의 기본적인 구성요소를 이해하고 넘어갈 필요가 있습니다. 아래에 나오는 간단한 예제들을 직접 실행해 봅시다. 각 요소들에 대한 자세한 설명은 이어지는 챕터에서 다룹니다.

## 코드의 실행

기본적으로 JavaScript 코드는 세미콜론(`;`)으로 구분된 구문(statement) 단위로 위에서부터 차례대로 실행됩니다. 그러나 제어 흐름, 예외 처리, 함수 호출 등을 만나면 코드의 실행 흐름이 이리저리 옮겨다니기도 합니다.

JavaScript 코드는 REPL이라는 도구를 이용해서 조금씩 실행시킬 수도 있고, 혹은 미리 작성해둔 많은 양의 코드를 한 번에 실행시킬 수도 있습니다. 여기서 REPL(Read-Evaludate-Print-Loop)는 코드를 실행시키고 그 결과를 바로 확인할 수 있는 컴퓨터 프로그램을 총칭합니다. 아래에 나오는 코드 예제를 실행시키려면 JavaScript의 최신 문법을 지원하는 웹 기반 REPL인 [repl.it](https://repl.it/languages/babel)을 이용하세요.

## 기본 문법

### 대소문자의 구분

JavaScript 언어는 모든 부분에서 대소문자 구분을 하기 때문에 주의해야 합니다. 예를 들어 `function`과 `Function`은 JavaScript에서 완전히 다른 의미를 가집니다.

### 세미콜론

JavaScript는 세미콜론(;)을 이용해서 각 구문을 구분합니다.

```js
const a = 1;
const b = 2;

// 혹은 이렇게 할 수도 있습니다만, 좋아 보이지는 않습니다.
const c = 1; const d = 2;
```

특별한 경우가 아니라면, 세미콜론을 쓰고 나서는 개행을 해서 각각의 구문이 구분되어 보일 수 있도록 하는 것이 좋습니다.

### 공백

JavaScript 언어는 공백에 민감하지 않은 언어입니다. 즉, 다른 문법 요소만 잘 지킨다면 공백의 수가 코드의 실행에 별 영향을 미치지 않습니다.[^1]

```js
// 아래 세 구문은 완벽히 똑같은 동작을 합니다.
const x = 1;

const     x      =     1;

const
      x
        =
          1;
```

또한 코드의 동작 여부와는 별개로, 코드를 읽기 쉽도록 공백을 깔끔하게 유지해야 할 필요가 있습니다.

## 주석(comment)

주석은 실행되는 코드는 아니지만, 코드에 부가적인 설명을 넣고 싶을 때 사용합니다.

```js
// 한 줄 주석

/* 여러 줄 주석 */

/*
여러
줄
주석
*/
```

## 값(value)과 그 리터럴(literal)

프로그래밍은 근본적으로 '값'을 다루는 행위라 할 수 있습니다. JavaScript에도 여러가지 값을 표현하는 문법이 있으며, 이를 리터럴(literal)이라고 합니다.

```js
1 // 정수
2.5 // 부동소수점 실수
'hello world' // 작은 따옴표 문자열
"JavaScript" // 큰 따옴표 문자열
true // 참임을 나타내는 진리값
false // 거짓임을 나타내는 진리값
null // '존재하지 않음'을 나타내는 값
undefined // '정의된 적 없음'을 나타내는 값
```

## 값의 타입(type)

JavaScript에서 다루어지는 모든 값은 그 '타입'을 가지고 있습니다. 쉽게 '값의 종류'라고 생각하시면 됩니다. `typeof` 연산자는 피연산자의 타입을 가리키는 문자열을 반환합니다.

```js
typeof 1 // 'number'
typeof 2.5 // 'number'
typeof 'hello world' // 'string'
typeof true // 'boolean'
typeof null // 'object'
typeof undefined // 'undefined'
// ...
```

## 표현식(expression)과 연산자(operator)

표현식이란 JavaScript 문장의 구성요소를 구분하는 하나의 단위로, **값으로 변환될 수 있는 부분**을 가리킵니다.

```js
// 사칙 연산
1 + 3;
2 - 4;
3 * 5;
4 / 6;

// 연산자 우선순위 (operator precedence)
1 + 2 * 3;
(1 + 2) * 3;

// 논리 연산
true || false;
true && false;

// 진리값으로 취급하기
1 || 0;
1 && 0;
```

## 변수(variable)

값을 재사용하기 위해 값에 붙일 이름을 선언하고 그 이름에 값을 대입할 수 있습니다. 이 때 이 이름을 변수(variable)라고 부릅니다. `let` 변수에는 값을 여러 번 다시 대입할 수 있지만, `const` 변수에는 값을 한 번만 대입할 수 있습니다.

```js
// 한 변수의 선언
let v;

// 값의 대입
v = 1;

// 변수의 선언과 값의 대입을 동시에
let x = 1;

// 두 변수의 선언과 대입
let y = 2, z = x + y;

// const 변수
const c = 1;
c = 2; // 에러!

// 선언한 변수를 사용하기
x;
typeof x;
x * z;
```

## 제어 흐름

JavaScript는 특정 조건을 만족할 때에만 코드를 실행시키거나, 혹은 여러 번 실행시킬 수 있는 구문을 제공합니다.

```js
// if 구문
if (2 > 1) {
  console.log('괄호 안의 값이 `true`이면 이 영역의 코드가 실행됩니다.');
} else {
  console.log('괄호 안의 값이 `false`면 이 영역의 코드가 실행됩니다.');
}

// for 구문
for (let i = 0; i < 5; i++) { // (초기값; 조건; 갱신)
  console.log(`이 코드는 ${i + 1}번 째 실행되고 있습니다.`);
}

// while 구문
let i = 0;
while (i < 5) {
  console.log('이 코드는 괄호 안의 값이 `true`인 한 계속 실행됩니다.')
  i++;
}
```

## 함수 (function)

값 뿐만 아니라 코드 뭉치에 이름을 붙여서 **재사용**을 할 수도 있는데, 이를 함수라 부릅니다. JavaScript에는 함수를 선언할 수 있는 여러가지 방법이 있습니다.

```js
// `function` 키워드를 이용한 함수 선언
function add(x, y) {
  return x + y;
}

// arrow function
const multiply = (x, y) => x * y;

// 함수 호출하기
add(1, 2); // 3
multiply(3, 4); // 12
```

JavaScript 및 그 구동 환경에 내장되어 있는 여러가지 함수를 사용해서 사용자와 상호작용을 하는 코드를 작성할 수 있습니다.

```js
// 브라우저 내장 함수인 `prompt`, `console.log`, `alert` 사용하기
const answer = prompt('이름이 무엇인가요?');
console.log(answer);
alert(answer);
```

## 객체

대부분의 프로그래밍 언어는 여러 개의 값을 한꺼번에 담아 통(container)처럼 사용할 수 있는 자료구조를 지원합니다. JavaScript에는 **객체(object)**라는 자료구조가 있습니다.

객체에는 **이름(name)**에 **값(value)**이 연결되어 저장됩니다. 이를 이름-값 쌍(name-value pair), 혹은 객체의 **속성(property)**이라고 합니다. 객체를 사용할 때는 속성 이름을 이용해서, 속성 값을 읽거나 쓸 수 있습니다. 또는 아래와 같이 여러 속성을 한꺼번에 정의할 수도 있습니다.

```js
// 객체의 생성
const obj = {
  x: 0, // 객체의 속성. 속성 이름: x, 속성 값: 0
  y: 1 // 객체의 속성. 속성 이름: y, 속성 값: 1
}

// 객체의 속성에 접근하기
obj.x;
obj['y'];

// 객체의 속성 변경하기
obj.x += 1;
obj['y'] -=1;

// 객체의 속성 삭제하기
delete obj.x;
```

객체의 속성을 통해 사용하는 함수를 **메소드(method)**라고 부릅니다.

```js
const obj = {
  x: 0,
  increaseX: function() {
    this.x = this.x + 1;
  }
};

obj.increaseX();
console.log(obj.x); // 1
```

## 배열

JavaScript에서의 배열은 객체의 일종으로, 다른 객체와는 다르게 특별히 취급됩니다. 배열에 담는 데이터는 객체의 경우와 달리 **요소(element)** 혹은 **항목(item)**이라고 부릅니다. 객체와 마찬가지로 배열 안에 여러 개의 값을 저장할 수 있지만, 배열 요소 간에는 **순서**가 존재하며, 이름 대신에 **인덱스(index)**를 이용해 값에 접근합니다.

```js
// 배열의 생성
const arr = ['one', 'two', 'three'];

// 인덱스를 사용해 배열의 요소(element)에 접근할 수 있습니다.
// 배열 인덱스(index)는 0부터 시작합니다.
arr[0]; // === 'one'
arr[1]; // === 'two'

// 여러 타입의 값이 들어있는 배열
[1, 2, 3, 'a', 'b', {x: 0, y: 0, name: '원점'}];

// 배열에 요소 추가하기
arr.push('four');

// 배열의 요소 삭제하기
arr.splice(3, 1); // 인덱스가 3인 요소부터 시작해서 하나를 삭제합니다.
```

[^1]: 다만, 정말로 공백을 아무렇게나 넣어도 되는 것은 아닙니다. JavaScript에는 몇몇 조건을 만족하면 개행을 세미콜론처럼 취급하는 세미콜론 자동 삽입(ASI, Auto Semicolon Insertion) 기능이 내장되어 있기 때문에 개행을 할 때는 주의해야 합니다.