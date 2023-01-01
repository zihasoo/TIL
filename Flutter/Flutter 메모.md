Flutter 메모
=

내용 좀 쌓이면 파일 분할함.

* Row, Column 정렬 https://beomseok95.tistory.com/m/310

* 현재 기기의 방향, 화면 크기를 얻어오는 법:
```dart
MediaQuery.of(context).size
MediaQuery.of(context).orientation
```

* 키보드의 맨 위 좌표를 얻어오는 방법:
```dart
MediaQuery.of(context).viewInsets.bottom
```

* dart 2.2.2 부터 리스트 내포형 if 사용가능. (중괄호 사용 못함)

```dart
children[
    if (isLandscape) Row(...)
    if (isLandscape) ...[OutlinedButton(), OutlinedButton()] 
    //여러개 하고싶으면 이런식으로 하면 될듯?
]
```

* LayoutBuilder : Builds a widget tree that can depend on the parent widget's size.     
constraints 인자를 받아서 부모 위젯의 크기에 맞게 위젯 사이즈를 설정하고 반응형으로 만들 수 있음.    <br><br>
아래와 같은 경우에 호출된다고 함.
    - 처음으로 widget이 layout 될 때
    - 부모 widget의 constraint가 바뀔 때
    - 부모 widget이 해당 widget을 업데이트할 때

```dart
return LayoutBuilder(
    builder: (BuildContext context, BoxConstraints constraints) {
        final width = constraints.maxWidth;
        final height = constraints.maxHeight;
        final ratio = width / height;
        return Column(...)
    }
)
```

* dart:io 를 import 하면 현재 플랫폼을 확인할 수 있다.

```dart
import 'dart:io';

void main() {
  print(Platform.isAndroid);
  print(Platform.isFuchsia);
  print(Platform.isIOS);
  print(Platform.isLinux);
  print(Platform.isMacOS);
  print(Platform.isWindows);
}
```

* 제스처 디텍팅 하는 방법 
```dart
InkWell //누르면 기본 버튼 누른 효과 나옴 (잉크 퍼지는 효과)
GestureDetector //좀 더 섬세한 컨트롤 가능. 효과 x
```

* 보이지 않는 자식을 가진 GestureDetector의 터치 이벤트 활성화 하는 법
```dart
onTap: () {},
behavior: HitTestBehavior.opaque, //이걸 사용하면 된다
```


* primarySwatch에 들어갈 MaterialColor 만드는 방법   
https://points.tistory.com/65

