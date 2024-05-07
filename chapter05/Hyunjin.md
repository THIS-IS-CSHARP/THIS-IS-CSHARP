#연습문제

###연습문제1
####다음과 같은 결과를 출력하는 프로그램을 for문을 이용하여 작성하세요. 규칙은 첫번째 줄에 별 1개 두번째 줄에 별2개 세번째 줄에 별 3개... 이런식으로 별 5개가 찍힐때까지 반복합니다.
####(힌트: for문안에 for문을 넣으세요).

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
