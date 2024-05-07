# 비타민 퀴즈 5-1 (188P)

```csharp
using System;
class Car
{
    public string Model { get; set; }
    public DateTime ProducedAt { get; set; }

    public static string GenerateMessage(Car car, string nickname)
    {
        return $"{car.Model} produced in {car.ProducedAt.Year} is {nickname}";
    }
}

class Program
{
    static string GetNickname(Car car)
    {
        if (car.Model == "Mustang" && car.ProducedAt.Year == 1967)
            return Car.GenerateMessage(car, "Fastback");
        else if (car.Model == "Mustang" && car.ProducedAt.Year == 1976)
            return Car.GenerateMessage(car, "Cobra II");
        else
            return Car.GenerateMessage(car, "Unknown");
    }

    static void Main(string[] args)
    {
        Console.WriteLine(
            GetNickname(new Car() { Model = "Mustang", ProducedAt = new DateTime(1967, 11, 23) }));
        Console.WriteLine(
            GetNickname(new Car() { Model = "Mustang", ProducedAt = new DateTime(1976, 6, 7) }));
        Console.WriteLine(
            GetNickname(new Car() { Model = "Mustang", ProducedAt = new DateTime(2099, 12, 25) }));
    }

}
```
### 위 예제의 GetNickname() 메소드를 is 연산자 대신 switch 식을 이용해서 다시 구현해보세요.

```csharp
using System;
class Car
{
    public string Model { get; set; }
    public DateTime ProducedAt { get; set; }

    public static string GenerateMessage(Car car, string nickname)
    {
        return $"{car.Model} produced in {car.ProducedAt.Year} is {nickname}";
    }
}

class Program
{
    static string GetNickname(Car car)
    {
        string nick = car.ProducedAt.Year switch
        {
            1967 => Car.GenerateMessage(car, "Fastback"),
            1976 => Car.GenerateMessage(car, "Cobra II"),
            _ => Car.GenerateMessage(car, "Unknown")
        };

        return nick;
    }

    static void Main(string[] args)
    {
        Console.WriteLine(
            GetNickname(new Car() { Model = "Mustang", ProducedAt = new DateTime(1967, 11, 23) }));
        Console.WriteLine(
            GetNickname(new Car() { Model = "Mustang", ProducedAt = new DateTime(1976, 6, 7) }));
        Console.WriteLine(
            GetNickname(new Car() { Model = "Mustang", ProducedAt = new DateTime(2099, 12, 25) }));
    }

}
```

# 연습문제 5-1 (196P)
```csharp
*
**
***
****
*****
```
### 다음과 같은 결과를 출력하는 프로그램을 for 문을 이용하여 작성하세요.
```csharp
using System;

namespace printStar
{
    class MainApp
    {
        static void Main(string[] args)
        {
            for (int i = 0; i < 5; i++)
            {
                for (int j = 0; j <= i; j++)
                {
                    Console.Write("*");
                }
                Console.WriteLine();
            }
        }
    }
}
```

# 연습문제 5-2
```csharp
*****
****
***
**
*
```
### 다음과 같은 결과를 출력하는 프로그램을 for 문을 이용하여 작성하세요.
```csharp
using System;

namespace printStar
{
    class MainApp
    {
        static void Main(string[] args)
        {
            for (int i = 0; i < 5; i++)
            {
                for (int j = i; j < 5; j++)
                {
                    Console.Write("*");
                }
                Console.WriteLine();
            }
        }
    }
}
```

# 연습문제 5-3
### 1번과 2번을 for문 대신 while과 do 문으로 바꿔서 각각 작성하세요.
```csharp
using System;

namespace printStar
{
    class MainApp
    {
        static void Main(string[] args)
        {
            int i = 0;
            while (i < 5)
            {
                int j = 0;
                while (j <= i)
                {
                    Console.Write("*");
                    j++;
                }
                i++;
                Console.WriteLine();
            }
        }
    }
}
```
```csharp
using System;

namespace printStar
{
    class MainApp
    {
        static void Main(string[] args)
        {
            int i = 0;
            while (i < 5)
            {
                int j = i;
                while (j < 5)
                {
                    Console.Write("*");
                    j++;
                }
                i++;
                Console.WriteLine();
            }
        }
    }
}
```
```csharp
using System;

namespace printStar
{
    class MainApp
    {
        static void Main(string[] args)
        {
            int i = 0;
            do
            {
                int j = 0;
                do
                {
                    Console.Write("*");
                    j++;
                } while (j <= i);
                i++;
                Console.WriteLine();
            } while (i < 5);
        }
    }
}
```
```csharp
using System;

namespace printStar
{
    class MainApp
    {
        static void Main(string[] args)
        {
            int i = 0;
            do
            {
                int j = i;
                do
                {
                    Console.Write("*");
                    j++;
                } while (j < 5);
                i++;
                Console.WriteLine();
            } while (i < 5);
        }
    }
}
```

# 연습문제 5-4
```csharp
반복 횟수를 입력하세요. : -10
0보다 같거나 작은 수는 사용할 수 없습니다.

반복 횟수를 입력하세요. : 5
*
**
***
****
*****
```
### 다음과 같이 사용자로부터 입력받은 횟수만큼 별을 반복 출력하는 프로그램을 작성하세요.

```csharp
using System;

namespace star
{
    class MainApp
    {
        static void Main(string[] args)
        {
            Console.WriteLine("횟수 :");
            int input = int.Parse(Console.ReadLine());
            if (input < 0)
            {
                Console.WriteLine("0보다 같거나 작은 숫자는 사용할 수 없습니다.");
                return;
            }
            else
            {
                for (int i = 0; i < input; i++)
                {
                    for (int j = 0; j <= i; j++)
                    {
                        Console.Write("*");
                    }
                    Console.WriteLine();
                }
            }
        }
    }
}
```

# 연습문제 5-5
```csharp
using System;
class Fibonacci
{
    public static long GetNumber(long index)
    {
        long result = 0;
        
        switch (index)
        {
            case 0:
                result = 0;
                break;
            case 1:
                result = 1;
                break;
            default:
                result = GetNumber(index -1) + GetNumber(index - 2);
                break;
        }
        return result;
    }
}
```
### 다음 Fibonacci 클래스의 GetNumber() 메소드에서 switch 문을 switch 식으로 변경하세요.

```csharp
using System;
class Fibonacci
{
    public static long GetNumber(long index)
    {
        long result = index switch
        {
            0 => 0,
            1 => 1,
            _ => GetNumber(index - 1) + GetNumber(index - 2)
		};
        return result;
    }
}
```