# 비타민 퀴즈 8-1 (321P)
### 앞의 예제 프로그램에서 ClimateMonitor의 logger가 FileLogger 대신 ConsoleLogger의 객체를 가리키도록 바꿔서 테스트해보세요.
```csharp
using System;
using System.IO;

namespace Vitamin8_1
{
    interface ILogger
    {
        void WriteLog(string message);
    }

    class ConsoleLogger : ILogger
    {
        public void WriteLog(string message)
        {
            Console.WriteLine(
                "{0} {1}",
                DateTime.Now.ToLocalTime(), message);
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
            while (true)
            {
                Console.Write("온도를 입력해주세요 .: ");
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
            //ClimateMonitor monitor = new ClimateMonitor(
            //    new FileLogger("MyLog.txt"));
            //monitor.start();

            ClimateMonitor monitor = new ClimateMonitor(
                new ConsoleLogger());
            monitor.start();
        }
    }
}
```


# 비타민 퀴즈 8-2 (328P)
### 여기에 인터페이스 둘(IFlyable, IRunnable)과 이 두 인터페이스를 각각 상속하는 두 개의 클래스(Plane, Car), 그리고 두 인터페이스를 동시에 상속(다중 상속)하는 하나의 클래스(FlyingCar)가 있습니다. 이들을 이용해서 인터페이스 다중 상속과 포함 기법을 활용해 클래스 다중 상속을 흉내내보세요.

```csharp
using System;

namespace Vitamin8_2
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
            Console.WriteLine("Run! Run!");
        }
    }

    class Plane : IFlyable
    {
        public void Fly()
        {
            Console.WriteLine("Fly! Fly!");
        }
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

    class MyVehicle
    {
        IRunnable car;
        IFlyable plane;

        public MyVehicle(FlyingCar fc)
        {
            this.car = fc;
            this.plane = fc;
        }
        public MyVehicle(Car c, Plane p) 
        {
            this.car = c;
            this.plane = p;
        }

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
            MyVehicle a = new MyVehicle(new FlyingCar());
            a.Run();
            a.Fly();

            MyVehicle b = new MyVehicle(new Car(), new Plane());
            b.Run();
            b.Fly();
        }
    }
}
```
참고: https://cafe.naver.com/thisiscsharp/462  
포함(Containment) - 326P  
클래스 안에  
물려받고 싶은 기능을 가진 클래스들을  
필드로 선언해 넣는 것.  

매개변수로, 물려받고 싶은 메서드를 가지고 있는 클래스의, 객체를 전달 받는 생성자 함수를 오버로딩.  
클래스에 '포함'된 객체의 메서드를 사용하여 다중상속을 흉내.

# 연습문제 8-1 (335P)
### 인터페이스와 클래스가 다른 점은 무엇입니까?
인터페이스는...  
1. 메서드, 이벤트, 인덱서, 프로퍼티'만' 가질 수 있다.  
2. 메서드 구현부가 없다.  
3. 접근 제한 한정자를 사용할 수 없고 모든 것이 public으로 선언된다.   
4. 인스턴스를 만들 수 없다.  
5. 인터페이스를 상속받은 클래스는 인터페이스에 선언된 메서드를 구현해야한다.  
6. 구현된 메서드들은 public 한정자로 수식해야한다.  

# 연습문제 8-2
### 인터페이스와 추상 클래스가 다른 점은 무엇입니까?
추상 클래스는...  
1. 선언할 때 abstract 한정자가 붙는다.  
2. 구현부를 가진 메서드를 가질 수 있다.  
3. 구현부가 없는 '추상 메서드'가 하나라도 있으면 추상 클래스다.  
4. 추상 클래스는 추상 클래스를 상속할 수 있고 추상 메서드를 구현하지 않아도 된다.  
5. 단, 객체를 생성하는 추상 클래스는 추상 메서드를 구현해야한다.  