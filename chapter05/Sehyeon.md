## 연습문제
### 01.
```C#
using System;
class StarWrite {
  static void Main() {
      for(int i = 1; i <= 5; i++)
      {
          for(int j=1; j<=i; ++j)
          {
              Console.Write("*");
          }
        Console.WriteLine();         
      }
  }
}
```

### 02.
```C#
using System;
class StarWrite {
  static void Main() {
      for(int i = 5; i >= 1; i--)
      {
          for(int j=i; j>=1; j--)
          {
              Console.Write("*");
          }
        Console.WriteLine();
      }
  }
}
```

### 03.

while 루프
```C#
using System;

class StarWrite {
    static void Main() {
        int i = 1;
        while (i <= 5) {
            int j = 1;
            while (j <= i) {
                Console.Write("*");
                j++;
            }
            Console.WriteLine();
            i++;
        }
    }
}

```
do-while 루프
```C#
using System;

class StarWrite {
    static void Main() {
        int i = 1;
        do {
            int j = 1;
            do {
                Console.Write("*");
                j++;
            } while (j <= i);
            Console.WriteLine();
            i++;
        } while (i <= 5);
    }
}
```
while문 - 반대로 별표표기
```c#
using System;

class StarWrite {
    static void Main() {
        int i = 5;
        while (i >= 1) { 
            int j = 1;
            while (j <= i) {
                Console.Write("* ");
                j++;
            }
            Console.WriteLine();
            i--;
        }
    }
}
```
