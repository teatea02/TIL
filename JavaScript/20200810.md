# var, let, const의 차이점
요약하자면
- `var`은 `function-scoped`이다.
- `let`, `const`는 `block-scoped`이다.
- `var`은 변수 재선언 가능 / `let`, `const`는 변수 재선언 불가능
- `const`는 변수 재할당도 불가능
## `var` - function-scoped
```javascript
for(var j=0; j<10; j++) {
  console.log('j', j)
}
console.log('after loop j is ', j) // after loop j is 10
```
`var`은 `function-scoped`이므로, 위의 코드에서 for문 안에서 선언한 `var j` 변수는 for문 밖에서 정상적으로 사용된다.
```javascript
function counter () {
  for(var i=0; i<10; i++) {
    console.log('i', i)
  }
}
counter()
console.log('after loop i is', i) // ReferenceError: i is not defined
```
위 코드의 경우 `var i`가 function안에서 선언되었기 때문에, function밖에서 i 변수를 사용하려하면 `ReferenceError`가 발생하게된다.

## `let`, `const` - blocked-scoped
`let`과 `const`는 es2015에서 추가되었다.
```javascript
function fn() {
  var a = 1;
  let b = 2;
  console.log(a); // 1출력
  console.log(b); // 2출력
  //함수를 벗어나면 a,b둘다 메모리에서 해제됨
}
fn();

console.log(a); // ReferenceError발생
console.log(b); // ReferenceError발생
```
`var`은 `function-scoped`, `let`은 `block-scoped`이므로 함수안에서 선언한 두 변수는 함수 밖에서 호출할 경우 `ReferenceError`가 발생한다.
```javascript
if(true) {
  var a2 = 1;
  let b2 = 2;
  console.log(a2); // 1출력
  console.log(b2); // 2출력
  //a2는 function-scoped이기 때문에 function내부에 선언된게 아닐 경우 전역 변수로 hoisting됨
  //b2는 block-scoped이기 때문에 if를 벗어나면 메모리에서 해제됨
}

console.log(a2); // 1출력
console.log(b2); // ReferenceError발생
```
`var`은 `function-scoped`이므로 if문 block안에서 선언한 후 바깥에서 호출해도 문제가 발생하지 않는다. 하지만 `let`은 `block-scoped`이므로 if문 block밖에서 호출하면 `ReferenceError`가 발생한다.
```javascript
var a = 1;
var a = 2;
console.log(a); // 2출력
//이미 선언된 변수로 재선언해도 에러가 발생하지 않음

let a = 1;
let a = 2; //SyntaxError: Identifier 'a' has already been declared
console.log(a);
//반면 let의 경우 에러 발생
```
또한, `var`은 변수 재선언이 가능하지만 `let`은 변수 재선언이 불가능하다.
## `let` vs. `const`
`let`과 `const`의 차이점은 `mutablity`에 있다.
```javascript
// let
let a = 'test'
let a = 'test2' // Uncaught SyntaxError: Identifier 'a' has already been declared
a = 'test3'     // 가능

// const
const b = 'test'
const b = 'test2' // Uncaught SyntaxError: Identifier 'a' has already been declared
b = 'test3'    // Uncaught TypeError:Assignment to constant variable.
```
`let`은 변수에 재할당이 가능하지만, `const`는 변수의 재선언, 재할당이 모두 불가능하다.
## `var`, `let`, `const`를 생략한 변수 선언?
자바스크립트는 변수 선언을 다음과 같이 매우 유연하게 할 수 있다.
```javascript
var a = 5;
 
b = 10;
 
console.log(a+b); // 15
```
이때, `var`을 사용한 변수 선언과 그렇지 않은 경우는 변수의 scope 범위에서 차이점이 있다.
```javascript
a = 3;
 
function add(){    
    var a = 5;
    console.log(a);
}
 
add(); // 5
console.log(a); // 3
```
`var`은 `function-scoped`이므로 위와 같은 결과가 발생한다
```javascript
a = 3;
 
function add(){    
    a = 5;
    console.log(a);
}
 
add(); // 5
console.log(a); // 5
```
`var`을 생략한 위의 경우, `a = 5`라는 선언은 add() function안의 지역 변수뿐만 아니라 전역 객체 window의 a를 전부 5로 초기화해버린다.
# 참고자료
- [var를 사용한 변수 선언과 var를 생략하는 변수 선언의 차이](https://reshoe.tistory.com/11)
- [var, let, const 차이점은?](https://gist.github.com/LeoHeo/7c2a2a6dbcf80becaaa1e61e90091e5d)
- [자바스크립트 var, let 차이점](https://m.blog.naver.com/PostView.nhn?blogId=rnjsrldnd123&logNo=221502769952&proxyReferer=https:%2F%2Fwww.google.com%2F)
- [let과 var의 성능 비교](https://gomugom.github.io/let-vs-var-performance-compare/)