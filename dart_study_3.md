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
