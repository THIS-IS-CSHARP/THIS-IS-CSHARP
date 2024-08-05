# 연습문제
## 01. 익명 메소드
- 대리자가 참조할 메소드를 넘겨야하는데, 한번만 사용할 경우 익명메소드를 사용
```C#
namespace AnonymousMethod
{

    // 대리자 선언
    delegate int MyDelegate(int a, int b);
    internal class Program
    {
        static void Main(string[] args)
        {

            MyDelegate Callback;

            // 대리자를 참조 Callback에 할당
            Callback = delegate (int a, int b)
            {
                return a + b;
            };
            Console.WriteLine(Callback(3, 4)); // 출력: 7

            Callback = delegate (int a, int b)
            {
                return a - b;
            };

            Console.WriteLine(Callback(7, 5)); // 출력: 2

        }
    }
}


```

## 02. 이벤트

- 이벤트는 외부에서 직접 사용할수 없다.
- 객체의 상태 변화나 사건의 발생을 알리는 용도로 구분해서 사용

```C#
namespace EventTest
{

    // 대리자 선언
    delegate void MyDelegate(int a);

    class Market
    {
        // event 한정자로 선언
        public event MyDelegate CustomerEvent;

        public void BuySomething(int CustomerNo) 
        {
        if(CustomerNo == 30)
            {
                // 이벤트 객체는 내부에서만 사용가능
                CustomerEvent(CustomerNo);
            }

        }
    }
    internal class Program
    {

        // 이벤트 처리기 구현
        static public void MyHandler(int num)
        {
            Console.WriteLine("축하합니다! {0}번째 고객 이벤트에 당첨되셨습니다.",num);
        }
        static void Main(string[] args)
        {
            // Market 클래스의 새로운 인스턴스 생성
            Market market = new Market();
            // 이벤트 처리기 등록
            market.CustomerEvent += new MyDelegate(MyHandler);

            for (int customerNo = 0; customerNo < 100; customerNo += 10)
                market.BuySomething(customerNo);
                

        }
    }
}

```
