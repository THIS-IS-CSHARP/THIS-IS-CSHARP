# 연습문제

## 1. 다음 코드에서 NameCard 클래스의 GetAge(), SetAge(), GetName(), SetName() 메소드들을 프로퍼티로 변경해 작성하세요.

```csharp
using System;
namespace Ex9_1{
    class NameCard
    {
        private int age;
        private string name;
        
        public int GetAge(){ return age; }
        public void SetAge(int value){ age = value;}
        
        public string GetName(){ return name; }
        public void SetName(string value){ name = value; }
    }
    
    class MainApp
    {
        public static void Main()
        {
            NameCard MyCard = new NameCard();
            
            MyCard.SetAge(24);
            MyCard.SetName("상현");
            
            Console.WriteLine("나이 : {0}", MyCard.GetAge());
            Console.WriteLine("이름 : {0}", MyCard.GetName());
        }
    }
}
```

### 정답

```csharp
using System;
namespace Ex9_1{
    class NameCard
    {
        private int age;
        private string name;
        
        public int Age{ get; set;}
        public string Name{ get; set;}
    }
    
    class MainApp
    {
        public static void Main()
        {
            NameCard MyCard = new NameCard();
            
            MyCard.Age = 24;
            MyCard.Name = "상현";
            
            Console.WriteLine("나이 : {0}", MyCard.Age);
            Console.WriteLine("이름 : {0}", MyCard.Name);
        }
    }
}
```

## 2. 다음 프로그램을 완성해서 다음과 같은 결과를 출력하도록 하세요. 단, 무명 형식을 이용해야 합니다.

```
이름:박상현, 나이:17
Real:3, Imaginary:-12
```

```csharp
using System;
namespace Ex9_2{
    class MainApp
    {
        static void Main(string[] args)
        {
            var nameCard = /* 무명 형식을 이용해서 완성하세요.*/;
            Console.WriteLine("이름:{0}, 나이:{1}", nameCard.Name, nameCard.Age);
            
            var complex = /* 무명 형식을 이용해서 완성하세요.*/;
            Console.WriteLine("Real:{0}, Imaginary:{1}", complex.Real, complex.Imaginary);
        }
    }
}
```

### 정답

```csharp
using System;
namespace Ex9_2{
    class MainApp
    {
        static void Main(string[] args)
        {
            var nameCard = new { Name = "박상현", Age ="17" };
            Console.WriteLine("이름:{0}, 나이:{1}", nameCard.Name, nameCard.Age);
            
            var complex = new { Real = "3", Imaginary = "-12"};
            Console.WriteLine("Real:{0}, Imaginary:{1}", complex.Real, complex.Imaginary);
        }
    }
}
```
