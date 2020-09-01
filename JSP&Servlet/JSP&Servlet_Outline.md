### 서블릿과 JSP의 기초 개념

**서블릿 Servlet** : Server + Applet의 합성어로 서버에서 실행되는 Applet이란 의미로, 

자바를 이용하여 웹에서 실행되는 프로그램을 작성하는 기술

클라이언트는 서버에 get과 post 두 가지 방식 중 하나로 요청을 합니다. 두 전송방식의 차이점은 다음과 같습니다.

- get 방식 : 주소 창을 타고 넘어가기 때문에 서버로 보내는 데이터를 사용자가 그대로 볼 수 있습니다. 그래서 보안에 취약합니다. 255자 이하의 적은 양의 데이터를 전송합니다.
- post 방식 : html header를 타고 넘어가기 때문에 보안에 강합니다. 255자 이상의 대용량의 데이터를 전송합니다.

서블릿 클래스에는 doGet() 혹은 doPost()가 있는데, 요청 방식에 따라 호출되는 메소드가 달라집니다.

```java
<form action="CallServlet"> // 요청할 서블릿
    <input type="submit" value="전송"> // 클릭하면 서블릿이 요청된다.
</form>
```

전송 방식을 결정해 주려면 method속성값을 <form>태그에 추가하면 됩니다. method 속성값으로 get을 기술하면 doGet() 메소드가, post를 기술하면 doPost() 메소드가 호출됩니다. 전송 방식을 결정하지 않으면 기본값인 get 방식으로 요청을 하게 됩니다.

- <form> 태그를 이용한 get방식 요청의 예

```java
<form method="get" action="CallServlet"> // 요청할 서블릿
    <input type="submit" value="전송"> // 클릭하면 서블릿이 요청된다.
</form>

```

- <a> 태그를 이용한 get방식 요청의 예

```java
<a href="CallServlet"> get 방식의 요청 </a>
```

- 주소 입력란에서 직접 서블릿 요청을 위한 URL을 입력해도 get방식으로 요청한 것으로 인식

서블릿 클래스 메소드의 매개변수

```java
HttpServletRequest request // 클라이언트의 요청을 처리
HttpServletResponse response // 요청 처리 결과를 클라이언트에게 되돌리기(응답하기)위해 사용
```

서버가 요청에 대한 처리를 마치고 클라이언트에게 결과를 되돌려주기 위해서는 response로 부터 PrintWriter형의 출력 스트림 객체를 얻어와야 합니다.

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {

    int num1 = 20;
    int num2 = 10;
    int add = num1 + num2;
    PrintWriter out = response.getWriter();
    out.println("<html><head><title>Addition</title></head>");
    out.println("<body>");
    out.println(num1 + "+" + num2 + "=" +add);
    out.println("</body>");
    out.println("</html>");
}
```

**JSP : Java Server Page**의 줄임말로 자바로 서버 페이지를 작성하기 위한 언어. HTML과 JSP태그(스크립트릿)로 구성되어 화면을 작성하는 데 유리한 웹프로그래밍 기술입니다.

서블릿은 자바 코드 내부에 HTML코드가 들어가는 구조이지만, JSP는 반대로 HTML 문서 내부에 자바 코드가 들어가는 구조입니다.

```html
<body>
<%
int num1 = 10;
int num2 = 20;
int add = num1 + num2;
%>
    <%=num1 %>+<%=num2 %>=<%=add %>
</body>
```

<%@page%> 태그 : 해당 페이지 내에 사용되는 전반적인 환경을 결정해주는 태그

<% %> 태그 : 스크립트릿 scriptlet. 자바 코드 기술

<%= %> 태그 : 표현식. 변수에 저장된 값이나 함수의 결과값을 출력

두 수에 대한 합을 구하는 서블릿 클래스

AdditionServlet03.java

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
    // 두 수에 대한 합을 구하는 자바 코드 기술
    int num1 = 10;
    int num2 = 20;
    int add = num1 + num2;

    // 출력할 데이터를 request 객체의 속성값으로 저장
    request.setAttribute("num1", num1);
    request.setAttribute("num2", num2);
    request.setAttribute("add", add);

    // 서버 상에서 페이지가 이동되는 forward방식으로 "addition03.jsp"페이지로 이동
    RequestDispatcher dispatcher = request.getRequestDispatcher("addition03.jsp");
    dispatcher.forward(request, response);
}
```

addition03.jsp

```java
<body>
    // request객체에 저장된 속성값을 얻어와 출력
    ${num1 }+${num2 }=${add }
</body>
```
