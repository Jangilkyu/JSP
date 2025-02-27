# 스크립트

# 스크립트 태그의 종류

## 스크립트 태그
- `*<% %*>`을 사용한다.
- JSP페이지가 서블릿 프로그램에서 서블릿 클래스로 변환할 때
    - JSP컨테이너가 자바 코드가 삽입되어 있는 스크립트 태그를 처리하고 나머지는 HTML 코드나 일반 텍스트로 간주한다.

|스크립트 태그|형식|설명|
|----|----|----|
|선언문(declaration)|<%! ... %>|자바 변수나 메소드를 정의하는데 사용|
|스크립틀릿(scriptlet)|<% ... %>|자바 로직코드를 작성하는데 사용
|표현문(expression)|<%= ... %>|변수,계산식,메소드 호출 결과를 문자열 형태로 출력하는 데 사용|

# 선언문 태그
- 변수 및 메소드를 선언
    - 변수 - `전역변수`로 사용
    - 메소드 - `전역 메소드`로 사용

```jsp
<%-- 선언부 --%>
<%-- 선언문 태그를 사용하여 자바의 변수와 메소드를 정의 - 멤버변수 영역 --%>
<%! 
	int count = 3;

	String makeItLower(String data){
		return data.toLowerCase();
	}
%>
```

# 스크립틀릿 태그
- 자바 코드로 이루어진 로직 부분을 표현
- `out 객체`를 사용하지 않고도 쉽게 HTML 응답을 만들어 낼 수 있다.

```jsp
<%-- 처리부 --%>
<%-- 스크립틀릿 태그로 자바 로직 코드 작성 - 지역변수 영역 --%>
<%
	int year = 2021;
	out.print("year:" + year + "<br>");
	out.print("count:" + count + "<br>");
	
	for(int i = 1; i <= count; i++){
		out.println(i + "<br>");
	}
%>
```

|선언문 태그 | 스크립틀릿 태그|
|----|----|
|변수뿐만 아니라 메소드를 선언할 수 있습니다.| 스크립틀릿 태그는 메소드 없이 변수만을 선언할 수 있습니다.|
|서블릿 프로그램으로 변환될 때 _jspService()메소드 외부에 배치됩니다.|서블릿 
프로그램으로 변환될 때 _jspService()메소드 내부에 비치됩니다.|

# 표현문 태그
- 웹 브라우저에 출력할 부분을 표현
- `표현문 태그`에 숫자, 문자,불린(boolean)등의 기본 데이터 타입과 자바 객체 타입도 사용 가능하다. 

```jsp
<%-- 출력부 --%>
<%--표현문 태그로 선언문의 메소드를 호출하여 문자열 형태로 출력 --%>
<%= makeItLower("HELLO WORLD") %>
```