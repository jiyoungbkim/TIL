# 3. 제어문

## 조건문

### if 문

> if (조건) {
         조건이 참일 때 실행되는 명령문
}

- if -else 문
- if -else if 문
- 중첩 if 문

### switch 문

> switch (조건) {
        case 값 1 :
                   조건식의 결과가 1 일 때 실행되는 명령문
                   Break ;
        case 값 2 :
                   조건식의 결과가 2 일 때 실행되는 명령문
                   Break ;
        default : 
                   조건식의 결과가 일치하는 case문이 없을 때 실행되는 명령문
}

```java
// case문은 한 줄에 하나씩 쓰던, 한 줄에 붙여서 쓰던 상관없다.
switch (month) {
		case 3:
		case 4:
		case 5:
				// 실행문
				break;
		case 6: case 7: case 8:
				// 실행문
				break;
```

break문은 각 case문의 영역을 구분하는 역할을 하는데, 생략하면 다른 break문을 만나거나 switch문 블럭의 끝을 만날 때까지 나오는 모든 문장들을 수행한다. 각 case문의 마지막에 break문을 빼먹는 실수를 하지 않도록 주의한다. 그러나 경우에 따라서는 고의적으로 break문을 생략하는 경우도 있다.

```java
switch (level) {
		case 3:
				grantDelete(); // 삭제 권한을 준다
		case 2:
				grantWrite(); // 쓰기 권한을 준다
		case 3:
				grantRead(); // 읽기 권한을 준다
```

로그인한 사용자의 등급(level)을 체크하여, 등급에 맞는 권한을 부여하는 방식. 등급이 3이면 모든 권한 1이면 읽기권한만 가지게 된다.

- switch문의 제약 조건
