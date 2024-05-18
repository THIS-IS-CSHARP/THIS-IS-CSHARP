#1.다음 코드에서 Square() 메소드를 구현해 프로그램을 완성하세요. Square() 함수는 매개변수를 제곱하여 반환합니다. 프로그램의 실행 예제는 다음과 같습니다.

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace SquareMethod
{
  class Program
    {
        
        static double Square(double arg)
        {
            return arg * arg;
        }
        static void Main(string[] args)
        {
            Console.WriteLine("수를 입력하세요: ");
            string input = Console.ReadLine();
            double arg = Convert.ToDouble(input);

            Console.WriteLine("결과 : {0}", Square(arg));
        }
    }
}


```
#2.다음 코드에서 Mean() 메소드를 실행한 후의 mean은 얼마의 값을 가질까요? 3이라고요? 아닙니다. 0입니다. 자, 문제 나갑니다. 
#mean이 0을 갖게 되는 원인은 무엇이며, 이를 바로잡으려면 다음 코드에서 어떤 부분을 고쳐야 할까요?

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Mean
{
    class Program
    {
        public static void Main()
        {
            double mean = 0;
            Mean(1, 2, 3, 4, 5, mean);
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
#수정
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Mean
{
    class Program
    {
        public static void Main()
        {
            double mean = 0;
            Mean(1, 2, 3, 4, 5, ref mean);
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
##설명
메소드에서 mean의 파라미터가 double 이므로 메소드 호출시 타입 파라미터는 지역변수로 불러오므로 Mean 메소드에서 타입을 변경해도 적용되지 않으므로 참조타입으로 전달 한다. 이때 ref를 쓰면 된다

