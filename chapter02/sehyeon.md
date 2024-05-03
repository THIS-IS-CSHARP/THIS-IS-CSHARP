## 연습문제
### 01. 텍스트 출력하는 프로그램 작성
```c#
using System;

class Program {
  public static void Main (string[] args) {
    Console.WriteLine("여러분, 안녕하세요?");
    Console.WriteLine("반갑습니다!");
  }
}
```
- `using System;` : System 네임스페이스를 포함하는 코드로 여기에 속한 클래스 기능을 사용할때 매번 네임을 명시할 필요가 없다. 예시로 System.Console.WriteLine()이 아닌 Console.WireLine()으로 사용할수 있다.
- `class Program{}` : Main() 메소드를 포함하는 Program 클래스 생성
- `public static void Main (string[] args){}` : Main()메서드가 프로그램의 진입시점으로 프로그램이 실행되면 Main()메서드가 호출 된다. 이때 매개변수로 커맨드 라인수를 string[] 배열로 받는다.
- `Console.WriteLine()` : 메서드로 문자열 출력후 줄바꿈을 포함한다.


### 02. 실행결과를 출력할 수 있도록 코드에서 1, 2에 필요한 내용 채우기
```C#
using System; // 1. System

class Program {
  public static void Main (string[] args) {
    Console.WriteLine("Hello World!"); // 2. Console
  }
}
```

- using System의 system 네임스페이스를 쓰겠다고 컴파일러에게 알림.
- 그래서 System을 네임을 생략하고 Console.WriteLine(); 으로 간단히 출력이 가능함
