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


* 자바에서 제네릭의 원리:   
C++에서 템플릿이 컴파일 타임에 적절한 코드를 직접 생성하는 것과 다르게, 자바의 제네릭은 단순히 타입을 지워서 일반화를 시키는 것으로 알려져 있다. 그렇다면 여기서 타입을 지운다는 말이 무슨 뜻일까? 자바는 정말 단순한 방식을 선택했다. 비 제네릭 코드와의 호환성과 컴파일 타임 오버헤드를 피하기 위해, 모든 제네릭 타입을 Object로 만들고, 사용하는 부분마다 형변환 하는 코드를 삽입하는 것이다.(제네릭을 코드에 넣은 뒤 컴파일 -> 디컴파일을 해서 코드를 보게 되면 확인할 수 있다.) 이 때문에 직접 Object-형변환 패턴으로 타입 일반화를 시키는 것과 성능상의 차이가 없다. 또한 컴파일 이후엔 Object로 바뀌므로 런타임에는 제네릭의 타입을 알 수 없게 된다.    
참고로 제네릭에 <T extends SomeClass> 형태로 타입 경계를 걸 수 있는데, 이렇게 타입 경계를 사용하면 Object대신 해당 타입으로 변환되게 된다. 그런데 <T extends SomeClass1 & SomeClass2> 처럼 여러개의 타입 경계를 지정할 수도 있는데, 이럴 때는 가장 왼쪽에 있는 클래스로 변환된다. 그래서 가장 구체적인 타입이 가장 왼쪽에 와야 한다.