## 1. 다음 배열 선언 문장 중 올바르지 않은 것을 고르세요.

1️⃣ int[ ] array = new string[3]{”안녕”,”Hello”,”Halo”};

2️⃣ int[ ] array = new int[3]{1,2,3};

3️⃣ int[ ] array = new int[ ]{1,2,3};

4️⃣ int[ ] array = {1,2,3};

### 정답

1️⃣ int[ ] array = new string[3]{”안녕”,”Hello”,”Halo”};

int형 배열에 string배열을 값으로 넣어서 올바르지 않다.

## 2. 두 행렬의 곱은 다음과 같이 계산합니다.


![image](https://github.com/THIS-IS-CSHARP/THIS-IS-CSHARP/assets/118328426/7cc08cf6-5fa3-4b52-b0c9-44d01b6d2ea8)
![image](https://github.com/THIS-IS-CSHARP/THIS-IS-CSHARP/assets/118328426/c95cc8c2-2c5a-4903-b007-538b0c49339f)


## 다음 두 행렬 A와 B의 곱을 2차원 배열을 이용하여 계산하는 프로그램을 작성하세요.

$$
A = \begin{pmatrix}
3&2\\
1&4\\
\end{pmatrix}
B = \begin{pmatrix}
9&2\\
1&7\\
\end{pmatrix}
$$

### 정답

```csharp
using System;

class Program
{
    static void Main()
    {
        // 첫 번째 행렬
        int[,] matrix1 = {
            { 3, 2 },
            { 1, 4 }
        };

        // 두 번째 행렬
        int[,] matrix2 = {
            { 9, 2 },
            { 1, 7 }
        };

        // 행렬 곱셈 결과를 저장할 배열
        int[,] result = MultiplyMatrices(matrix1, matrix2);

        // 결과 출력
        PrintMatrix(result);
    }

    static int[,] MultiplyMatrices(int[,] matrix1, int[,] matrix2)
    {
        int rows1 = matrix1.GetLength(0);
        int cols1 = matrix1.GetLength(1);
        int rows2 = matrix2.GetLength(0);
        int cols2 = matrix2.GetLength(1);

        if (cols1 != rows2)
            throw new InvalidOperationException("행렬의 곱셈이 불가능합니다. 첫 번째 행렬의 열 수와 두 번째 행렬의 행 수가 같아야 합니다.");

        int[,] result = new int[rows1, cols2];

        for (int i = 0; i < rows1; i++)
        {   // 첫번째 행렬의 첫 행의 길이 만큼 반복
            for (int j = 0; j < cols2; j++)
            {   // 두번째 행렬의 열의 길이 만큼 반복
                for (int k = 0; k < cols1; k++)
                {   // 행렬 곱 연산
                    result[i, j] += matrix1[i, k] * matrix2[k, j];
                }
            }
        }

        return result;
    }

    static void PrintMatrix(int[,] matrix)
    {
        int rows = matrix.GetLength(0);
        int cols = matrix.GetLength(1);

        for (int i = 0; i < rows; i++)
        {
            for (int j = 0; j < cols; j++)
            {
                Console.Write(matrix[i, j] + "\t");
            }
            Console.WriteLine();
        }
    }
}
```

## 3. 다음 코드의 출력 결과는 무엇일까요?

```csharp
using System;
using System.Collections;

class Program
{
    static void Main()
    {
       Stack stack = new Stack();
       stack.Push(1);
       stack.Push(2);
       stack.Push(3);
       stack.Push(4);
       stack.Push(5);
       
       while (stack.Count > 0)
        Console.WriteLine(stack.Pop());
    }
}
```

### 정답

```
출력결과
5
4
3
2
1
```

## 4. 다음 코드의 출력 결과는 무엇일까요?

```csharp
using System;
using System.Collections;

class Program
{
    static void Main()
    {
       Queue que = new Queue();
       que.Enqueue(1);
       que.Enqueue(2);
       que.Enqueue(3);
       que.Enqueue(4);
       que.Enqueue(5);
       
       while (que.Count > 0)
        Console.WriteLine(que.Dequeue());
    }
}
```

### 정답

```
출력결과
1
2
3
4
5
```

## 5. 다음과 같은 결과를 출력하도록 아래의 코드를 완성하세요.

```
회사 : Mircosoft
URL : www.microsoft.com
```

```csharp
using System;
using System.Collections;

class Program
{
    static void Main()
    {
        Hashtable ht = new Hashtable();
        /* 1) */ = "Microsoft";
        ht["URL"] = /* 2) */
        
        Console.WriteLine("회사 : {0}", /* 3) */);
        Console.WriteLine("URL : {0}", /* 4) */);
    }
}
```

### 정답

```csharp
using System;
using System.Collections;

class Program
{
    static void Main()
    {
        Hashtable ht = new Hashtable();
       ht["회사"] = "Microsoft";
        ht["URL"] = "www.microsoft.com";
        
        Console.WriteLine("회사 : {0}", ht["회사"]);
        Console.WriteLine("URL : {0}", ht["URL"]);
    }
}
```
