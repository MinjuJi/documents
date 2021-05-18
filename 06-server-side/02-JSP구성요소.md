# JSP 구성요소

## 디렉티브
- JSP페이지에 대한 설정 정보를 정의한다.

### page 디렉티브
```jsp
  <%@ page 속성="속성값" />
  <%-- jsp페이지에 대한 정보를 설정한다. -->
```
- page 디렉티브의 주요 속성
  + contentType
    * 응답컨텐츠의 타입 및 인코딩방식을 설정
    * 설정예)
    ```jsp
      <% page contentType="text/html; charset=utf-8" %>
      <% page contentType="text/xml; charset=utf-8" %>
      <% page contentType="application/json; charset=utf-8" %>
      <% page contentType="text/plain; charset=utf-8" %>
    ```
  + pageEncoding
    * jsp 파일을 저장할 때 사용할 인코딩방식을 설정
    * 설정예)
    ```jsp
      <%@ page pageEncoding="utf-8" %>
    ```
  + import
    * jsp 파일에서 사용되는 클래스에 대한 import문 역할 수행
    * 설정예)
    ```jsp
      <% page import="java.util.List"%>
      <% page import="java.util.List,java.util.ArrayList"%>
    ```
  + errorPage
    * jsp파일 실행 중 에러 발생시 표시할 페이지를 설정
    * 설정예)
    ```jsp
      <% page errorPage="serverError.jsp" %>
    ```
  + isErrorPage
    * 에러페이지로 사용되는 jsp 페이지인지 여부를 설정
    * 설정예)
    ```jsp
      <% page isErrorPage="true" %>
    ```
  + trimDirectiveWhiteSpace
    * 디렉티브 정의로 발생되는 빈줄을 삭제할지 여부를 설정
    * 설정예)
    ```jsp
      <% page trimDirectiveWhiteSpace="true" %>
    ```

### include 디렉티브
```jsp
  <%@ include file="현재페이지에 포함시킬 jsp파일의 경로와 이름" />
```
- JSP 페이지에 다른 jsp페이지를 포함시킨다.
- include 디렉티브의 주요 속성
  + file
    * 현재 페이지에 포함시킬 jsp파일의 경로와 이름을 지정한다.
    * 설정예)
    ```jsp
      <%@ include file="common/header.jsp" %>
    ```
    
### taglib 디렉티브
```jsp
  <%@ taglib prefix="속성값" uri="속성값" />
```
- JSP 페이지에서 사용할 커스텀 태그 라이브러리나 JSP표준태그 라이브러리를 정의한다.
- taglib 디렉티브의 주요 속성
  + prefix
    * 태그 라이브러리 적용시 사용되는 별칭을 지정한다.
    * 설정예)
    ```jsp
      <%@ prefix="c" taglib="http://java.sun.com/jsp/jstl/core" %>
      <%@ prefix="fmt" taglib="http://java.sun.com/jsp/jstl/fmt" %>
      
      <c:out value="값" />
      <fmt:formatNumber value="값" />
    ```
  + uri
    * jsp페이지에서 사용할 태그라이브러리식별자를 정의한다.
    ```jsp
      <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
      <%@ prefix="fmt" taglib="http://java.sun.com/jsp/jstl/fmt" %>
    ```

## 스크립트 요소
- JSP에서 로직을 수행하거나, 변수의 값을 출력에 포함시키거나, 메소드를 정의하거나 할 때 사용한다.

### 스크립트릿
```jsp
  <%
    자바코드를 작성할 수 있다.
  %>
```
- JSP 페이지에서 자바코드를 실행할 수 있게 한다.
- JSP가 자바파일로 변환될 때, \_jspService메소드내에 포함되는 코드를 작성할 수 있게 한다.
- 사용예)
```jsp
  <%
    int x = 10;
    EmployeeService service = new EmployeeService();
    
    // 접근제한자를 가지는 변수를 정의할 수 없다.
    private int y = 10;	// 오류
    
    // 메소드를 정의할 수 없다.
    private void log(Employee emp) {
      System.out.println(emp.getName());
    }
  %>
```
### 표현식
```jsp
  <태그><%=값 %></태그>
  <태그><%=값을 반환하는 메소드 %></태그>
```
- 응답컨텐츠에 포함되어서 클라이언트로 전송되게 한다.
- 변수에 저장된 값이나, 메소드의 실행결과로 획득되는 반환값을 표현식에서 사용할 수 있다.
- 사용예)
```jsp
  <% 
    int empNo = 100;
    EmployeeService employeeService = EmployeeService.getInstance();
    Employee emp = employeeService.getEmployeeDetailInfo(empNo);
  %>
  <table>
    <tr>
      <th>직원이름</th><td><%=emp.getName() %></td>
      <th>소속부서번호</th><td><a href="dept.jsp?deptno=<%=emp.getDeptNo() %>"><%=emp.getDeptNo() %></a></td>
      <th>전화번호</th><td><input type="text" value="<%=emp.getTel() %>" /></td>
    </tr>
  </table>
```
### 선언식
```jsp
  <%!
    private DecimalFormat df = new DecimalFormat("##,###");
    private String numberToCurrency(long number) {
      return df.format(number);
    }
  %>
```
- JSP페이지에 새로운 필드나 새로운 메소드를 정의(선언)할 때 사용한다.
- 사용빈도는 그렇게 높지 않다.

### 주석
```jsp
  <%-- jsp 주석을 여기에 적는다. -->
  
  <%-- 아래의 모든 코드는 주석처리되어서 실행되지 않는다. --%>
  <%--
    int bookNo = Integer.parseInt(request.getParameter("no"));
    BookService bookService = BookService.getInstance();
    Book book = bookService.getBookInfo(bookNo);
  --%>
```
- jsp주석을 추가한다.










