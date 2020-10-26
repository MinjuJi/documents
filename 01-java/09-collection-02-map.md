# Map<K, V> 인터페이스
- Key와 Value의 쌍으로 연결지어서 저장하는 객체
- Key는 중복될 수 없다.
- K는 key(상징)의 타입
- V는 Value(객체, 실제 데이터, 실제 사용할 객체)의 타입
- 주요 메소드
  + V **put(K key, V value)**
    * Map객체에 key, value의 쌍을 저장한다.
  + V **get(Object key)**
    * Map객체에서 지정된 key에 해당하는 value를 조회한다.
		- V		remove(Object key)
				Map객체에서 지정된 key에 해당하는 value를 삭제한다.
		- void		clear()
				Map객체에 저장된 모든 key, value의 쌍을 삭제한다.
		- int 		size()
				Map객체에 저장된 Key,value쌍의 갯수를 반환한다.
		- boolean	isEmpty()
				Map객체가 비어있으면 true를 반환한다.
		- boolean	containsKey(Object key)
				Map객체에 지정된 key가 포함되어 있는지 여부를 반환한다.
		- boolean	containsValue(Object value)
				Map객체에 지정된 value가 포함되어 있는지 여부를 반환한다.
		- Set<Key>	keySet()
				Map객체의 모든 key를 Set객체에 담아서 반환한다.
		- Collection<V>	values()
				Map객체의 모든 value를 Collection객체에 담아서 반환한다.
	- 주요 구현 클래스
		- HashMap 	: 가장 많이 사용하는 Map인터페이스 구현 클래스다.
		- HashTable	: HashMap과 사용법은 동일하지만, 멀티스레드환경에서 안전하다.


Map객체를 ValueObject로 활용하기
	* 사람정보를 담은 클래스 정의
	public class Person {
		int no;
		String name;
		double height;
		double weight;
		// getter,setter 생략
	}
	* 사람정보를 담는 객체 생성, 정보저장	  * 사람정보를 담는 Map객체 만들고, 정보 담기
	Person p = new Person();		    HashMap<String, Object> p = new HashMap<>();
	p.setNo(10);				    p.put("no", 10);
	p.setName("홍길동");			    p.put("name", "홍길동");
	p.setHeight(178.4);			    p.put("height", 178.4);
	p.setWeight(78.1);			    p.put("weight", 78.1);
	* 장점					    * 단점
	  1. 이클립스의 코드자동완성을 지원받음	      1. 이클립스의 코드자동완성 지원을 받지 못함
	  2. p.setNane("홍길동") 코드에러 표시	      2. p.put("nane", "홍길동") 에러표시 안됨
	  3. p.setName(10) 코드에러 표시	      3. p.put("name", 10) 에러표시 안됨
	  4. int no = p.getNo() 형변환 불필요	      4. int no = (Integer) p.get("no") 형변환필요
	* 단점					    * 장점
	  1. 정보가 가변적이면 그때마다 	      1. 정보가 가변적이면, 그때마다 
             클래스를 수정해야 한다.                     새key,value 쌍으로 저장하기만 하면 됨
						      2. 정보를 담기위한 클래스를 만들지 않아도
							 Map객체를 생성해서 key,value쌍으로 값을
							 저장할 수 있다.




	
















	
