# 연습문제

## 1. 다음 코드를 컴파일하면 실행 결과처럼 예외를 표시하고 비정상 종료합니다. try~catch 문을  이용해서 예외를 안전하게 처리하도록 코드를 수정하세요.

```csharp
using System;
namespace Ex12_1 
  { 
    class MainApp
    { 
      static void Main(string[] args) 
      { 
        int[] arr = new int[10];
        
        for(int i = 0; i < 10; i++)
          arr[i] = i;
          
        for(int i = 0; i< 11; i++)
          Console.WriteLine(arr[i]);
      }
    }
  }
```

```
실행결과

0
1
2
3
4
5
6
7
8
9
처리되지 않은 예외: System.IndexOutOfRangeException: 인덱스가 배열 범위를 벗어났습니다.
위치: Ex12_1.MainApp.Main(String[] args) 파일 C:\Users\seanl\source\repos\ThisisCSharp11\ Ex12_1\MainApp.cs:줄 9
```

### 정답

```csharp
using System;
namespace Ex12_1 
  { 
    class MainApp
    { 
      static void Main(string[] args) 
      { 
        int[] arr = new int[10];
        try
        {
          for(int i = 0; i < 10; i++)
            arr[i] = i;
          
          for(int i = 0; i< 11; i++)
            Console.WriteLine(arr[i]);
        }
        catch (IndexOutOfRangeException e)
        {
          Console.WriteLine(e);
        }
      }
    }
  }
```