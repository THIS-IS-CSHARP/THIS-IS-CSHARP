### chapter2 연습문제

1.

```csharp
using System;
class Hello {
  static void Main() {
    Console.WriteLine("여러분 안녕하세요?");
    Console.WriteLine("반갑습니다!");
  }
}
```

2.  1 - System / 2 - Console

### chapter3 비타민문제

3-1.

```csharp
using System;
class Homework {
  static void Main() {
    //sbyte a = -10;
    sbyte a = -5000_0000_0000;
    Console.WriteLine(a);
  }
}
```

```
실행 결과 CS0031 에러 발생
main.cs(13,16): error CS0031: Constant value `-500000000000' cannot be converted to a `sbyte'

CS0031(컴파일러 오류) ****- ****해당 값을 저장할 수 없는 변수에 값을 할당하려고 시도했을때 발생하는 오류
```

3-2.

```csharp
using System;
class Overflow {
  static void Main() {
    //uint a = uint.MaxValue;
    int a = int.MaxValue;
    Console.WriteLine(a); // 출력 : 2147483647
    
    a = a + 1;
    Console.WriteLine(a); // 출력 : -2147483648 (오버플로우 발생)
  }
}
```

```
이 연산의 결과는 정수 오버플로우를 발생시키며, int 타입의 범위를 초과하게 된다. C#에서는 기본적으로 오버플로우 검사가 활성화되어 있지 않기 때문에, 이러한 연산이 예외를 발생시키지 않고, 대신 오버플로우가 발생할 때 자동으로 가장 작은 값으로 롤오버된다. int 타입의 경우 가장 작은 값은 -2,147,483,648으로 위 코드의 두번째 Console.WriteLine(a);에서는 -2147483648가 출력된다.
```

3-3.

```csharp
using System;
class FindError {
  static void Main() {
    char a = "안";
    char b = '안녕'; // error
    char c = '안';
    string d = '안';
    string e = '안녕'; // error
    string f = "안녕";
  }
}
```

