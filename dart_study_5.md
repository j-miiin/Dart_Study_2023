## Cascade Notation
```dart
class Player {
  String name;
  int xp;
  String team;
    
  Player({required this.name, required this.xp, required this.team});
    
  void sayHello() {
    print("Hi my name is $name");
  }
}

void main() {
  var potato = Player(name: 'potato', xp: 1500, team: 'blue');
  potato.name = 'tomato';
  potato.xp = 2000;
  potato.team = 'red';
}
```
- __cascade notation__을 사용
  - 세미콜론은 마지막에만 사용
  ```dart
  void main() {
    var potato = Player(name: 'potato', xp: 1500, team: 'blue')
    ..name = 'tomato'
    ..xp = 2000
    ..team = 'red';
    ..sayHello();
  }
  ```
- 앞에 class가 있다면 바로 뒤에 사용하지 않아도 괜찮음
  ```dart
  void main() {
    var potato = Player(name: 'potato', xp: 1500, team: 'blue');
    var tomato = potato
      ..name = 'tomato'
      ..xp = 2000
      ..team = 'red';
      ..sayHello();
    }
  ```
</br>

## Enums
```dart
enum Team { red, blue }
enum XPLevel { beginner, medium, pro }

class Player {
  String name;
  XPLevel xp;
  Team team;
    
  ...
  }

void main() {
  var potato = Player(
    name: 'potato',
    xp: XPLevel.medium,
    team: Team.blue,
  );
    
  var tomato = potato
    ..name = 'tomato'
    ..xp = XPLevel.pro
    ..team = Team.red
    ..sayHello();
}
```
</br>

