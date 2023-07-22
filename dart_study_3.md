## Defining a Function
```dart
String sayHello(String name) {
  return "Hello $name nice to meet you!";
}

void main() {
  print(sayHello('potato'));
}
```
```
Hello potato nice to meet you!
```

- __fat arrow syntax__ : 한 줄짜리 함수일 때 사용 가능
  ```dart
  String sayHello(String name) => "Hello $name nice to meet you!";
  
  num plus(num a, num b) => a + b;
  ```
</br>

## Named Parameters
- positional parameter : 사용자가 순서를 잊을 수도 있고, parameter만 봐서는 의미를 알 수 없기 때문에 좋은 방식이 아님
  ```dart
  String sayHello(String name, int age, String country) {
    return "Hello $name, you are $age, and you come from $country";
  }
  
  void main() {
    print(sayHello('potato', 100, 'Korea'));
  }
  ```
- default value를 지정하여 선언
  ```dart
  String sayHello({
    String name = 'tomato',
    int age = 200,
    String country = 'Korea',
  }) {
    return "Hello $name, you are $age, and you come from $country";
  }
  
  void main() {
    print(sayHello(
      name: 'potato',
      country: 'Korea',
      age: 100,
    ));
  }
  ```
- __required__를 사용하여 선언
  ```dart
  String sayHello({
    required String name,
    required int age,
    required String country,
  }) {
    return "Hello $name, you are $age, and you come from $country";
  }
  
  void main() {
    print(sayHello(
      name: 'potato',
      country: 'Korea',
      age: 100,
    ));
  }
  ```
  </br>

## Optional Positional Parameters
```dart
String sayHello(
  String name,
  int age,
  [String? country = 'Korea'],
) => "Hello $name, you are $age years old from $country";

void main() {
  var results = sayHello('potato', 100);
  print(results);
}
```
```
Hello potato, you are 100 years old from Korea
```
- 대괄호로 감싸기
- String? : country가 null이 될 수도 있음을 표시
- 기본 값을 지정

</br>

## Operator
- 일반적인 방법
  ```dart
  String capitalizeName(String? name) {
    if (name != null) {
      return name.toUpperCase();
    }
    return 'TOMATO';
  }

  void main() {
    capitalizeName('potato');
    capitalizeName(null);
  }
  ```
- fat arrow 사용
  ```dart
  String capitalizeName(String? name) =>
    name != null ? name.toUpperCase() : 'TOMATO';
  ```
### question question operator(QQ, null aware operator)
- 좌항이 null이면 우항을 return
  ```dart
  String capitalizeName(String? name) =>
    name?.toUpperCase() ?? 'TOMATO';
  ```
### QQ equals (QQ assignment operator)
- null이 아니라면 값을 할당
  ```dart
  void main() {
    String? name;
    name ??= 'potato';
    name ??= 'tomato';
    print(name);
  }
  ```
  ```
  potato
  ```
  </br>

## Typedef
- 자료형이 헷갈릴 때 도움이 될 alias를 만드는 방법
```dart
typedef ListOfInts = List<int>;

ListOfInts reverseListofNumbers(ListOfInts list) {
  var reversed = list.reversed;
  return reversed.toList();
}

void main() {
  print(reversedListOfNumbers([1, 2, 3]));
}
```
```
[3, 2, 1]
```
- typedef는 간단한 구조에서만 사용 -> 더 복잡하고 구체적인 구조는 class를 사용할 것