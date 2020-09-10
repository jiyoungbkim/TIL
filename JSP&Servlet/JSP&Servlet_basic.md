**URL Mapping** : 서블릿을 동작시키기 위해서 실제 자바 클래스 명을 사용하는 대신 문자열을 서블릿 클래스와 매핑시키는 것

URL 매핑을 하는 이유 : 실제 서블릿 클래스를 공개하지 않기 위해서 합니다. 외부에서 서블릿을 요청할 때 서블릿 클래스 이름이 아닌 서블릿 클래스와 매핑된 URL로 접근합니다.

서블릿을 요청하기 위한 URL

http://localhost:8080/컨텍스트 패스/서브릿 요청 URL 패턴(URL Mapping한 주소)

**컨텍스트 패스** : 웹 서버에서 제공하는 다양한 웹 애플리케이션을 구분하기 위해서 사용하는 것

이클립스는 컨텍스트 패스를 프로젝트 단위로 자동 생성해 줍니다.

톰캣서버의 server.xml의 <Context> 태그에서 확인 가능

```java
<Context docBase="web-study-02" path="/web-study-02" 
reloadable="true" source="org.eclipse.jst.jee.server:web-study-02"/>
```

**@WebServlet** : 서블릿 클래스의 요청을 위한 URL 매핑을 보다 쉽게 자바 클래스에서 설정할 수 있도록 제공되는 어노테이션

**응답 객체에 콘텐트 타입 지정하기**

HttpServletResponse객체인 response로 setContentType()메소드를 호출하여 응답할 페이지에 대한 환경 설정을 해주어야 합니다. 결과를 출력할 내용이 한글일 경우 인코딩 방식을 지정하지 않으면 한글이 깨지는 현상이 나타납니다.

```java
response.setContentType("text/html; charset=UTF-8");
```

**출력 스트림 얻어오기**

response객체의 인코딩 형태를 바꿔준 후에는 결과 출력을 위해 출력 스트림을 얻어오는 response.getWriter() 메소드를 호출해야 합니다. 순서는 반드시 인코딩 방식이 지정된 후 얻어와야 제대로 출력이 됩니다. 

스트림이란 : 사용자가 입력한 데이터를 메모리에 저장하는 과정을 입력, 메모리에 저장된 데이터를 사용자가 볼 수 있도록 하는 과정을 출력이라고 하는데 입출력 과정이 가능하도록 하는 객체를 자바에서는 스트림이라고 합니다. 

```java
PrintWriter out = response.getWriter();
```

### 서블릿의 동작 원리

서블릿 컨테이너 : 톰캣은 웹서버이면서 서블릿 컨테이너입니다. 톰캣이 구동되면 자바가상머신이 구동되어 자바 문법을 따르는 서블릿을 처리할 수 있는 환경을 제공하여 서블릿 컨테이너라는 별칭이 붙여있다고 생각하면 될 것입니다. 

### 서블릿의 라이프 사이클

서블릿이 다른 웹 기술보다 주목을 받게 된 이유는 수행 속도가 빠르다는 점입니다. 다른 웹 기술들은 클라이언트의 요청이 있을 때마다 작업을 처음부터 새롭게 하여 제공하지만, 서블릿은 첫 번째 요청인 경우에는 서블릿 클래스를 찾아 메모리에 로딩하여 인스턴스(객체)를 생성합니다. 이때 생성된 서블릿 인스턴스는 메모리에 계속 남아 있게 되므로 이후부터는 이미 메모리에 로딩된 서블릿으로부터 서비스만 받기 때문에 수행속도가 빠른 것입니다. 

1. Instance 생성 : 서블릿 객체 생성
2. init() : 최초로 한번만 호출. 초기화 작업
3. doGet() 혹은 doPost() : 요청될 때마다 호출
4. destroy() : 톰캣 해제시 자원 해제. 서블릿 컨테이너가 종료(톰캣 재가동)되거나 서블릿 내용이 변경되어 다시 컴파일해서 클래스 파일이 바뀌는 경우

### get방식과 post방식

- 형식 : <form>태그의 기본 형식

```java
<form method="get/post" action="호출할서블릿">
```

method : get과 post방식 중에 하나를 선택하여 어떤 방식으로 데이터를 넘겨 줄 것인가를 결정

action : 전송(submit) 버튼을 누르면 action 속성 다음에 기술한 URL에 지정된 파일로 이동

