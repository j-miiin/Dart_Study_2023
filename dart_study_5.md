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

## Abstract Classes
- 추상화 클래스로는 객체 생성 불가능
- 다른 클래스들이 직접 구현 해야하는 메소드들을 모아 놓은 일종의 청사진(blueprint)
  - class에서 상속, 확장 가능
  ```dart
  abstract class Human {
    // 메소드의 시그니쳐(signature)만 정의 (반환하는 값을 정의)
    void walk();
  }
   
  class Player extends Human {
    ...
    
    void walk() {
      print("I'm walking");
    }
  }
   
  class Coach extends Human {
    void walk() {
      print("The coach is walking");
    }
  }
  ```
  
</br>

## Inheritance
```dart
class Human {
  final String name;
  Human(this.name);
  void sayHello() {
    print("Hi my name is $name");
  }
}

enum Team { blue, red }
 
class Player extends Human {
  final Team team;
    
    Player({
      required this.team,
      required String name,
    }) : super(name);
}

void main() {
  var player = Player(
    team: Team.red,
    name: 'potato',
  );
}
```
- __super__ : 확장을 한 부모 클래스와 상호작용할 수 있게 해주는 키워드
- __override__
  ```dart
  class Player extends Human {
    final Team team;
    
    Player({
      required this.team,
      required String name,
    }) : super(name);
    
    @override
    void sayHello() {
      super.sayHello();
      print("and I play for $team");
    }
  }
  ```
  
</br>

## Mixins
- 생성자가 없는 클래스
- 클래스에 프로퍼티나 메소드를 추가할 때 사용
  - 여러 클래스에 재사용 가능
  ```dart
  class Strong {
    final double strengthLevel = 1500;
  }
  
  class QuickRunner {
    void runQuick() {
      print("ruuuuun!");
    }
  }
  
  class Tall {
    final double height = 190.5;
  }
  
  class Player with Strong, QuickRunner, Tall {
    ...
  }
  
  class Horse with Strong, QuickRunner {
    ...
  }
  
  class Kid with QuickRunner {
    ...
  }
  ```
- 상속(확장)과 차이점
  - __extend__ : extend를 하게 되면 확장한 그 클래스는 부모 클래스가 되고, 자식 클래스는 부모 클래스를 super를 통해 접근하게 되며 그 순간 부모 클래스의 인스턴스가 됨
  - __with__ : 단순하 Mixin 내부의 프로퍼티와 메소드들을 가져오는 것 뿐 -> 부모 클래스 X
