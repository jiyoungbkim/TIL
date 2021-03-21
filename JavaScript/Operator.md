# 2. 연산자

## 단항 연산자

- 증감 연산자 : **`++, --`**
- 부호 연산자 : `**+, -**`

## 산술 연산자

- 사칙 연산자 : **`+,-,*,/`**
- 나머지 연산자 : **`%`**

## 대입 연산자(할당 연산자)

연산자(또는 연산식) 오른쪽의 실행 결과를 왼쪽 변수에 할당하는 연산자

- 숫자 복합 대입 연산자

## 논리연산자

- NOT 논리 부정 연산자 : **`!` *!!true == true**
- AND 그리고, 두 피연산자가 모두 true일 때 true : **`&&`**
- OR 또는, 두 피연산자 중 어느 한 쪽만 true면 true : **`||`**

### 연산 순서 NOT → AND → OR

```jsx
const value = !((true && false) || (true && false) || !false); // false
```

## 단축 평가 (short-circuit evaluation) 논리 계산법

논리 연산자를 사용 할 때에는 무조건 우리가 true 혹은 false 값을 사용해야 되는 것은 아닙니다. 문자열이나 숫자, 객체를 사용 할 수도 있고, 해당 값이 Truthy 하냐 Falsy 하냐에 따라 결과가 달라집니다.

만약 함수에서 animal 값이 제대로 주어졌을 때만 name 을 조회하고, 그렇지 않을때는 그냥 undefined 를 반환하게 하고 싶으면 어떻게 해야 할까요?

```jsx
const dog = {
  name: '멍멍이'
};

function getName(animal) {
  if (animal) {
    return animal.name;
  }
  return undefined;
}

const name = getName();
console.log(name); // undefined
```

### && 연산자로 코드 단축시키기

위의 코드와 이 코드는 완벽히 똑같이 작동하는 코드입니다.

```jsx
function getName(animal) {
  return animal && animal.name;
}
```

이게 작동하는 이유는, A && B 연산자를 사용하게 될 때에는 A 가 Truthy 한 값이라면, B 가 결과값이 됩니다. 반면, A 가 Falsy 한 값이라면 결과는 A 가 됩니다.

```jsx
console.log(true && 'hello'); // hello
console.log(false && 'hello'); // false
console.log('hello' && 'bye'); // bye
console.log(null && 'hello'); // null
console.log(undefined && 'hello'); // undefined
console.log('' && 'hello'); // ''
console.log(0 && 'hello'); // 0
console.log(1 && 'hello'); // hello
console.log(1 && 1); // 1
```

### || 연산자로 코드 단축시키기

|| 연산자는 만약 어떤 값이 Falsy 하다면(값이 없을  대체로 사용 할 값을 지정해줄 때 매우 유용하게 사용 할 수 있습니다.

```jsx
const namelessDog = {
  name: ''
};

function getName(animal) {
  const name = animal && animal.name;
  if (!name) {
    return '이름이 없는 동물입니다';
  }
  return name;
}

const name = getName(namelessDog);
console.log(name); // 이름이 없는 동물입니다.
```

위 코드는 || 연산자를 사용하면 다음과 같이 단축시킬 수 있습니다.

```jsx
function getName(animal) {
  const name = animal && animal.name;
  return name || '이름이 없는 동물입니다.';
}
```

A || B 는 만약 A 가 Truthy 할경우 결과는 A 가 됩니다. 반면, A 가 Falsy 하다면 결과는 B 가 됩니다.

```jsx
console.log(1 || '음?'); // 1
console.log(true || '여기 안본다.'); // true
console.log('와아' || '여기 안봐요'); // 와아
console.log([] || '노노');

console.log(false || 'hello'); // hello
console.log('' || '이름없다'); // 이름없다
console.log(null || '널이다~'); // 널이다~
console.log(undefined || 'defined 되지 않았다!'); // defined 되지 않았다!
console.log(0 || '제로다'); // 제로다
```

## 비교 연산자

- 대소 비교 :  **`<,<=,>,>=`**
- 같음 : **`==` `===`**
- 같지 않음 : **`!=` `!==`**

### == : 값만 비교

- 숫자 1과 문자 '1' 이 동일한 값으로 간주
- 0 과 false 도 같은 값으로 간주
- undefined 와 null 도 같은 값으로 간주

### === : 타입까지 비교

### 문자열 연결 연산자 : +

```jsx
const a = '안녕';
const b = '하세요';
console.log(a + b); // 안녕하세요
```

### 템플릿 리터럴 Templete Literal : `문자열, ${변수명}!`

console.log 를 하게 될 때 우리는 문자열을 조합하기 위해서 + 연산자를 사용했습니다. 이렇게 문자열을 조합 할 때 + 를 사용해도 큰 문제는 없지만, 더욱 편하게 조합을 하는 방법이 있습니다. 바로, ES6 의 템플릿 리터럴 (Template Literal)이라는 문법을 사용하는 것 입니다.

```jsx
function hello(name) {
  return `Hello, ${name}!`;
}
const result = hello('velopert');
console.log(result);
```

- ES6 가 뭔가요?

## 삼항 연산자 : condition ? true : false

> (조건) ? true일 때 실행할 명령 : false일 때 실행할 명령

```jsx
const array = [];
let text = array.length === 0 ? '배열이 비어있습니다' : '배열이 비어있지 않습니다.';

console.log(text); // 배열이 비어있습니다
```

라인의 길이가 너묵 길어진다면 다음과 같이 작성하기도 합니다.

```jsx
const array = [];
let text = array.length === 0 
  ? '배열이 비어있습니다' 
  : '배열이 비어있지 않습니다.';

console.log(text);
```
