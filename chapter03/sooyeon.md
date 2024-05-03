### chapter3 연습문제

1.

```csharp
using System;
namespace RectArea
{
    class MainApp{
        public static void Main(){
            Console.WriteLine("사각형의 너비를 입렵하세요");
            string width = Console.ReadLine();
            
            Console.WriteLine("사각형의 높이를 입렵하세요");
            string height = Console.ReadLine();
            
            int rectArea = int.Parse(width) * int.Parse(height);
            
            Console.WriteLine("사각형의 넓이 : {0}",rectArea);
        }   
    }
}
```

2.

```
int a = 7.3; 
// 7.3은 float 이나 double 형식을 사용해야한다.

char d = "abc"; 
// char 자료형은 단일 문자형으로 1개의 문자만 할당할 수 있다.
```

3. 값 형식은 변수가 값을 담는 데이터 형식을 말하고, 참조 형식은 변수가 값 대신 값이 있는 곳의 위치를 담는 데이터 형식을 말한다.

4.

**박싱(Boxing)**: 박싱은 값 형식을 참조 형식으로 변환하는 과정이다. 값 형식을 박싱하면 값이 담긴 새로운 객체가 힙(heap)에 생성되고, 해당 객체에 대한 참조(주소값)가 반환된다.

```csharp
int i = 10; // 값 형식
object obj = i; // 박싱
```

**언박싱(Unboxing)**: 언박싱은 박싱의 반대 과정으로, 박싱된 객체에서 값을 추출하는 것을 의미한다.

```csharp
object obj = 10; // 박싱된 정수
int i = (int)obj; // 언박싱
```

5.    a - int   /  b - string


</br>

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
