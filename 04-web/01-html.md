# HTML
- HyperText Markup Language
  + 웹용 문서를 작성할 때 사용되는 언어
  + HyperText : 문서의 링크를 클릭하면 연결된 문서로 즉시 이동할 수 있는 기능
  + Markup : 문서에서 어느 부분이 제목인지, 본문인지, 링크인지, 그림인지 등을 표시할 때 마크업(태그)을 사용한다.
  + 마크업(태그)을 사용해서 작성된 문서이며, 링크를 클릭하면 연결된 다른 문서로 즉시 이동할 수 있는 문서를 작성할 때 사용되는 언어

## HTML의 구성요소
- 태그
  + &lt;와 &gt;를 이용해서 만든다.
  + 예) &lt;a&gt;, &lt;p&gt;, &lt;table&gt;, &lt;ul&gt;, &lt;input&gt;, &lt;img&gt;, &lt;h1&gt;, &lt;body&gt;, &lt;html&gt;		
  + 태그명은 소문자로 적는다.
  + 태그는 여는 태그, 닫는 태그가 있다.
    * 여는 태그 : &lt;a&gt; &lt;table&gt; &lt;ul&gt; &lt;h1&gt;
    * 닫는 태그 : &lt;/a&gt; &lt;/table&gt; &lt;/ul&gt;
    * 태그를 작성할 때는 여는 태그와 닫는 태그를 짝을 맞춰서 정확히 입력해야 한다.
      - 올바른 예)
      ```html
        <h1>html 수업</h1>
        <p>이번 시간에는 html의 주요 태그를 살펴봅시다.</p>
      ```
      - 올바르지 않은 예)
      ```html
        <h1>html 수업
        <p>이번 시간에는 html의 주요 태그를 살펴봅시다.</p>
      ```
  + 태그들 사이에는 부모태그, 자식태그의 관계를 가지는 태그가 있다.
    * 자식태그는 부모태그 안에서만 사용할 수 있다.
    * 자식태그를 부모태그 안에 적을 때는 들여쓰기 한다.
      - 올바른 예) 
        + 부모태그(ul)태그 안에 자식태그(li)를 적었다.
        ```html
          <ul>
            <li>커피</li>
            <li>쥬스</li>
          </ul>
        ```
      - 올바르지 않은 예)
        + 부모태그 밖에 적었다.
        ```html
          <ul></ul>
          <li>커피</li>
          <li>쥬스</li>
        ```
        * 부모태그 없이 적었다.
        ```html
          <li>커피</li>
          <li>쥬스</li>
        ```
  + 태그는 속성과 함께 사용할 수 있다.
    * 속성은 태그와 관련된 부가적인 정보, 추가기능을 정의한다.
    * 형식 : &lt;태그명 속성명="속성값" 속성명="속성값"&gt;
    * 속성명과 속성값은 붙여서 적고, 속성값은 ""사이에 적는다.
    * 동일한 속성명을 여러 번을 적을 수 없다.
    * 속성명을 적을 때는 특별한 순서가 없다.
      + 작성예) 
      ```html
        <img src="images/logo.png" width="160" height="70">
      ```
- 속성
  + 태그마다 고유한 속성을 가지고 있다.
  + 속성은 원래 사용목적에 맞게 사용해야 한다.
  + 어떤 속성은 속성값이 미리 정해진 것들도 있다.
  ```html
    <input type="속성값">
    <!--
      속성값은 text, password, radio, checkbox, date, number, hidden, file, button, submit, reset ...
    -->
  ```
  + data-*로 시작하는 속성은 임의로 추가할 수 있다.
  ```html
    <img src="images/logo.png" data-title="회사로고" data-creator="홍길동" data-pubdate="2019-10-31">
  ```
  
## HTML 문서의 구조
```html
<!doctype html>
<html lang="ko">
<head>
<!-- 웹브라우저가 html문서를 해석할 때 필요한 정보를 정의하는 곳 -->
</head>
<body>
<!-- 실제로 화면에 표시되는 내용이 정의되는 곳 -->
</body>
</html>	
```

- &lt;!doctype html&gt;
  + html 문서의 유형을 선언하는 선언문이다.
  + "이 문서는 html5 작성규칙을 준수하는 HTML 문서다"라는 의미를 나타냄
- &lt;html&gt; ~ &lt;/html&gt;
  + html 문서의 루트 태그
  + 모든 html문서는 루트 태그를 오직 하나만 가질 수 있다. 	
  + 모든 태그는 &lt;html&gt;와 &lt;/html&gt;태그 안에 작성해야 한다.
  + &lt;html&gt;태그는  &lt;head&gt;와  &lt;body&gt;태그를 자식태그로 가진다.
  + &lt;html&gt;태그는 lang속성을 가진다.
  + lang 속성은 문서에서 사용되는 언어를 지정할 수 있다.
  + lang 속성에 지정된 언어와 브라우저의 기본언어가 다르면 번역옵션이 표시된다.
    * 한국어:ko
    * 영어:en
    * 일본어:ja
    * 중국어:zh
    * 프랑스어:fr
    * 독일어:de
- &lt;head&gt; ~ &lt;/head&gt;
  + 웹브라우져가 문서를 해석하는데 필요한 정보를 제공하는 태그
    * 문서의 제목 : &lt;title&gt;문서의 제목&lt;/title&gt;
    * 문자 인코딩 방식 : &lt;meta charset="utf-8"&gt;
    * 스타일시트 : &lt;link rel="style" href="style.css"&gt;
    * 기타 : 자바스크립트소스
  + &lt;head&gt;태그에 정의된 태그는 화면에 표시되지 않는다.
- &lt;body&gt; ~ &lt;/body&gt;
  + 웹브라우저에 실제로 표시될 내용을 포함하는 태그
  + 앞으로 배우게 될 태그들은 대부분 &lt;body&gt; 태그 안에서 사용하게 될 태그
