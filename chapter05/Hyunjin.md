# 연습문제

# 연습문제01
# 다음과 같은 결과를 출력하는 프로그램을 for문을 이용하여 작성하세요. 규칙은 첫번째 줄에 별 1개 두번째 줄에 별2개 세번째 줄에 별 3개... 이런식으로 별 5개가 찍힐때까지 반복합니다.
# (힌트: for문안에 for문을 넣으세요).

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace fiveLineStars
{
    class Program
    {
        static void Main(string[] args)
        {
            for(int i =0; i < 5; i++) {
              
                for(int j = 0; j < i; j++)
                {
                    Console.Write("*");
                }
                Console.WriteLine();
            }
        }
    }
}
```


# 연습문제02
# 다음과 같은 결과를 출력하는 프로그램을 for문을 이용하여 작성하세요. 규칙은 첫번째 줄에 별 1개 두번째 줄에 별2개 세번째 줄에 별 3개... 이런식으로 별 5개가 찍힐때까지 반복합니다.
# (힌트: for문안에 for문을 넣으세요).
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace descendingOrderStars
{
    class Program
    {
        static void Main(string[] args)
        {
            for (int i = 5; i >= 1; i--)
            {
                for (int j = 0; j < i; j++)
                {
                    Console.Write("*");
                }
                Console.WriteLine();
            }
        }
    }
}

```
# 연습문제03
# 1번과 2번을 for문 대신 while문과 do문으로 바꿔서 각각 작성하세요

##01번의 while, do while문
```
while문문
namespace fiveLineStars
{
    class Program
    {
        static void Main(string[] args)
        {
            int i = 0;
            while (i < 5)
            {
                int j = 0;
                while (j < i)
                {
                    Console.Write("*");
                    j++;
                }
                Console.WriteLine();
                i++;
            }
        }
    }
}

```
```
do while문
namespace fiveLineStars
{
    class Program
    {
        static void Main(string[] args)
        {
            int i = 0;
            do
            {
                int j = 0;
                do
                {
                    Console.Write("*");
                    j++;
                } while (j < i);
                Console.WriteLine();
                i++;
            } while (i < 5);
        }
    }
}
```
##02번의 while, do while문

```
while문

namespace descendingOrderStars
{
    class Program
    {
        static void Main(string[] args)
        {
            int i = 5;
            while (i >= 1)
            {
                int j = 0;
                while (j < i)
                {
                    Console.Write("*");
                    j++;
                }
                Console.WriteLine();
                i--;
            }
        }
    }
}
```
```
do while문

namespace descendingOrderStars
{
    class Program
    {
        static void Main(string[] args)
        {
            int i = 5;
            do
            {
                int j = 0;
                do
                {
                    Console.Write("*");
                    j++;
                } while (j < i);
                Console.WriteLine();
                i--;
            } while (i >= 1);
        }
    }
}


```
# 연습문제04
# 4. 다음과 같이 사용자로부터 입력받은 횟수만큼 별을 반복 출력하는 프로그램을 작성하세요. 단, 입력받은 수가 0보다 작거나 같을 경우 ‘0보다 같거나 작은 숫자는 사용할 수 없습니다.’라는 메시지를 띄우고 프로그램을 종료합니다.

```
반복 횟수를 입력하세요. : -10
0보다 같거나 작은 수는 사용할 수 없습니다.

반복 횟수를 입력하세요 : 5
*
**
***
****
***** 
```

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace creatingStars
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Write("반복 횟수를 입력하세요: ");
            int repeatCount = int.Parse(Console.ReadLine());

            if (repeatCount <= 0)
            {
                Console.WriteLine("0보다 같거나 작은 수는 사용할 수 없습니다.");
            }
            else
            {
                for (int i = 1; i <= repeatCount; i++)
                {
                    for (int j = 1; j <= i; j++)
                    {
                        Console.Write("*");
                    }
                    Console.WriteLine();
                }
            }
        }
    }
}


```
