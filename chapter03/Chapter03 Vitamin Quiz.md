# Vitamin Quiz

## 3-1
앞의 예제 코드에서 9행은 다음과 같습니다. <br>
`sbyte a = 10;` <br>
다음 코드로 수정해서 컴파일하면 어떤 일이 벌어질까요? 직접 테스트해보세요. <br>
`sbyte a = -5000_0000_0000;` // 0이 11 개

### 결과
```C#
using System;
class Vitamin {
  static void Main() {
    //sbyte a = -10;
    sbyte a = -5000_0000_0000;
    Console.WriteLine(a);
  }
}
```
```
실행 결과 CS0031 에러가 발생한다.
main.cs(13,16): error CS0031: Constant value `-500000000000' cannot be converted to a `sbyte'

CS0031(컴파일러 오류) : 해당 값을 저장할 수 없는 변수에 값을 할당하려고 시도했을때 발생하는 오류
```

<br>

## 3-2
Overflow 예제에서 uint 대신에 int를 사용하고, uint.MaxValue 대신에 int.MaxValue를 사용해서 코드를 바꿔 실험해보세요. 어떤 결과가 나왔습니까?

### 결과
```C#
using System;
namespace Overflow
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int a = int.MaxValue;
            Console.WriteLine(a); // 출력 : 2147483647
                a = a + 1;
            Console.WriteLine(a); // 출력 : -2147483648 (오버플로우 발생)
        }
    }
}
```
> 이 연산의 결과는 정수 오버플로우를 발생시키며, int 타입의 범위를 초과하게 된다.<br>
> C#에서는 기본적으로 오버플로우 검사가 활성화되어 있지 않기 때문에, 이러한 연산이 예외를 발생시키지 않는다.<br>
> 대신 오버플로우가 발생할 때 자동으로 가장 작은 값으로 롤오버된다.<br>
> int형의 경우 가장 작은 값은 -2,147,483,648으로 위 코드의 두번째 Console.WriteLine(a);에서는 -2147483648가 출력된다.

<br>

## 3-3
다음 코드에서 컴파일 에러를 발생시키는 부분을 모두 고르세요.
```
char a = "안";
char b = '안녕';
char c = '안';
string d = '안';
string e = '안녕'
string f = "안녕";
```

### 결과
```C#
using System;
class FindError {
  static void Main() {
    char a = "안";  // error
    char b = '안녕'; // error
    char c = '안';
    string d = '안';  // error
    string e = '안녕'; // error
    string f = "안녕";
  }
}
```

> char 형식은 `''` , string 형식은 `""`을 사용해야한다. <br>
> char b 의 '안녕'은 단일 문자가 아니기에 할당이 불가능해 컴파일 에러가 발생한다. <br>
> string e 의 '안녕'은 문자열으로 ""를 사용해야 할당이 가능해 컴파일 에러가 발생한다. <br>
