### Vitamin Quiz 3-1
```
sbyte a = -50000_0000_0000;
```
##### sbyte는 8비트 부호 있는 정수형이므로 -50000_0000_0000 범위를 벗어난다

### Vitamin Quiz 3-2

```
using System;

namespace Overflow
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int a = int.MaxValue;
            Console.WriteLine(a);
            
         
                a = a + 1;
            
            
            Console.WriteLine(a); // 이 줄은 실행됩니다.
        }
    }
}
```
##### 결과 : 2147483647, -2147483648



### Vitamin Quiz 3-3 다음 코드에서 컴파일 에러가 발생하는 부분을 고르세요
```
char a = "안";
char b = '안녕';
char c = '안';
string d = '안';
string e = '안녕'
string f = "안녕";
```
##### 답: a, d, e char type은 '' 작은 따옴표를 쓰고  string type "" 큰따옴표를 쓴다

###연습문제
#### 연습문제 01
```
using System;

namespace RectArea
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("사각형의 너비를 구하세요.");
            string width = Console.ReadLine();

            Console.WriteLine("사각형의 높이를 입력하세요.");
            string height = Console.ReadLine();

            int result = int.Parse(width) * int.Parse(height);

            Console.WriteLine("사각형의 넓이는: " + result);
        }
    }
}
```
####연습문제02
```
int a = 7.3
float b = 3.14;
double c = a*b;
char d = "abc";
string e = '한'
```
##### 문제 풀이 
1. int 는 정수형 이므로 소수점을 나타낼수 없다
2. float b = 3.14 는 3.14f 부동소수를 나타내야 한다
3. int*float 은 float 이다
4. char 는 '' 작은따옴표로 나타낸다
5. string은 "" 큰따옴표로 나타낸다

####연습문제03
##### 값 형식과 참조 형식의 차이는 무엇인가요?
값 형식은 변수가 값을 보유한다
참조 형식은 변수가 값이 아닌 객체의 참조를 보유한다

####연습문제04
##### 박싱과 언박싱을 설명하세요
박싱은 값형식의 값을 참조형식으로 변환을 해주는 것이고, 언박싱은 박싱했던 값은 원래 형식으로 바꿔주는 것이다

####연습문제05
##### 다음 코드를 컴파일한 후의 a와 b는 각각 어떤 데이터 형식이겠습니까?
```
var a = 2020;
var b = "double";
```
##### 답: int, string
