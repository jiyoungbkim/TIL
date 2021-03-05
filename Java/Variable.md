# 1. 변수

## 변수(Variable)

하나의 값을 저장하기 위한 공간

### 변수 명명규칙(Naming Convention)

- 식별자

    1. 대소문자가 구분되며, 길이에 제한이 없다.

    2. 예약어(keyword 혹은 Reserved word)를 사용해서는 안된다.

    3. 숫자로 시작해서는 안된다.

    4. 특수문자는 '_'와 '$'만을 허용한다.

- 권장 규칙
    - 이외에도 개발자들에게 권장되는 규칙은 아래와 같다.

    1. 클래스 이름의 첫 글자는 항상 대문자로 한다. (변수와 메소드 이름의 첫 글자는 항상 소문자로 한다.)

    2. 여러 단어로 이루어진 이름은 두번째 단어의 첫 글자를 대문자로 한다. (Camel case)

    3. 상수의 이름은 모두 대문자로 하며, 여러 단어로 이루어진 경우 '_'로 구분한다.

## 변수의 타입

- 기본형과 참조형

    **1. 기본형(*Primitive type)**

    기본형 변수는 계산을 위한 실제 값(data)을 저장한다.

    - 논리형 : boolean(1byte, default: false)
    - 문자형 : char(2byte : Java에서는 Unicode로 문자 표현)
    - 정수형 : byte(1byte), short(2byte), **int(4byte),** long(8byte)
    - 실수형 : float(4byte), **double(8byte)**

    *Primitive : 원초적인, 원시적인, 가장 기초적인

    **2. 참조형(Reference type)**

    - 기본형을 제외한 나머지 타입으로, 객체의 주소를 저장한다.
    - 모든 참조형 변수는 종류에 관계없이 null 또는 4byte의 객체 주소를 저장한다.

### 참조변수의 초기화

```java
Date today = new Date(); // Date 객체를 생성해서, 그 주소를 today에 저장
```

**상수와 리터럴**

상수(constant) : 값을 한번만 저장할 수 있는 공간. 상수를 선언하는 방법은 변수의 타입 앞에 키워드 'final'을 붙여주기만 하면 된다.

```java
final int WIDTH = 20; // 폭
final int HEIGHT = 10; // 높이

int triangleArea = (WIDTH * HEIGHT) / 2 // 삼각형의 면적을 구하는 공식
int rectangleArea = WIDTH * HEIGHT // 사각형의 면적을 구하는 공식
```

리터럴(literal) : 그 자체로 값을 의미하는 것

리터럴에 접미사가 붙는 타입은 long, float, double뿐인데, doble은 생략가능하므로 long(L)과 float(F,f)의 리터럴에 접미사를 붙이는 것만 신경쓰면 된다.

### 문자열 결합

덧셈 연산자는 피연산자가 모두 숫자일 때는 두 수를 더하지만, 피연산자 중 어느 한 쪽이 String이면 나머지 한 쪽을 먼저 String으로 변환한 다음 두 String을 결합한다.

문자열 + anytype → 문자열 + 문자열 → 문자열

### 화면에서 입력받기: Scanner

```java
import java.util.Scanner; // Scanner를 사용하기 위해 추가

public class ScannerEx {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(); // 정수를 입력받아서 변수 n에 저장
		}
}
```

## 형변환 Casting(문자형,정수형,실수형)

## 문자 → 숫자

### 1. String to Int : Integer.parseInt( String ), Integer.valueOf( String )

```java
String s_num = "10";
int i_num = Integer.parseInt(s_num); //String -> Int 1번방식
int i_num2 = Integer.valueOf(s_num); //String -> Int 2번방식
```

### 2. String to Double, Float : Double.valueOf( String ), Float.valueOf( String )

```java
String s_num = "10";
double d_num = Double.valueOf(s_num); //String -> Double
float f_num = Float.valueOf(s_num); //String -> Float
```

### 3. String to Long, Short : Long.parseLong( String ), Short.parseShort( String )

```java
String s_num = "10";
long l_num = Long.parseLong(s_num); //String -> Long
short sh_num = Short.parseShort(s_num); //String -> Short
```

## 숫자 → 문자

### 1. Int to String : String.valueOf( int ), Integer.toString( int )

```java
int i_num = 10;
String s_num;
		
s_num = String.valueOf(i_num); //문자 -> 숫자 1번방식
s_num = Integer.toString(i_num); //문자 -> 숫자 2번방식
s_num = ""+i_num; //문자 -> 숫자 3번방식
```

### 2. Double/Float to String : String.valueOf( float/double ), Float/Double.toString( float/double )

```java
float f_num = 10.10;
double d_num = 10.10;
		
String s_num;

s_num = String.valueOf(f_num); //Float -> String 1번방식
s_num = Float.toString(f_num); //Float -> String 2번방식
		
s_num = String.valueOf(d_num); //Double -> String 1번방식
s_num = Double.toString(d_num); //Double -> String 2번방식
```

## 정수 ←→ 실수

### 1. Double/Float to Int : (int)double/float

```java
double d_num = 10.101010;
float f_num = 10.1010

int i_num;
i_num = (int)d_num; //Double-> Int
i_num = (int)f_num; //Float -> Int
```

### 2. Int to Double,Float : (double/float)int

```java
int i_num = 10;
	
double d_num = (double)i_num; //Int -> Double
float f_num = (float)i_num; //Int -> Float
```

### 아스키코드, 유니코드를 문자나 숫자로 변환하기: (int), (char)

문자 → 숫자 (int)

어떤 문자의 유니코드를 알고 싶으면, char형 변수에 저장된 값을 정수형(int)으로 변환하면 된다.

```java
char ch = 'A';
int code = (int)ch; // 65
```

숫자 → 문자 (char)

```java
int code = 65;
char ch = (char)code; // 'A'
```
