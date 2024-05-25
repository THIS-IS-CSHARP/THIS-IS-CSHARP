# 연습문제

## 1. 인터페이스와 클래스가 다른 점은 무엇입니까?

### 정답

클래스는 멤버변수, 생성자, 멤버함수를 가진다.

인터페이스는 메소드, 이벤트, 인덱서, 프로퍼티만을 가질 수 있으며, 구현부가 없다. 

클래스는 접근 제한 한정자로 수식하지 않으면 기본적으로 private로 선언되지만, 인터페이스는 접근 제한 한정자를 사용할 수 없고 모든 것이 public으로 선언된다. 

인터페이스는 인스터스 생성이 불가능하다. 인터페이스는 구현 클래스를 통해 간접적으로 사용된다.

## 2. 인터페이스와 추상 클래스가 다른 점은 무엇입니까?

### 정답

인터페이스는 구현부가 없으나, 추상 클래스는 구현을 가질 수 있다. 

모든 메소드가 public으로 선언되는 인터페이스와 다른게 클래스는 한정자를 명시하지 않으면 모든 메소드가 private로 선언된다.

## Vitamin Quiz

## 8-1

```csharp
using System;
using System.IO;

namespace Interface
{
    interface ILogger
    {
        void WriteLog(string message);
    }
    
    class ConsoleLogger: ILogger
    {
        public void WriteLog(string message)
        {
            Console.WriteLine("{0} {1}", DateTime.Now.ToLocalTime(), message);
        }
    }
    
    class FileLogger: ILogger
    {
        private StreamWriter writer;
        
        public FileLogger(string path)
        {
            writer = File.CreateText(path);
            writer.AutoFlush = true;
        }
        
        public void WriteLog(string message)
        {
            writer.WriteLine("{0} {1}", DateTime.Now.ToShortTimeString(), message);
        }
        
    }
    
    class ClimateMonitor
    {
        private ILogger logger;
        public ClimateMonitor(ILogger logger)
        {
            this.logger = logger;
        }
        
        public void start()
        {
            while(true)
            {
                Console.Write("온도를 입력해주세요: ");
                string temperature = Console.ReadLine();
                if(temperature == "")
                    break;
                
                logger.WriteLog("현재 온도 : " + temperature);
            }
        }
    }
    
    class MainApp
    {
        static void Main(string[] args)
        {
            ClimateMonitor monitor = new ClimateMonitor(new FileLogger("MyLog.txt"));
            monitor.start();
        }
    }
    
}
```

앞의 예제 프로그램에서 ClimateMonitor의 logger가 FileLogger 대신 ConsoleLogger의 객체를 가리키도록 바꿔서 테스트해보세요.

### 결과

```csharp
using System;
using System.IO;

namespace Interface
{
    interface ILogger
    {
        void WriteLog(string message);
    }
    
    class ConsoleLogger: ILogger
    {
        public void WriteLog(string message)
        {
            Console.WriteLine("{0} {1}", DateTime.Now.ToLocalTime(), message);
        }
    }
    
    class FileLogger: ILogger
    {
        private StreamWriter writer;
        
        public FileLogger(string path)
        {
            writer = File.CreateText(path);
            writer.AutoFlush = true;
        }
        
        public void WriteLog(string message)
        {
            writer.WriteLine("{0} {1}", DateTime.Now.ToShortTimeString(), message);
        }
        
    }
    
    class ClimateMonitor
    {
        private ILogger logger;
        public ClimateMonitor(ILogger logger)
        {
            this.logger = logger;
        }
        
        public void start()
        {
            while(true)
            {
                Console.Write("온도를 입력해주세요: ");
                string temperature = Console.ReadLine();
                if(temperature == "")
                    break;
                
                logger.WriteLog("현재 온도 : " + temperature);
            }
        }
    }
    
    class MainApp
    {
        static void Main(string[] args)
        {
            ClimateMonitor monitor = new ClimateMonitor(new ConsoleLogger());
            monitor.start();
        }
    }
    
}
```

## 8-2

```csharp
using System;

namespace MultiInterfaceInheritance
{
    interface IRunnable
    {
        void Run();
    }
    
    interface IFlyable
    {
        void Fly();
    }
    
    class FlyingCar : IRunnable, IFlyable
    {
        public void Run()
        {
            Console.WriteLine("Run! Run!");
        }
        
        public void Fly()
        {
            Console.WriteLine("Fly! Fly!");
        }
    }
    
    class MainApp
    {
        static void Main(string[] args)
        {
            FlyingCar car = new FlyingCar();
            car.Run();
            car.Fly();
            
            IRunnable runnable = car as IRunnable;
            runnable.Run();
            
            IFlyable flyable = car as IFlyable;
            flyable.Fly();
        }
    }
}
```

여기에 인터페이스 둘(IFlyable, IRunnable)과 이 두 인터페이스를 각각 상속하는 두 개의 클래스(Plane, Car), 그리고 두 인터페이스를 동시에 상속( 다중 상속 )하는 하나의 클래스(FlyingCar)가 있습니다. 이들을 이용해서 인터페이스 다중 상속과 포함 기법을 활용해 클래스 다중 상속을 흉내내보세요.

### 결과

```csharp
using System;

namespace MultiInterfaceInheritance
{
    interface IRunnable
    {
        void Run();
    }
    
    interface IFlyable
    {
        void Fly();
    }
    
    class Plane : IFlyable
    {
        public void Fly()
        {
            Console.WriteLine("Fly! Fly!");
        }
    }
    
    class Car : IRunnable
    {
        public void Run()
        {
            Console.WriteLine("Run! Run!");
        }
    }
    
    class FlyingCar : IRunnable, IFlyable
    {
        private Car car = new Car();
        private Plane plane = new Plane();
        
        public void Run()
        {
            car.Run();
        }
        
        public void Fly()
        {
            plane.Fly();
        }
    }
    
    class MainApp
    {
        static void Main(string[] args)
        {
            FlyingCar flyingCar = new FlyingCar();
            flyingCar.Run();
            flyingCar.Fly();
        }
    }
}
```
