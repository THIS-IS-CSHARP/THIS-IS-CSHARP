# 비타민 퀴즈 10-1
### string[3, 5]인 배열은 길이가 얼마인 1차원 배열을 몇 개 갖고 있는 2차원 배열일까요?
```csharp
기반형식이 string이며 길이가 5인 1차원 배열을 원소로 3개 갖고 있는 2차원 배열
```
# 비타민 퀴즈 10-2
### 2차원 배열을 foreach 문에 넣고 각 요소의 데이터를 출력해보세요. 어떤 결과가 나옵니까?
```csharp
using System;

namespace Vitamin10_1
{
    class MainApp
    {
        static void Main(string[] args)
        {
            int[,] arr = new int[2, 3] { { 1, 2, 3 }, { 4, 5, 6 } };

            foreach (int i in arr)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```
```csharp
1
2
3
4
5
6

//foreach로 2차원 배열을 순회할 수 있다.
```
# 연습문제 10-1
### 다음 배열 선언 문장 중 올바르지 않은 것을 고르세요.

1. int[] array = new string[3]{"h", "Hello", "Halo"};
2. int[] array= new int[3]{1, 2, 3};
3. int[] array=new int[]{1, 2, 3};
4. int[] array = {1, 2, 3};

##### 정답 1번 데이터 형식이 일치하지 않음.

# 연습문제 10-2
### 2차원 배열을 이용하여 두 행렬의 곱을 계산하는 프로그램을 작성해보세요.
```csharp
namespace Ex10_2
{
    class MainApp
    {

        static void Main(string[] args)
        {
            static int[,] MultiplyMatrix(int[,] mat1, int[,] mat2)
            {
                int[,] result = new int[2, 2];

                for (int i = 0; i < 2; i++)
                {
                    for (int j = 0; j < 2; j++)
                    {
                        result[i, j] = mat1[i, 0] * mat2[0, j] + mat1[i, 1] * mat2[1, j];
                    }
                }

                return result;
            }

            static void printMatrix(int[,] matrix)
            {
                Console.WriteLine($"{matrix[0, 0]}, {matrix[0, 1]}");
                Console.WriteLine($"{matrix[1, 0]}, {matrix[1, 1]}");
            }

            int[,] arr1 = new int[2, 2] { { 3, 2 }, { 1, 4 } };
            int[,] arr2 = new int[2, 2] { { 9, 2 }, { 1, 7 } };
            int[,] arr3 = MultiplyMatrix(arr1, arr2);
            
            printMatrix(arr3);
        }
    }
}
```

### 결과
```csharp
29, 20
13, 30
```
# 연습문제 10-3
### 다음 코드의 출력 결과는 무엇일까요?
```csharp
Stack stack = new Stack();
stack.Push(1);
stack.Push(2);
stack.Push(3);
stack.Push(4);
stack.Push(5);

while (stack.Count > 0)
    Console.WriteLine(stack.Pop());
```
##### 정답
```csharp
5
4
3
2
1
```
늦게 Push된 데이터부터 Pop된다.

# 연습문제 10-4
### 다음 코드의 출력 결과는 무엇일까요?
```csharp
Queue que = new Queue();
que.Enqueue(1);
que.Enqueue(2);
que.Enqueue(3);
que.Enqueue(4);
que.Enqueue(5);

while (que.Count > 0)
    Console.WriteLine(que.Dequeue());
```
##### 정답
```csharp
1
2
3
4
5
```
들어간 순서대로 Dequeue 된다.

# 연습문제 10-5
### 다음과 같은 결과를 출력하도록 아래의 코드를 완성하세요.
```csharp
회사 : Microsoft
URL : www.microsoft.com
```
```csharp
Hashtable ht = new Hashtable();

/* 1) */ = "Microsoft";
ht["URL"] = /* 2) */;

Console.WriteLine("회사 : {0}", /* 3) */ );
Console.WriteLine("URL : {0}", /* 4) */ );
```
### 정답'
1. ht["회사"]
2. "www.microsoft.com"
3. ht["회사"]
4. ht["URL"]
