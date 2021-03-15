# 4. 함수

함수는 특정 코드를 하나의 명령으로 실행 할 수 있게 해주는 기능

## function 함수

> function 함수명(매개변수) {
        실행할 소스코드;
        return 반환 값;
}

매개 변수 parameter : 외부에서 값을 받아와서 함수 내부에서 사용할 변수

반환 값 return value : 함수에서 처리된 결과를 반환

인자 argument : 함수를 호출할 때 넣는 값

```jsx
function add(a, b) {
  return a + b;
}
const sum = add(1, 2);
console.log(sum);
```

매개 변수와 반환값은 존재하지 않을 수도 있다.

```jsx
function hello(name) {
  console.log('Hello, ' + name + '!');
}
hello('velopert');
```

## 화살표 함수 : (매개변수) => { }

> const 함수명 = (매개변수) => {
        실행할 소스코드;
        return 반환 값;
}

```jsx
const add = (a, b) => {
  return a + b;
};
console.log(add(1, 2));
```

만약에 위와 같이 코드 블록 내부에서 바로 return 을 하는 경우는 다음과 같이 줄여서 쓸 수도 있습니다.

```jsx
const add = (a, b) => a + b;
console.log(add(1, 2));
```

화살표 함수와 일반 function 으로 만든 함수와의 주요 차이점은 화살표 함수에서 가르키는 this 와 function 에서 가르키는 this 가 서로 다르다는 것이다.
