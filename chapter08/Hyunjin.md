# VITAMIN QUIZ 8-1  앞의 예제 프로그램에서 ClimateMonitor의 logger가 FileLogger 대신 ConsoleLogger의 객체를 가리키도록 바꿔서 테스트해보세요.
```
using System;
using System.IO;

namespace Interface
{
    interface ILogger
    {
        void WriteLog(string message);
    }
    
    class ConsoleLogger : ILogger
    {
        public void WriteLog(string message)
        {
            Console.WriteLine("{0} {1}", DateTime.Now.ToLocalTime(), message);
        }
    }
    
    class FileLogger : ILogger
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
                if (temperature == "")
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

# VITAMIN QUIZ 8-2 여기에 인터페이스 둘(IFlyable, IRunnable)과 이 두 인터페이스를 각각 상속하는 두 개의 클래스(Plane, Car), 그리고 두 인터페이스를 동시에 상속(다중 상속)하는 하나의 클래스(FlyingCar)가 있습니다.
# 이들을 이용해서 인터페이스 다중 상속과 포함 기법을 활용해 클래스 다중 상속을 흉내내보세요.

```
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

    class Car : IRunnable
    {
        public void Run()
        {
            Console.WriteLine("Car is running!");
        }
    }

    class Plane : IFlyable
    {
        public void Fly()
        {
            Console.WriteLine("Plane is flying!");
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

            IRunnable runnable = flyingCar as IRunnable;
            runnable.Run();

            IFlyable flyable = flyingCar as IFlyable;
            flyable.Fly();
        }
    }
}


```


# 연습문제 1. 인터페이스와 클래스카 다른점은 무엇입니까?

## 클래스
클래스는 객체를 생성하기 위한 템플릿입니다. 상태와 메서드을 정의합니다.
클래스는 단일 상속만 가능하다.
클래스의 인스턴스를 생성할 수 있습니다.

## 인터페이스
인터페이스는 클래스나 구조체가 구현해야 하는 메서드, 속성, 이벤트 및 인덱서를 정의합니다.
인터페이스는 다중 상속이 가능합니다.
인터페이스 자체의 인스턴스를 생성할 수 없습니다.

# 2. 연습문제 인터페이스와 추상 클래스가 다는 점은 무엇입니까?

## 인터페이스
다중 상속이 가능합니다.
모든 접근제어자가 기본적으로 public이다

## 추상클래스
단일 상속만 가능합니다
다양한 접근제어자 사용 가능합니다.

