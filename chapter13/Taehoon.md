# 연습문제 13-1
### 출력 결과가 다음과 같이 나오도록 다음 코드에 익명 메소드를 추가하여 완성하세요.

```cs
using System;

namespace Ex13_1
{
    delegate int MyDelegate(int a, int b);
    class MainApp
    {
        static void Main(string[] args)
        {
            MyDelegate Callback;

            Callback = /* 익명 메소드 선언 1 */

            Console.WriteLine(Callback(3, 4));

            Callback = /* 익명 메소드 선언 2 */

            Console.WriteLine(Callback(7, 5));
        }
    }
}
```

### 정답
```cs
namespace Ex13_1
{
    delegate int MyDelegate(int a, int b);
    class MainApp
    {
        static void Main(string[] args)
        {
            MyDelegate Callback;

            Callback = delegate (int a, int b)
            {
                return a + b;
            };

            Console.WriteLine(Callback(3, 4));

            Callback = Callback = delegate (int a, int b)
            {
                return a - b;
            };

            Console.WriteLine(Callback(7, 5));
        }
    }
}
```

# 연습문제 13-2
### 출력 결과가 다음과 같이 나오도록 다음 코드에 이벤트 처리기를 추가하세요.

### 출력 결과
```
축하합니다! 30번째 고객 이벤트에 당첨되셨습니다.
```

### 정답
```cs
namespace Ex13_2
{
    delegate void MyDelegate(int a);
    class Market
    {
        public event MyDelegate CustomerEvent;

        public void BuySomething(int CustomerNo)
        {
            if(CustomerNo == 30)
            {
                CustomerEvent(CustomerNo);
            }
        }
    }

    class MainApp
    {
        static void Main(string[] args)
        {
            static void MyHandler(int a)
            {
                Console.WriteLine("축하합니다! {0}번째 고객 이벤트에 당첨되셨습니다.", a);
            }
            Market market = new Market();
            market.CustomerEvent += new MyDelegate(MyHandler);

            for (int customerNo = 0; customerNo < 100; customerNo += 10)
            {
                market.BuySomething(customerNo);
            }
        }
    }
}

```
