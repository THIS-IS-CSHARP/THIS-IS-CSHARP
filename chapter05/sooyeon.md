## 연습문제

## 1. 다음과 같은 결과를 출력하는 프로그램을 for문을 이용하여 작성하세요. 규칙은 첫 번째 줄에 별 1개, 두 번째 줄에 별 2개, 세 번째 줄에 별 3개 ・・・ 이런 식으로 별 5개가 찍힐 때까지 반복합니다.(힌트: for문 블록 안에 for 문 블록을 넣으세요.)

```
*
**
***
****
*****
```

### 정답

```csharp
using System;
class Stars {
  static void Main() {
    for(int i = 0; i < 5; i++)
    {
        for(int j = 0; j < i+1; j++)
        {
            Console.Write("*");
        }
        Console.WriteLine("");
    }
    
  }
}
```

<br>

## 2. 다음과 같은 결과를 출력하는 프로그램을 for 문을 이용하여 작성하세요.

```
*****
****
***
**
*
```

### 정답

```csharp
using System;
class StarsReverse {
  static void Main() {
    for(int i = 0; i < 5; i++)
    {
        for(int j = 5 - i; j > 0; j--)
        {
            Console.Write("*");
        }
        Console.WriteLine("");
    }
    
  }
}
```

<br>

## 3. 1번과 2번을 for 문 대신 while 문과 do 문으로 바꿔서 각각 작성하세요.

### 정답

```csharp
// 1번 while문  

using System;
class Stars {
  static void Main() {
    int i = 0;
    while(i<5){
        int j = 0;
        while(j<i+1){
            Console.Write("*");
            j++;
        }
        Console.WriteLine("");
        i++;
    }
  }
}
```

```csharp
// 1번 do while문

using System;
class Stars {
  static void Main() {
    int i = 0;
    do{
        int j = 0;
        do{
            Console.Write("*");
            j++;
        }while(j<i+1);
        Console.WriteLine("");
        i++;
    }while(i<5);
  }
}
```

```csharp
// 2번 while문 

using System;
class StarsReverse {
  static void Main() {
    int i = 0;
    while(i<5){
        int j = 5 - i;
        while(j>0){
            Console.Write("*");
            j--;
        }
        i++;
        Console.WriteLine("");
    }
  }
}
```

```csharp
// 2번 do while문

using System;
class StarsReverse {
  static void Main() {
    int i = 0;
    do{
        int j = 5-i;
        do{
            Console.Write("*");
            j--;
        }while(j>0);
        i++;
        Console.WriteLine("");
    }while(i<5);
  }
}
```

<br>

## 4. 다음과 같이 사용자로부터 입력받은 횟수만큼 별을 반복 출력하는 프로그램을 작성하세요. 단, 입력받은 수가 0보다 작거나 같을 경우 ‘0보다 같거나 작은 숫자는 사용할 수 없습니다.’라는 메시지를 띄우고 프로그램을 종료합니다.

```
반복 횟수를 입력하세요. : -10
0보다 같거나 작은 수는 사용할 수 없습니다.

반복 횟수를 입력하세요 : 5
*
**
***
****
*****
```

### 정답

```csharp
using System;
class Stars {
  static void Main() {
    Console.Write("반복 횟수를 입력하세요. : "); 
    string input = Console.ReadLine(); 
    int num = Int32.Parse(input); 
    if(num <= 0){
        Console.WriteLine("0보다 같거나 작은 수는 사용할 수 없습니다."); 
    } else{
        Console.WriteLine("");
        for(int i = 0; i < num; i++){
            for(int j = 0; j < i+1; j++){
                Console.Write("*");
            }
            Console.WriteLine("");
        }
    }
  }
}
```

<br>

## 5. 다음 Fibonacci 클래스의 GetNumber() 메소드에서 switch 문을 switch 식으로 변경하세요.

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
                result = GetNumber(index - 1) + GetNumber(index - 2);
                break;
        }
        return result;
    }

    static void Main()
    {
        Console.Write("피보나치 수열의 인덱스를 입력하세요: ");
        long index = Convert.ToInt64(Console.ReadLine());

        long number = GetNumber(index);
        Console.WriteLine($"피보나치 수열의 {index}번째 수는 {number}입니다.");
    }
}

```

### 정답

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

    static void Main()
    {
        Console.Write("피보나치 수열의 인덱스를 입력하세요: ");
        long index = Convert.ToInt64(Console.ReadLine());

        long number = GetNumber(index);
        Console.WriteLine($"피보나치 수열의 {index}번째 수는 {number}입니다.");
    }
}

```
