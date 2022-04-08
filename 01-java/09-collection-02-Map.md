# Map<K, V> 인터페이스
- Map<K, V>는 **데이터를 Key와 Value의 쌍으로 연결지어서 저장하는 객체**다.
- Key와 Value의 쌍을 표현하는 객체는 Entry<K, V>다.
- Map<K, V>객체는 Entry<K, V>객체를 여러 개 저장하는 객체다.
- Key는 값을 대표하는 값이다. Key는 중복될 수 없다. Key의 타입은 보통 String, Integer, Long 타입이 주로 사용된다.
- Value는 실제로 Map에 저장할 정보를 가지고 있는 객체다. 
- Key와 Value의 예
  | Key | Value | Map<K, V> |
  | --- | --- | --- |
  | 학번 | 학생객체 | Map<Integer, Student> |
  | 주문번호 | 주문정보객체 | Map<Long, Order> |
  | 사용자아이디 | 사용자정보객체 | Map<String, User> |
  | 상품번호 | 상품정보객체 | Map<Integer, Product> |
  
- 주요 메소드
  + V **put(K key, V value)**
    * Map객체에 key, value의 쌍을 저장한다.
  + V **get(Object key)**
    * Map객체에서 지정된 key에 해당하는 value를 조회한다.
  + V remove(Object key)
    * Map객체에서 지정된 key에 해당하는 value를 삭제한다.
  + void clear()
    * Map객체에 저장된 모든 key, value의 쌍을 삭제한다.
  + int size()
    * Map객체에 저장된 Key,value쌍의 갯수를 반환한다.
  + boolean	isEmpty()
    * Map객체가 비어있으면 true를 반환한다.
  + boolean	**containsKey(Object key)**
    * Map객체에 지정된 key가 포함되어 있는지 여부를 반환한다.
  + boolean	containsValue(Object value)
    * Map객체에 지정된 value가 포함되어 있는지 여부를 반환한다.
  + Set&lt;Key&gt; keySet()
    * Map객체의 모든 key를 Set객체에 담아서 반환한다.
  + Collection&lt;V&gt;	values()
    * Map객체의 모든 value를 Collection객체에 담아서 반환한다.
  + Set&lt;Map.Entry&lt;K, V&gt;&gt; **entrySet()**
    * Map에 저장된 모든 Entry<K, V>를 Set에 담아서 반환한다.
- 주요 구현 클래스
  + HashMap
    * 가장 많이 사용하는 Map인터페이스 구현 클래스다.
  + HashTable
    * HashMap과 사용법은 동일하지만, 멀티스레드환경에서 안전하다.
- HashMap<K, V> 사용하기
  ```java
    public static void main(String[] args) {
      Map<Integer, String> map = new HashMap<Integer, String>();
      
      // HashMap객체에 Key, Value의 쌍으로 데이터 저장하기
      map.put(100, "김유신");
      map.put(200, "강감찬");
      map.put(300, "이순신");
      map.put(400, "류관순");
      
      // HashMap객체에 저장된 데이터를 key를 이용해서 조회하기
      String value1 = map.get(100);   // 김유신이 조회됨
      String value2 = map.get(300);   // 이순신이 조회됨
      String value3 = map.get(500);   // null이 반환됨
      
      // HashMap객체에 지정된 Key값이 존재하는지 확인하기
      boolean result1 = map.containsKey(300); // true가 반환됨
      
      // HashMap객체에 저장된 Key, Value 쌍의 갯수를 조회하기
      int count = map.size(); // 4가 조회됨
      
      // HashMap객체에서 지정된 Key값으로 저장된 데이터를 삭제하기
      map.remove(200);  // 200, "강감찬"의 key, Value쌍의 데이터가 삭제됨
      
      // HashMap객체가 비어있는지 확인하기
      boolean result2 = map.isEmpty(); // false가 반환됨
      
      // HashMap객체에 저장된 모든 Entry객체를 조회하기
      Set<Entry<Integer, String>> entries = map.entrySet();
      for (Entry<Integer, String> entry : entries) {
        int key = entry.getKey(); // key값이 반환됨
        String value = entry.getValue(); // value값이 반환됨
        System.out.println(key + " : " + value);
      }
    }
  ```





	
















	
