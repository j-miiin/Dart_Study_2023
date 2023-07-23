## Your First Dart Class
- class에서 property를 선언할 때는 타입을 사용해서 선언
  ```dart
  class Player {
    String name = 'potato';
    int xp = 1500;
  }

  void main() {
    var player = Player();
    print(player.name);
    player.name = 'tomato';
    print(player.name);
  }
  ```
  ```
  potato
  tomato
  ```
- property 값을 바꾸지 못하게 하고 싶으면 final을 사용
  ```dart
  class Player {
    final String name = 'potato';
    int xp = 1500;
  }
  ```
- class의 함수
  - class의 property와 variable의 이름이 겹치는 것이 아니라면 this를 사용할 필요 없음
  ```dart
  class Player {
    final String name = 'potato';
    int xp = 1500;
        
    void sayHello() {
      print("Hi my name is $name");
    }
  }
  
  void main() {
    var player = Player();
    player.sayHello();
  }
  ```
  ```
  Hi my name is potato
  ```
</br>

## Constructors
- argument를 받아서 Player class의 property 값이 되도록 함
  - class와 같은 이름을 가짐
  - __late__ : 변수들의 값을 나중에 받아올 것을 의미
  ```dart
  class Player {
    late final String name;
    late int xp;
        
    Player(String name, int xp) {
      this.name = name;
      this.xp = xp;
    }
        
    void sayHello() {
      print("Hi my name is $name");
    }
  }
  
  void main() {
    var player = Player("potato", 1500);
    player.sayHello();
    var player2 = Player("tomato", 2500);
    player2.sayHell();
  }
  ```
  ```
  Hi my name is potato
  Hi my name is tomato
  ```
- constructor를 작성하는 더 나은 방법
  - 위에서 작성한 코드는 반복되는 부분이 너무 많음
  - late로 선언할 필요 없음
  ```dart
  class Player {
    final String name;
    int xp;
        
    Player(this.name, this.xp);

    ...
  }
  ```
</br>

## Named Constructor Parameters
- positional parameter(argument)는 class가 커지면 비효율적임
- named constructor parameter를 만드는 방법
  - required를 붙이거나 default value를 주면 됨
  ```dart
  class Player {
    final String name;
    int xp;
    String team;
    int age;
        
    Player({
      required this.name,
      required this.xp,
      required this.team,
      required this.age,
    });
        
    void sayHello() {
      print("Hi my name is $name");
    }
  }
  
  void main() {
    var player = Player(
      name: "potato",
      xp: 1500,
      team: "blue",
      age: 100,
    );
      
    var player2 = Player(
      name: "tomato",
      xp: 2500,
      team: "blue",
      age: 500,
    );
  }
  ```
</br>

## Named Constructors
- constructor들이 개발자가 정한 값으로 property를 초기화 시킨 객체를 주길 원할 때 사용
  - 콜론(:)을 사용하여 class를 초기화 함
  ```dart
  class Player {
    final String name;
    int xp;
    String team;
    int age;
        
    Player({
      required this.name,
      required this.xp,
      required this.team,
      required this.age,
    });
      
    Player.createBluePlayer({
      required String name,
      required int age,
    }) : this.age = age,
        this.name = name,
        this.team = 'blue',
        this.xp = 1500;
           
    Player.createRedPlayer(String name, int age)
      : this.age = age,
        this.name = name,
        this.team = 'red',
        this.xp = 2500;
        
    void sayHello() {
      print("Hi my name is $name");
    }
  }
  
  void main() {
    // named syntax
    var player = Player.createBluePlayer(
      name: "potato",
      age: 100,
    );
      
    // positional syntax
    var player2 = Player.createRedPlayer("tomato", 500);
  }
  ```
</br>

## Recap
- API Data를 통해 JSON 객체를 받는 상황을 가정해보자
  ```dart
  class Player {
    final String name;
    int xp;
    String team;
    int age;
        
    Player.fromJson(Map<String, dynamic> playerJson)
      : name = playerJson['name'],
        xp = playerJson['xp'],
        team = playerJson['team'];
            
    void sayHello() {
      print("Hi my name is $name");
    }
  }
  
  void main() {
    var apiData = [
      {
        "name": "potato",
        "team": "brown",
        "xp": 1500,
      },
      {
        "name": "tomato",
        "team": "red",
        "xp": 2500,
      },
      {
        "name": "lemon",
        "team": "yellow",
        "xp": 7000,
      },
    ];

    apiData.forEach((playerJson) {
      var player = Player.fromJson(playerJson);
      player.sayHello();
    });
  }
  ```
  ```
  Hi my name is potato
  Hi my name is tomato
  Hi my name is lemon
  ```
</br>


