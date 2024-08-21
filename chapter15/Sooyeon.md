# 연습문제

## 1. 다음과 같은 배열이 있다고 할 때,  Cost는 50 이상, MaxSpeed는 150 이상인 레코드만 조회하는 LINQ를 작성하세요.

```csharp
class Car{
    public int Cost { get;, set; };
    public int MaxSpeed { get;, set; };
}

// ...

Car[] cars = {
    new Car(){Cost=56, MaxSpeed=120};
    new Car(){Cost=70, MaxSpeed=150};
    new Car(){Cost=45, MaxSpeed=180};
    new Car(){Cost=32, MaxSpeed=200};
    new Car(){Cost=82, MaxSpeed=280};
}

var selected = /* Cost가 50 이상, MaxSpeed는 150 이상인 레코드를 조회하는 LINQ */
```

### 정답

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace Ex15_1{
    class Car{
        public int Cost { get; set; }
        public int MaxSpeed { get; set; }
    }
    
    class MainApp{
        static void Main(string[] args){
            Car[] cars = {
                new Car(){Cost=56, MaxSpeed=120},
                new Car(){Cost=70, MaxSpeed=150},
                new Car(){Cost=45, MaxSpeed=180},
                new Car(){Cost=32, MaxSpeed=200},
                new Car(){Cost=82, MaxSpeed=280}
            };
            
            var selected = from car in cars
                            where car.Cost >= 50 && car.MaxSpeed >=150
                            orderby car.Cost
                            select car;
                            
            foreach(var car in selected)
                Console.WriteLine("Const:{0}, MaxSpeed:{1}",car.Cost, car.MaxSpeed);
        }
    }
}
```

</br>
</br>


## 2. **다음 코드에서 cars.Where(c ⇒ c.Cost < 60).OrderBy(c ⇒ c.Cost)와 동일한 결과를 반환하는 LINQ를 작성하세요.**

```csharp
class Car{
    public int Cost { get;, set; };
    public int MaxSpeed { get;, set; };
}

// ...

Car[] cars = {
    new Car(){Cost=56, MaxSpeed=120};
    new Car(){Cost=70, MaxSpeed=150};
    new Car(){Cost=45, MaxSpeed=180};
    new Car(){Cost=32, MaxSpeed=200};
    new Car(){Cost=82, MaxSpeed=280};
}

var selected = cars.Where(c ⇒ c.Cost < 60).OrderBy(c ⇒ c.Cost);
```

### 정답

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace Ex15_1{
    class Car{
        public int Cost { get; set; }
        public int MaxSpeed { get; set; }
    }
    
    class MainApp{
        static void Main(string[] args){
            Car[] cars = {
                new Car(){Cost=56, MaxSpeed=120},
                new Car(){Cost=70, MaxSpeed=150},
                new Car(){Cost=45, MaxSpeed=180},
                new Car(){Cost=32, MaxSpeed=200},
                new Car(){Cost=82, MaxSpeed=280}
            };
            
            var selected = from car in cars
                            where car.Cost < 60
                            orderby car.Cost
                            select car;
                            
            foreach(var car in selected)
                Console.WriteLine("Const:{0}, MaxSpeed:{1}",car.Cost, car.MaxSpeed);
        }
    }
}

```
