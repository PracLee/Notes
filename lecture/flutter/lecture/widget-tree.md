# Widget Tree

* UI를 랜더링하는 데 사용되는 계층 구조
* MaterialApp -> Scaffold -> Center -> Text

```dart
void main() {
  // flutter app 실행
  // widget 추가
  runApp(
    // MaterialApp 은 항상 최상단에 위치 : Material Design 을 사용 할 수 있게 하는 Widget
    const MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        backgroundColor: Colors.black,
        body: Center(
          child: Text(
            'TEST TEXT',
            style: TextStyle(
              color: Colors.white,
            ),
          ),
        ),
      ),
    ),
  );
}

```

