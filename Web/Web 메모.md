Web 메모
=
내용 쌓이면 파일 분할함

<hr>

### HTML
* class랑 id의 차이: <br> class는 같은 이름 중복 사용 가능, id는 불가능. 그리고 css에서 class는 .btn 처럼 쓰는데 id는 #btn으로 써야함

* ico파일을 가지고 favicon을 정해줄 수 있음 (탭 옆에 작게 뜨는 아이콘)
```html
<link rel="icon" href="./favicon.ico" />
```

* 요즘 웹의 개발 트렌드는 html은 스타일적인 요소를 모두 빼고 대신 시멘틱 태그를 활용해 어떤 요소가 어떤 의미인지를 가지는지 구조적인것에 집중하고, 나머지 스타일을 모두 css가 처리하는 방식인 것 같음.

<hr>

### CSS

* none을 써주면 그 효과를 제거할 수 있음. <br> 예를 들어, a태그를 달면 자동으로 밑줄이 생기는데, 아래처럼 하면 효과가 제거됨.
```css
text-decoration: none;
```

* 태그 뒤에 : last-child, hover 같은 것을 붙여서 특정 상태나 특정 자식에 대해 스타일을 정의할 수 있음. nth-child(3) 으로 n번째 자식도 됨.    
 li:before 도 있는데 리스트 아이템의 뒤에 (li들 사이에) 뭔가를 넣고 싶을 때 사용할 수 있음

```css
.container .loginBox a:first-child:hover,
.container .regiBox a:nth-child(0),
header .inner .submenu .menu li::before 
```
* display 타입을 flex로 많이 사용함. 정렬이나 갭 넣어주는게 편하다고 함. 자세한건 아직 덜 배움.

* position이라는 속성이 있는데 기본값은 static이고, relative, absolute, fixed라는 것을 많이 쓴다고 함.    
relative를 쓰면 원래 속성과 달라지진 않지만, 위치 지정 요소로써 작동할 수 있음. 자신의 원래 위치로부터 top, left등을 계산하게 됨.    
absolute를 쓰게 되면 그 요소가 붕 뜬 것처럼 되어 다른 요소는 그 요소를 무시하고 배치되고, 그 요소는 제일 앞으로 나오게 됨.    
fixed는 absolute와 비슷한데, 스크롤을 해도 위치를 고정시킬 수 있음.     
fixed와 absolute 모두 가장 가까운 위치 지정 요소를 가진 조상을 기준으로 거리를 계산함.     
참고: https://developer.mozilla.org/ko/docs/Web/CSS/position

<hr>

### JS
* js에서 어떤 요소를 변수에 가져온 뒤에, 그 변수의 classList를 통해 css를 추가하거나 제거할 수 있음. 추가 제거 모두 class의 이름으로 함.