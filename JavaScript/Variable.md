# 1. 변수

- 자바스크립트 스타일 가이드

## 변수와 상수

- 변수 선언의 규칙

### 이제는 더 이상 사용하지마세요, var

- 모오오오던 자바스크립트에서는 더 이상 사용하지 않습니다.

### 변수 : let

변수는, 바뀔수 있는 값을 말합니다. 한번 값을 선언하고 나서 바꿀 수 있습니다.

사용 하실 때 주의 할 점은 한번 선언했으면 똑같은 이름으로 선언하지 못합니다.

```jsx
let value = 1;
let value = 2; // error
```

### 상수 : const

상수는, 한번 선언하고 값이 바뀌지 않는 값을 의미합니다. 즉, 값이 고정적이죠. 상수를 선언 할 때에는 다음과 같이 선언합니다.

상수를 선언하고 나면, 값을 바꿀 수 없습니다.

```jsx
const a = 1;
a = 2; // error
```

상수를 선언할 때에도 마찬가지로 한번 선언했으면 같은 이름으로 선언 할 수 없습니다.

```jsx
const a = 1;
const a = 2; // error
```

let 과 const 는 다른 블록 범위에서는 똑같은 이름으로 선언 할 수도 있다.

```jsx
const a = 1;
if (true) {
  const a = 2;
  console.log('if문 안의 a 값은 ' + a); // if문의 안의 a 값은 2
}
console.log('if문 밖의 a 값은 ' + a); // if문 밖의 a 값은 1
```

## 데이터 타입

### 숫자(Number) : let valueName = 숫자;

```jsx
let value = 1;
```

### 문자열(String) : let valueName = ' ' or " ";

작은 따옴표 혹은 큰 따옴표로 감싸서 선언합니다.

```jsx
let text = 'hello';
let name = "좌봐스크립트";
```

### 참/거짓 (Boolean) : true / false;

```jsx
let good = true;
let loading = false;
```

### null : 없음

null 은 주로, 이 값이 없다! 라고 선언을 할 때 사용합니다.

```jsx
let friend = null;
```

### undefined : 미설정

반면, undefined 는 아직 값이 설정되지 않은 것을 의미합니다.

```jsx
let criminal;
console.log(criminal);
```

### Truthy and Falsy : false 같은거, true 같은거

null 체크시

```jsx
if (person === undefined || person === null)
```

이렇게 person 이 undefined 이거나, null 인 상황을 대비하려면 위와 같이 코드를 작성해야하는데요, 여기서 위 코드는 다음과 같이 축약해서 작성 할 수 있답니다.

```jsx
if (!person)
```

Falsy 한 값

```jsx
console.log(!undefined);
console.log(!null);
console.log(!0);
console.log(!'');
console.log(!NaN);
```

Truthy 한 값 : Falsy한 값을 제외한 모든 값

```jsx
console.log(!3);
console.log(!'hello');
console.log(!['array?']);
console.log(![]);
console.log(!{ value: 1 }); // 객체
```

특정 값이 Truthy 한 값이라면 true, 그렇지 않다면 false 로 값을 표현하는 것을 구현해보겠습니다.

삼항연산자를 사용하면 쉽게 value 값의 존재 유무에 따라 쉽게 true 및 false 로 전환이 가능

그런데, 이를 더 쉽게 할 수도 있습니다.

!value 는 false 가 되고, 여기에 !false 는 true 가 되어서, 결과는 true 가 됩니다.

```jsx
const value = { a: 1 };

// const truthy = value ? true : false;
const truthy = !!value;
```

### NaN

Not a Number : 숫자가 아님을 나타냅니다.

보통 NaN 은 문자열을 숫자로 변환하는 자바스크립트 기본함수 parseInt 라는 함수를 사용하게 될 때 볼 수 있습니다.

```jsx
const num = parseInt('15', 10); // 10진수 15를 숫자로 변환하겠다는 의미
console.log(num); // 10
const notnum = parseInt('야호~', 10);
console.log(notnum); // NaN
```
