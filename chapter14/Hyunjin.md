# 연습문제 01
## 다음 코드의 출력 결과 값은 얼마일까요?
```
Func<int> func_1 = () => 10;
Func<int, int> func_2 = () => a * 2;

Console.WriteLine(func_1() + func_2(30));

```
## 정답
10 + 60 = 70

# 연습문제 02
## 다음 코드에서 익명 메소드를 람다식으로 수정하세요

## 수정
```
using system
namespace Ex14_2
{
    class MainApp
    {
        static void Main(string[] args)
        {
            int[] array = { 11, 22, 33, 44, 55 };

            foreach (int a in array)
            {
                Action action = () => Console.WriteLine(a * a);

                action.Invoke ();
            };
        }
    }
}
```
