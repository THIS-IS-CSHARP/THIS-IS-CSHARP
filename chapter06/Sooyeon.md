## 1. 다음 코드에서 Square() 메소드를 구현해 프로그램을 완성하세요. Square() 함수는 매개변수를 제곱하여 반환합니다. 프로그램의 실행 예제는 다음과 같습니다.

```csharp
using System;

namespace Ex6_1
{
    class MainApp
    {
        static double Square(double arg)
        {
            // 이 메소드를 구현해주세요.
        }
        
        static void Main(string[] args)
        {
            Console.Write("수를 입력하세요 : ");
            string input = Console.ReadLine();
            double arg = Convert.ToDouble(input);
            
            Console.WriteLine("결과 : {0}", Square(arg));
        }
    }
}
```

### 정답

```csharp
using System;

namespace Ex6_1
{
    class MainApp
    {
        static double Square(double arg)
        {
            return arg * arg;
        }
        
        static void Main(string[] args)
        {
            Console.Write("수를 입력하세요 : ");
            string input = Console.ReadLine();
            double arg = Convert.ToDouble(input);
            
            Console.WriteLine("결과 : {0}", Square(arg));
        }
    }
}
```

## 2. 다음 코드에서 Mean() 메소드를 실행한 후의 mean은 얼마의 값을 가질까요? 3이라고요? 아닙니다. 0입니다. 자, 문제 나갑니다. mean이 0을 갖게 되는 원인은 무엇이며, 이를 바로잡으려면 다음 코드에서 어떤 부분을 고쳐야 할까요?

```csharp
using System;

namespace Ex6_2
{
    class MainApp
    {
        public static void Main()
        {
            double mean = 0;
            Mean(1,2,3,4,5,mean);
            Console.WriteLine("평균 : {0}", mean);
        }
        
        public static void Mean( 
            double a, double b, double c, 
            double d, double e, double mean)
        {
            mean = (a + b + c + d + e) / 5;
        }
    }
}
```

### 정답

```csharp
using System;

namespace Ex6_2
{
    class MainApp
    {
        public static void Main()
        {
            double mean = 0;
            Mean(1,2,3,4,5, ref mean);
            Console.WriteLine("평균 : {0}", mean);
        }
        
        public static void Mean( 
            double a, double b, double c, 
            double d, double e, ref double mean)
        {
            mean = (a + b + c + d + e) / 5;
        }
    }
}
```

값에 의한 전달이 원인이다. ref 키워드를 붙여 참조에 의한 전달로 값을 넘겨줘야 원본 변수를 직접 참조해 값의 변경이 가능하다.

## 3. 다음 코드에 Plus () 메소드가 double형 매개변수를 지원하도로 오버로딩하세요. 이 프로그램이 완성된 후의 실행 결과는 다음과 같아야 합니다.

```
3 + 4 = 7
2.4 + 3.1 = 5.5
```

```csharp
using System;

namespace Ex6_3
{
    class MainApp
    {
        public static void Main()
        {
            int a = 3;
            int b = 4;
            int resultA = 0;
            
            Plus(a,b,out resultA);
            
            Console.WriteLine("{0} + {1} = {2}", a, b, resultA);
            
            double x = 2.4;
            double y = 3.1;
            double resultB = 0;
            
            Plus(x,y,out resultB); // 오버로드가 필요한 메소드입니다.
            
            Console.WriteLine("{0} + {1} = {2}", a, b, resultB);
        }
        
        public static void Plus(int a, int b, out int c)
        {
            c = a + b;    
        } 
        
        // 이 아래에 double 형 매개변수를 받을 수 있도록
        // 오버로딩된 Plus() 메소드를 작성하세요.
        
    }
}
```

### 정답

```csharp
using System;

namespace Ex6_3
{
    class MainApp
    {
        public static void Main()
        {
            int a = 3;
            int b = 4;
            int resultA = 0;
            
            Plus(a,b,out resultA);
            
            Console.WriteLine("{0} + {1} = {2}", a, b, resultA);
            
            double x = 2.4;
            double y = 3.1;
            double resultB = 0;
            
            Plus(x,y,out resultB); // 오버로드가 필요한 메소드입니다.
            
            Console.WriteLine("{0} + {1} = {2}", a, b, resultB);
        }
        
        public static void Plus(int a, int b, out int c)
        {
            c = a + b;    
        } 
        
        // 이 아래에 double 형 매개변수를 받을 수 있도록
        // 오버로딩된 Plus() 메소드를 작성하세요.
        public static void Plus(double x, double y, out double c)
        {
            c = x + y;
        }

   
```