- 서블릿을 get방식으로 요청한 예

```java
<form method="get" action="MethodServlet">
```

- 전송(submit) 버튼 만들기의 예

```java
<input type="submit" value="전송">
```

- 취소(reset) 버튼 만들기의 예

```java
<input type="reset" value="취소">
```

### 쿼리 스트링

쿼리 스트링 : get방식으로 요청했을 때 URL 주소 뒤에 입력 데이터를 함께 제공하는 방법으로 "리소스?이름=값&이름=값"의 형식을 취합니다.

왜 데이터를 궈리 스트링으로 전송하는 걸까요?

웹 프로그램에서는 페이지가 이동되면 현재 페이지의 정보를 다음 페이지에서 전혀 알 수 없습니다. 하지만 페이지 사이에 정보 교환이 필요한 경우가 있기 때문에 제공하는 것이 쿼리 스트링입니다.

- 아이디, 나이를 입력 받기 위한 텍스트 박스의 예

```java
<input type="text" name="id">
<input type="text" name="age">
```

- 아이디 : gildong, 나이 : 27로 입력한 경우

쿼리 스트링인 URL?id=gildong&age=27 형태로 서버 페이지에 전달되고 태그의 name 속성 값이 쿼리 스트링의 이름에 해당되고 입력한 값이 쿼리 스트링의 값에 해당됩니다. 

### 요청 객체(request)와 파라미터 관련 메소드(getParameter)

사용자가 폼에 입력한 값을 서블릿에서 어떻게 얻어올까?

request객체의 getParameter() 메소드를 호출하여 <input> 태그를 통해 입력된 값을 읽어올 수 있습니다. 

원하는 값을 얻기 위해서는 입력 양식의 name 속성 값을 getParameter()의 매개 변수로 기술합니다.

```java
<input type="text" name="id">
													|
													input 태그의 name 속성 값
															|
String id = req.getParameter("id");
//getParameter()의 결과 값인 "gildong"을 String 변수 id에 저장
```

getParameter()는 파라미터 값을 항상 문자열 형태로만 얻어오기 때문에 나이를 int형 변수에 저장해야 할 경우 getParameter()가 텍스트 박스에서 입력 받아온 문자열 형태의 값을 int 형으로 변환해야 합니다. 

Integer.parseInt() : String형을 int형으로 변환하는 메소드

```java
int age = Integer.parseInt(request.getParameter("age"));
```

### 자바스크립트 폼에 입력된 정보가 올바른지 판단하기

나이를 입력받지 않을 경우 공백 문자인 ""가 서블릿에 전송되고 이를 정수 형태로 변환하려고 하면 "java.lang.NumberFormatException"과 같은 예외가 발생합니다. 사용자가 폼에 입력한 데이터가 유효해야만 이를 서버에서 정상 처리할 수 있기 때문에 유효성 체크를 하여 유효하지 않으면 사용자가 다시 데이터를 입력하도록 유도해야 합니다. 이러한 작업은 HTML이나 JSP로는 불가능하고 자바스크립트로만 가능합니다. 

**유효성을 체크하는 자바스크립트 파일(param.js)을 만들어 이를 HTML 문서에서 포함시켜 사용하기**

- 유효성을 체크하는 자바스크립트 함수

```jsx
function check(){
	if(document.form.id.value == ""){
		alert("아이디를 입력해주세요.");
		document.form.id.focus();
		return false;
	} else if (document.form.age.value == ""){
		alert("나이를 입력해주세요.");
		document.form.age.focus();
		return false;
	} else if (isNaN(document.form.age.value)){
		alert("숫자로 입력해주세요.");
		document.form.age.focus();
		return false;
	} else {
		return true;
	}
}
```

- 외부 자바스크립트 파일을 불러오는 HTML 태그

```java
<script type="text/javascript" src="param.js"></script>
```

- 자바스크립트 함수가 호출되도록 onClick이벤트 기술

```java
<input type="submit" value="전송" onClick="return check()">
```

- 자바스크립트에서 표 객체로 접근할 수 있도록 form name을 기술

```java
<form method="get" action="ParamServlet" name="form">
```

### 서블릿에서 요청시 한글 처리

- 한글 출력시 처리

```java
response.setContentType("text/html; charset=UTF-8");
```

- post방식에서의 한글 입력 처리

```java
request.setCharacterEncoding("UTF-8");
```
