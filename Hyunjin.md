# 연습문제

## 1. 다음 배열 선언 문장 중 올바르지 않은 것을 고르세요.
int[] array = new string[3]{"h", "Hello", "Halo"};
int[] array= new int[3]{1, 2, 3};
int[] array=new int[]{1, 2, 3};
int[] array = {1, 2, 3};

## 답변: 1
데이터 타입이 같지 않다

## 2. 2차원 배열을 이용하여 두 행렬의 곱을 계산하는 프로그램을 작성해보세요.

```
using System;

namespace MatrixMultiplication
{
    class MainApp
    {
        static void Main(string[] args)
        {
            int[,] A = { { 3, 2 }, { 1, 4 } };
            int[,] B = { { 9, 2 }, { 1, 7 } };
            int[,] C = new int[2, 2];

            // 행렬 곱셈
            for (int i = 0; i < 2; i++)
            {
                for (int j = 0; j < 2; j++)
                {
                    C[i, j] = 0;
                    for (int k = 0; k < 2; k++)
                    {
                        C[i, j] += A[i, k] * B[k, j];
                    }
                }
            }

            // 결과 출력
            Console.WriteLine("행렬 A와 B의 곱:");
            for (int i = 0; i < 2; i++)
            {
                for (int j = 0; j < 2; j++)
                {
                    Console.Write(C[i, j] + " ");
                }
                Console.WriteLine();
            }
        }
    }
}
```

## 3. 다음 코드의 출력 결과는 무엇일까요?

```
Stack stack = new Stack();
stack.Push(1);
stack.Push(2);
stack.Push(3);
stack.Push(4);
stack.Push(5);

while (stack.Count > 0)
    Console.WriteLine(stack.Pop());
```


## 답변:
5
4
3
2
1

## 4. 다음 코드의 출력 결과는 무엇일까요?

```
Queue que = new Queue();
que.Enqueue(1);
que.Enqueue(2);
que.Enqueue(3);
que.Enqueue(4);
que.Enqueue(5);

while (que.Count > 0)
    Console.WriteLine(que.Dequeue());
```

## 답변:
1
2
3
4
5

## 5. 다음과 같은 결과를 출력하도록 아래의 코드를 완성하세요.

회사 : Microsoft
URL : www.microsoft.com

```
Hashtable ht = new Hashtable();

/* 1) */ = "Microsoft";
ht["URL"] = /* 2) */;

Console.WriteLine("회사 : {0}", /* 3) */ );
Console.WriteLine("URL : {0}", /* 4) */ );
```

## 답변
1) ht["회사"]
2) " www.microsoft.com"
3) ht["회사"]
4) ht["URL"]

