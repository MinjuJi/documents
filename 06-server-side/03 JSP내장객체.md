# JSP의 내장객체
- JSP 페이지가 자바로 변환될 때 _jspService메소드에서 사용가능한 객체
- JSP는 웹 애플리케이션 개발에 필요한 객체를 미리 생성(획득)해서 적절한 변수에 저장하고, 스크립트릿에서 사용가능한 상태로 초기화시켜놓는다.

| 변수명 | 클래스명 | 설명 |
| --- | --- | --- |
| request | HttpServletRequest | 클라이언트가 보낸 요청메세지 정보를 저장한다. |
| response | HttpServletResponse 클라이언트로 보낼 응답메세지 정보를 저장한다. |
| session | HttpSession | 세션정보를 저장한다.(로그인처리와 관련) |
| out | JspWriter | 응답컨텐츠를 클라이언트로 출력하는 스트림 |
| application | ServletContext | 웹 애플리케이션 프로젝트 정보를 저장한다. |
| config | ServletConfig | JSP 페이지와 관련된 설정 정보를 저장한다. | 
| pageContext| PageContext | JSP 페이지에 대한 정보를 저장한다. |
| exception | Throwable | 에러정보를 저장한다.(isErrorPage="true")에서만 사용가능 |
| page | Object | JSP 페이지를 구현한 자바객체가 저장된다. |

- HttpServletRequest
 + request 변수에 저장된다.
 + 클라이언트가 서버로 보낸 요청 메세지를 저장하고 있다
 + 요청메세지정보를 획득할 수 있는 다양한 getXXX() 메소드를 제공한다.
 + 주요 메소드
   * 요청 파라미터 정보를 조회하는 메소드
     - String getParameter(String name)
       + 지정된 이름에 해당하는 요청파라미터값을 반환한다.
    String[]	getParameterValues(String name)
        * 지정된 이름에 해당하는 요청파라미터값을 배열로 반환한다.
        * 입력컨트롤이 체크박스일 때 주로 사용
  * 인코딩 관련 메소드
    void		setCharacterEncoding(String encoding)
        * 지정된 인코딩방식으로 폼입력값을 복원하게 한다.
        * getParameter 메소드를 한번이라도 사용한 이후에는 적용되지 않는다.
  * 클라이언트의 정보를 조회하는 메소드
  * 요청 헤더 정보를 조회하는 메소드

	- HttpServletResponse
		- response 변수에 저장된다.
		- 서버가 클라이언트로 보낼 응답 메세지를 책임진다.
		- 응답메세지에 대한 다양한 정보를 설정할 수 있는 setXXX() 메소드를 제공한다.
		- 주요 메소드
			* 응답메세지에 대한 정보를 설정하는 메소드
			* 리다이렉트 응답을 보내는 메소드
				void 		sendRedirect(String url)
						* 재요청할 페이지의 경로를 브라우저에게 응답으로 보낸다.
						* JSP페이지에서 INSERT/UPDATE/DELETE 작업을 수행하였다면
                                                  DB의 변경된 정보를 조회할 수 있는 JSP페이지에 대한 url을
						  응답으로 제공해야 된다.
						* HTTP응답코드를 302로 설정
						* 응답헤더에 Location:재요청 JSP페이지 항목을 추가
			* 응답 헤더 정보를 설정하는 메소드
	- HttpSession
		- session 변수에 저장된다.
		- 클라이언트별로 고유하게 사용되는 객체다.
		- 고유한 아이디를 가지고 있다. 
		- 클라이언트가 처음 접속할 때 자동 생성되고, 생성된 HttpSession객체의 아이디가
		  응답으로 클라이언트에게 보내진다.
		- 세션아이디를 전달받은 클라이언트는 요청할 때 마다 세션아이디를 요청헤더에 
                  담아서 서버로 전송한다.
		- 서버는 요청헤더의 세션아이디를 조회해서 그 아이디에 해당하는 세션객체를
		  실행되는 JSP의 sessioin변수에 저장한다.
		- 용도
			* 클라이언트의 정보를 보관하기
				- 클라이언트별로 각각 다른 세션객체를 사용하기 때문에 
				- 로그인한 사용자정보, 장바구니정보, 최근 본 상품정보 ...
				  (클라이언트의 private한 정보)
			* 클라이언트의 상태 유지
				- 접속한 클라이언트를 식별해서(누군지 안다.) 
			          해당 클라이언트에게 적절한 응답을 제공할 수 있다.
		- 주요 메소드
		      * void 		setAttribute(String name, Object value)
						* 지정된 이름으로 세션에 값(객체)을 저장한다.
						* 이름을 다르게해서 여러 가지 담을 수 있다.
		      * Object		getAttribute(String name)
						* 지정된 이름으로 보관된 값(객체)을 조회한다.
						* 값이 찾아지지 않으면 null을 반환
			void 		removeAttribute(String name)
						* 지정된 이름으로 보관된 값을 삭제한다.
		      * void		invalidate()
						* 해당 세션을 무효화시킨다.
						* 로그아웃 요청시 실행한다.
			void 		setMaxInactiveInterval(int second)
						* 세션객체의 최대 비활성화 시간을 지정한다.
						* 지정된 시간동안 세션객체에 대한 엑세스가 
                                                  없으면 해당 세션객체는 무효화된다.
			String		getId();
						* 세션의 고유한 아이디를 반환한다.
			




