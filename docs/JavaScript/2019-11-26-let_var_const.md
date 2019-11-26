# var, let , const의 차이점
var는 기존에 있던 문법이고 `let`과 `const`는 `es2015`부터 추가되었다.
세 가지 모두 변수를 선언한다는 공통점이 있다. 세 가지의 차이점에 대해서 알아보자!

---
## var
var를 통해 변수를 선언할 수있지만 이미 만들어진 변수이름으로 재선언을 하여도 에러가 나지 않는다.
 <!-- (hosting으로 인해 global variable로 되기 때문에) -->
```javascript
// 이미 만들어진 변수이름으로 재선언했는데 아무런 문제가 발생하지 않는다.
var a = 'hello'
var a = 'thi'
```
// hoisting으로 인해 ReferenceError에러가 안난다.
c = 'test'
var c

## let, const
`let`과 `const` 사용하면 `var`와 다르게 **변수를 재선언 할 수 없다** 는 공통점이 있다.**하지만 let은 변수에 재할당이 가능하고 const는 재할당이 불가능하다!**

```javascript
// let
let a = 'hi'
let a = 'hello' // Uncaught SyntaxError: Identifier 'a' has already been declared
a = 'hello'     // 가능

// const
const b = 'hi'
const b = 'hello' // Uncaught SyntaxError: Identifier 'a' has already been declared
b = 'hello'    // Uncaught TypeError:Assignment to constant variable.
```




Reference
 - https://gist.github.com/LeoHeo/7c2a2a6dbcf80becaaa1e61e90091e5d
