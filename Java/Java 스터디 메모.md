Java 스터디 메모
=

* 자바의 다형성    
C++/C#과 다르게, 멤버 함수는 virtual이나 override 키워드 같은 것 없어도 무조건 자식 함수가 실행됨. 즉 모든 오버라이드 된 함수는 가상 함수처럼 작동 (아마 그냥 디폴트로 가상 함수 테이블을 가지는 게 아닐까  싶음)

* 자바의 접근 제한자
<div><table>
<thead><tr><th>Access Modifier</th><th>Class</th><th>Package</th><th>Subclass</th><th>World</th></tr></thead>
<tbody><tr><td>public</td><td>O</td><td>O</td><td>O</td><td>O</td></tr></tbody>
<tbody><tr><td>protected</td><td>O</td><td>O</td><td>O</td><td>X</td></tr></tbody>
<tbody><tr><td>default</td><td>O</td><td>O</td><td>X</td><td>X</td></tr></tbody>
<tbody><tr><td>private</td><td>O</td><td>X</td><td>X</td><td>X</td></tr></tbody></table></div>


* super    
그냥 사용하면 부모를 가리키는 변수, super()로 쓰면 부모의 생성자. 생성자 본문의 첫 번째 구문에서만 super()를 사용할 수 있음.

* 자바 한정으로 2가지 조건을 만족 할 시 리턴타입이 달라도 오버라이딩이 가능.    

1. 반환타입이 primitive type (int, double 등) 이거나 void가 아님
2. 내가 변경 할 리턴 타입이 부모 클래스 메소드의 리턴 타입으로 자동 형변환 가능할때.    