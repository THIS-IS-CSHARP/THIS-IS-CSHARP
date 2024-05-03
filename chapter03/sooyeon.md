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
