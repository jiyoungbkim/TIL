## String 클래스 기본 메소드

### 메소드의 기능 : 리턴타입 .메소드명( 매개변수 타입 )

- 문자열 동일성 검사 : boolean .equals( String )

```java
String str1 = "java";
String str2 = "Java";
boolean equals = str1.equals(str2); //equalsIgnoreCase() 대소문자 구분없이 비교
```

- 문자열 사전식 순서 : int .compareTo( String )

```java
String str1 = "absolute";
String str2 = "base";
int result = str1.compareTo(str2); 
//str1의 사전식 순서가 빠르면 음수, 같으면 0, 느리면 양수를 반환
```

- 문자열 길이 : int .length()

```java
String str = "abcdef";
int length = str.length();
```

- 특정 위치의 문자 : char .charAt( int )

```java
String str = "ABCDEFG";
char ch = str.charAt(2); //index 2번 위치의 문자
```

- 지정한 문자의 위치 검색 : int .indexOf( char ) .lastIndexOf( char )

```java
String str = "abcdef";
int index = str.indexOf("d");//없으면 return -1
int index2 = str.lastIndexOf("d"); // 뒤에서부터 찾아서 처음 찾은 해당 문자열의 인덱스를 반환
```

- 지정된 범위의 부분 문자열 : String .substring(int, int)

```java
String str = "ABCDEF";
String substr = str.substring(0, 2); // 0<=...<2
```

- 특정문자를 기준으로 문자열을 잘라서 배열에 넣어줌 : String[] .split( String )

```java
String str = "A,B,C,D";
String[] array = str.split(",");

//결과값 
//array[0] = A
//array[1] = B
//array[2] = C
//array[3] = D
```

- char타입을 String 타입으로 변환 : String Chracter.toString( char )

```java
String tostr = Character.toString(str.charAt(i));
```

- 바꾸고 싶은 문자열로 변환 : String .replace( String, String )
```java
String str = "abcdef";
str.replace("a","g"); // "gbcdef"
```

replace(기존문자, 바꿀문자)

replaceAll(정규식, 바꿀문자) : 특수문자로 변환이 어려움. 예를 들어 .마침표를 특수문자가 아닌 정규식(모든 문자를 의미)으로 인식한다

replaceFirst(기존문자, 바꿀문자) : 기존문자가 처음으로 해당할 때만 변환해준다.

- 문자열 검색 : boolean .contains( String )

```java
String str = "abcdef";
if(str.contains("a")) {
		System.out.println("true");
}
```
