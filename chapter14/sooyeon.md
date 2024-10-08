# 연습문제

## 1. **다음 코드의 출력 결과값은 얼마일까요?**

```
Func<int> func_1 = () => 10;
Func<int, int> func_2 = () => a * 2;

Console.WriteLine(func_1() + func_2(30));
```

### 정답

```
70
```

</br>
</br>


## 2. **다음 코드에서 익명 메소드를 람다식으로 수정하세요.**

```csharp
using System;
namespace Ex14_2
{
    class MainApp
    {
        static void Main(string[] args)
        {
            int[] array = {11, 22, 33, 44, 55};
            
            foreach (int a in array)
            {
                Action action = new Action
                (
                    delegate()
                    {
                        Console.WriteLine(a*a);
                    }
                );
                action.Invoke();
                
            }
        }
    }
}
```

### 정답

```csharp
using System;
namespace Ex14_2
{
    class MainApp
    {
        static void Main(string[] args)
        {
            int[] array = {11, 22, 33, 44, 55};
            
            foreach (int a in array)
            {
                Action action = () => Console.WriteLine(a*a);
                action.Invoke();
            }
        }
    }
}
```
