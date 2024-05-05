# chapter02 연습문제

<br>

## 1. 다음과 같이 텍스트를 출력하는 프로그램을 작성하세요.
```
여러분, 안녕하세요?
반갑습니다!
```
### 정답
```C#
using System;

class Program {
  public static void Main (string[] args) {
    Console.WriteLine("여러분, 안녕하세요?");
    Console.WriteLine("반갑습니다!");
  }
}
```
> `using System;` : System 네임스페이스를 포함하는 코드로 여기에 속한 클래스 기능을 사용할때 매번 네임을 명시할 필요가 없다. 
> 예시로 System.Console.WriteLine()이 아닌 Console.WireLine()으로 사용할수 있다.<br><br>
> `class Program{}` : Main() 메소드를 포함하는 Program 클래스 생성<br><br>
> `public static void Main (string[] args){}` : Main()메서드가 프로그램의 진입시점으로 프로그램이 실행되면 Main()메서드가 호출 된다.
> 이때 매개변수로 커맨드 라인수를 string[] 배열로 받는다.<br><br>
> `Console.WriteLine()` : 메서드로 문자열 출력후 줄바꿈을 포함한다.
<br>
<br>

## 2. 아래 실행 결과를 출력할 수 있도록 다음 코드에서  1️⃣과 2️⃣에 필요한 코드를 채우세요.
```C#
using 1️⃣
class MainApp
{
  static void Main(String[] args)
  {
    2️⃣.WriteLine("Hello World!")
  }
}
```

### 정답
```C#
using System; // 1️⃣ System

class Program {
  public static void Main (string[] args) {
    Console.WriteLine("Hello World!"); // 2️⃣ Console
  }
}
```
> `using System;` : System 네임스페이스를 쓰겠다고 컴파일러에게 알린다.
> 따라서 System.Console.WriteLine()에서 System을 생략하고 `Console.WriteLine();` 으로 간단히 출력이 가능하다.


