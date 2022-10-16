Flutter 메모
=

내용 좀 쌓이면 파일 분할함.

* Row, Column 정렬 https://beomseok95.tistory.com/m/310

* 현재 기기의 방향, 화면 크기를 얻어오는 법:
```dart
MediaQuery.of(context).size
MediaQuery.of(context).orientation
```

* dart 2.2.2 부터 리스트 내포형 if 사용가능. 중괄호 사용 안함

```dart
children[
    if (isLandscape) Row(...)
]
```