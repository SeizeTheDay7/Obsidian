
### gpt피셜 email 검사 잘하는 정규식
```js
var emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
```

### Arrow function 문법
```js
const add = (a,b) => {
    return a + b;
}

//매개변수가 1개라면 소괄호도 생략할수있다.
const square = x => { return x*x };

//한줄로 작성 가능한 경우 중괄호와 return 키워드도 생략 가능하다.
const square = x => x*x;
const add = (a,b) => a+b;
```

일반 함수의 this
```js
function 출력() { console.log(this) }

const 객체1 = { main: 출력 }
const 객체2 = { main: 출력 }

객체1.main(); // '객체1'
객체2.main(); // '객체2'
```
