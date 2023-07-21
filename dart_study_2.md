
## Basic Data Types
```dart
void main() {
  String name = "감자"; // 큰 따옴표, 작은 따옴표 상관 없음
  bool alive = true;
  int age = 100;
  double money = 11.11;
    
  num x = 12;	// num은 integer와 double의 부모 클래스
  x = 1.1;
}
```
- dart의 거의 전부는 object, class로 이루어져 있음
  - function도 object
</br>

## Lists
```dart
void main() {
  List<int> numbers = [1, 2, 3, 4];
  // var numbers = [1, 2, 3, 4];
  numbers.add(1);
}
```
- 리스트는 ","로 마칠 것 -> 자동 포매팅
  ```dart
  void main() {
    var numbers = [
      1,
      2,
      3,
      4,
    ];
  }
  ```
- collection if와 collection for를 지원
- __collection if__ : 존재할 수도, 하지 않을 수도 있는 요소를 가지고 리스트를 만들 수 있음
  ```dart
  void main() {
    var giveMeFive = true;
    var numbers = [
      1,
      2,
      3,
      4,
      if (giveMeFive) 5,	// giveMeFive가 true이면 5를 추가
    ];
  }
  ```
</br>

## String Interpolation
- text에 변수를 추가하는 방법
- 변수가 이미 존재할 때 사용하는 방식
  ```dart
  void main() {
    var name = "감자";
    var greeting = "Hello everyone, My name is $name, nice to meet you!";
  }
  ```
- 계산을 실행할 때의 문법
  ```dart
  void main() {
    var name = "감자";
    var age = 100;
    var greeting = "Hello everyone, My name is $name, and I'm ${age + 2}";
  }
  ```