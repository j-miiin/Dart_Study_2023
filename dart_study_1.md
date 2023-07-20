## Hello World
- main 함수는 모든 Dart 프로그램의 Entry point로 매우 중요
- 세미콜론을 잊지말자 -> 기능을 끝내는 역할

</br>  

## The Var Keyword 
- 변수 선언 방법
  - __var__
    ```dart
    void main() {
       var name = "감자";
       name = "포테이토";
    }
    ```
  - 명시적으로 타입 선언
    ```dart
    void main() {
      String name = "감자";
      name = "포테이토";
    }
    ``` 
- 업데이트 가능한 변수 -> 수정할 때는 같은 타입으로
- __var__은 관습적으로 함수나 메소드 내부에 지역 변수를 선언할 때 사용
- __타입 지정__은 class에서 변수가 property를 선언할 때 사용 
</br>  

## Dynamic Type
- __dynamic__ : 여러가지 타입을 가질 수 있는 변수에 쓰는 키워드
- 추천하지는 않지만 가끔 유용한 경우가 있음
  ```dart
  void main() {
    var name;
    name = "감자";
    name = 123;
    name = true;
  }
  ``` 
- dynamic으로도 선언 가능
  ```dart
  void main() {
    dynamic name;
    if (name is String) {
    	// name이 String인 것을 알기 때문에 name.(String 함수) 사용 가능
    }
  }
  ``` 
</br>  
  
## Nullable Variables
- __nullsafety__ : 개발자가 null 값을 참조할 수 없도록 하는 기능
  - null로 인한 에러는 컴파일러가 잡을 수 없음
  ```dart
  // Without null safety:
  bool isEmpty(String string) => string.length == 0;
  
  main() {
  	isEmpty(null);
  }
  ```
- dart에서 어떤 변수 혹은 데이터가 null이 될 수 있음을 명시하는 법
  ```dart
  void main() {
  	String? potato = '감자';
    	potato = null;
    	if (potato != null) {
    		potato.isNotEmpty;
    	}
       // potato?.isNotEmpty;
  }
  ```
- 기본적으로 모든 변수는 non-nullable
</br>  

## Final Variables
- __final__ : 한 번 정의된 변수를 수정할 수 없게 만들기 위해 사용
  ```dart
  void main() {
  	final String name = '감자';
    	// final name = '감자';
  }
  ```
</br>  

## Late Variables
- __late__ : 초기 데이터 없이 변수 선언 가능
  ```dart
  void main() {
  	late final String name;
    	// do something, go to api
      name = '감자';
  }
  ```
- 값을 넣어주지 않은 late로 선언된 변수에 접근하지 않도록 dart가 보호해줌
</br>  

## Constant Variables
- __const__ : compile-time constant를 만들어줌
  - 컴파일 타임에는 알고 있어야 하는 값 (앱스토어에 앱을 올리기 전에 알고 있어야 하는 값)
  ```dart
  void main() {
  	// const API = fetchApi(); 
    	// 위 변수는 API에서 받아와야 하는 값이므로 컴파일 타임에 알고 있는 변수가 아님
      // 따라서 final 변수를 사용해야 함   

      const max_allowed_price = 120;
      // 앱에서 사용할 상수들이 있다면 const를 사용하면 됨
  }
  ```
