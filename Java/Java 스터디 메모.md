Java 스터디 메모
=

* 자바의 다형성    
C++/C#과 다르게, 멤버 함수는 virtual이나 override 키워드 같은 것 없어도 무조건 자식 함수가 실행됨. 즉 모든 오버라이드 된 함수는 가상 함수처럼 작동 (아마 그냥 디폴트로 가상 함수 테이블을 가지는 게 아닐까  싶음)

* 자바의 접근 제한자<table>
<thead><tr><th>Access Modifier</th><th>Class</th><th>Package</th><th>Subclass</th><th>World</th></tr></thead>
<tbody><tr><td>public</td><td>O</td><td>O</td><td>O</td><td>O</td></tr></tbody>
<tbody><tr><td>protected</td><td>O</td><td>O</td><td>O</td><td>X</td></tr></tbody>
<tbody><tr><td>default</td><td>O</td><td>O</td><td>X</td><td>X</td></tr></tbody>
<tbody><tr><td>private</td><td>O</td><td>X</td><td>X</td><td>X</td></tr></tbody>
</table>