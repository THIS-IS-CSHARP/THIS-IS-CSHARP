## 연습문제
### 01 Func 대리자 출력 값
- 결과를 반환하는 메소드를 참조
```C#
namespace FuncTest
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // 출력 매개변수 1개
            Func<int> func_1 = () => 10;

            // 입력 매개변수 1개, 출력 매개변수 1개
            Func<int, int> func_2 = (a) => a * 2;

            Console.WriteLine(func_1() + func_2(30)); // 출력: 70
           
        }
    }
}
```
