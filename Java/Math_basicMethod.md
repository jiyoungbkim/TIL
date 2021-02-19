## Math 클래스
### 소수점 n번째 자리까지 반올림하기 : long Math.round(double*10^n)
/ int Math.round(float*10^n)

```java
double pie = 3.14159265358979;
System.out.println(Math.round(pie)); //결과 : 3
System.out.println(Math.round(pie*100)/100.0); //결과 : 3.14
System.out.println(Math.round(pie*1000)/1000.0); //결과 : 3.142
```

### 소수점 n번째 자리까지 반올림하기 : String String.format()

리턴되는 문자열 형태를 지정하는 함수
```java
double pie = 3.14159265358979;
double money = 4424.243423;
System.out.println(String.format("%.2f", pie)); //결과 : 3.14
System.out.println(String.format("%.3f", pie)); //결과 : 3.142
System.out.println(String.format("%,.3f", money)); //결과 : 4,424.243
```

Math.round()와 String.format()차이점

Math.round()함수는 소수점아래가 0일경우 절삭하지만 String.format은 절삭하지 않고 그대로 리턴

```java
double money = 5000.000;
System.out.println(Math.round(money*1000)/1000); //결과 5000
System.out.println(String.format("%.3f", money)); //결과 : 5000.000
```

### 올림, 내림 : double Math.ceil(), Math.floor()

### x의 n제곱 : double Math.pow(double x, double n);

```java
double target = Math.pow(5, 2); //5의제곱
System.out.println("5의 제곱은 : "+target); // 25.0
```

### 제곱근(루트)구하기 : double Math.sqrt(double x);
```java
double target = Math.sqrt(25); //25의 제곱근
System.out.println("25의 제곱근 : "+ target); // 5.0
```

### 최대값 : int Math.max(int a, int b);

### 최소값 : int Math.min(int a, int b);

### 절대값 : int Math.abs(int i);

### 임의의 수를 얻기 : double Math.random()

```java
int com = (int)(Math.random() * 9) + 1; // 1~9중 하나가 com에 저장
```
