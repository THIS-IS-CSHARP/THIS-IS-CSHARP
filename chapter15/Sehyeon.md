## 연습문제
### 01. Cost 50이상, MaxSpeed 150이상인 LINQ 작성
```C#
namespace CarSelectLINQ
{

    class Car
    {
        public int Cost { get; set; }
        public int MaxSpeed { get; set; }
    }
    }
    internal class Program
    {

    
        static void Main(string[] args)
        {
        // 클래스 기반 배열 선언
        Car[] cars = {
                        new Car() {Cost =56, MaxSpeed = 120},
                        new Car() {Cost =70, MaxSpeed = 150},
                        new Car() {Cost =45, MaxSpeed = 180},
                        new Car() {Cost =32, MaxSpeed = 200},
                        new Car() {Cost =82, MaxSpeed = 280},

                    };

        // Cost 가 50 이상, MaxSpeed는 150인 레코드를 조회하는 LINQ
        var selected = from car in cars
                       where car.Cost > 50 && car.MaxSpeed >= 150
                       orderby car.Cost
                       select car;

        // 실행 결과
        foreach (var car in selected)
            Console.WriteLine("{0}, {1}", car.Cost, car.MaxSpeed);
    }
}

```
