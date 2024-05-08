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
