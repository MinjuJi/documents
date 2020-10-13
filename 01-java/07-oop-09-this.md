# this와 this()

## this
- **this**는 **인스턴스 자기 자신**을 가리키는 키워드다.
  <kbd>![alt this키워드](/images/java/this.png)</kbd>
- this 키워드는 이 클래스를 기반으로 생성된 인스턴스를 참조한다.
- 이 this 키워드를 사용해서 인스턴스의 메소드와 생성자에서 자기 자신의 인스턴스(멤버변수나 멤버메소드)멤버에 접근할 수 있다.
- this 키워드는 생성자와 멤버메소드내에서 사용할 수 있다.

## this의 사용
- 생성자나 메소드에서 사용하기
  * 생성자에서 매개변수의 이름이 멤버변수의 이름이 동일한 경우, 매개변수와 멤버변수를 구분하기 위해서 this를 사용한다.
  * 생성자나 메소드에서 this를 사용하지 않을 경우, 생성자나 메소드내에서 사용되는 변수명이 어떤 이름에 해당하는지를 다음과 같은 규칙으로 결정한다.
    + 그 이름이 사용된 위치에서 속한 메소드의 지역변수나 매개변수에 해당 이름이 있으면 그것으로 본다.
    + 그 이름이 속한 메소드에서 해당 이름을 찾을 수 없다면 인스턴스의 멤버변수에서 그 이름에 해당하는 필드를 찾는다.
    + 그 이름이 인스턴스의 필드에도 없다면 컴파일 오류가 발생한다.
  
- 멤버변수명과 생성자의 파라미터명이 서로 다른 경우
  <kbd>![alt this사용하기](/images/java/this1.png)</kbd>
- 멤버변수명과 생성자의 파라미터명이 동일한 경우
  <kbd>![alt this사용하기](/images/java/this2.png)</kbd>
- 멤버변수명과 생성자의 파라미터명이 동일하고, this 키워드를 사용한 경우
  <kbd>![alt this사용하기](/images/java/this3.png)</kbd>
  
## this()
- this()는 한 생성자에서 다른 생성자를 호출할 때 사용하는 메소드다.
- 생성자 메소드에서 다른 생성자를 호출할 때는 **클래스명()** 대신 **this()** 를 사용한다.
- 생성자 메소드에서 다른 생성자메소드를 호출할 때는 반드시 수행문의 첫줄에 this()를 적어야 한다.
- 생성자 메소드가 여러개 재정의되어 있을 때는 해당 생성자의 매개변수에 맞게 **this(인자, 인자, 인자, ...)** 의 형태로 호출하면 된다.

## this() 사용예
```java
  public class User {
    int no;
    String name;
    String userId;
    int password;
    String email;
    boolean disabled;
    
    User() {
      this(0, "guest", "guest", 0000, null, false);
    }
    
    User(int no, String name, String userId, int password) {
      // 다른 생성자 메소드를 호출함
      this(no, name, userId, password, null, false);
    }
    
    User(int no, String name, String userId, int password, String email) {
      // 다른 생성자 메소드를 호출함
      this(no, name, userId, password, email, false);
    }
    
    User(int no, String name, String userId, int password, String email, boolean disabled) {
      this.no = no;
      this.name = name;
      this.userId = userId;
      this.password = password;
      this.email = email;
      this.disabled = disabled;
    }
  }
```

  
