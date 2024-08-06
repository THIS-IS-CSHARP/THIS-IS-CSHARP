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


## 02 익명메소드를 람다식으로 수정

```C#
namespace LambdaExpression
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] array = { 11, 22, 33, 44, 55 };
            foreach (int a in array)
            {

                // 람다식으로 수정
                Action action = () => Console.WriteLine(a * a);

                // 익명 메소드 실행
                action.Invoke();

            }
        }
    }
}

```
