## String 클래스 기본 메소드

### 메소드의 기능 : 리턴타입 .메소드명( 매개변수 타입 )

문자열 동일성 검사 : boolean .equals( String )

```java
String str1 = "java";
String str2 = "Java";
boolean equals = str1.equals(str2); //equalsIgnoreCase() 대소문자 구분없이 비교
```

문자열 사전식 순서 : int .compareTo( String )

```java
String str1 = "absolute";
String str2 = "base";
int result = str1.compareTo(str2); 
//str1의 사전식 순서가 빠르면 음수, 같으면 0, 느리면 양수를 반환
```

문자열 길이 : int .length()

```java
String str = "abcdef";
int length = str.length();
```

특정 위치의 문자 : char .charAt( int )

```java
String str = "ABCDEFG";
char ch = str.charAt(2); //index 2번 위치의 문자
```

지정한 문자의 위치 검색 : int indexOf( char )

```java
String str = "abcdef";
int index = str.indexOf("d");//없으면 return -1
```

지정된 범위의 부분 문자열 : String .substring(int, int)

```java
String str = "ABCDEF";
String substr = str.substring(0, 2); // 0<=...<2
```
