## 01 배열 선언 문장 중 올바르지 않은 것 고르기
- [x] int[] array = new string[3]{"안녕","Hello", "Halo"};
- [ ] int[] array = new int[3]{1,2,3};
- [ ] int[] array = new int[]{1,2,3};
- [ ] int[] array = {1,2,3};


## 02 두 행렬 A와 B의 2차원 배열을 이용하여 계산하는 프로그램 작성하기
```C#
internal class Program
{
    static void Main(string[] args)
    {
        int[,] A = { { 3, 2 }, { 1, 4 } };
        int[,] B = { { 9, 2 }, { 1, 7 } };

        int[,] C = new int[2, 2];

        for(int i=0; i<2; i++)
        {
            for(int j=0; j<2; j++)
            {
                C[i, j] = 0; // 초기화
                for (int k = 0; k < 2; k++)
                {
                    C[i, j] += A[i, k] * B[k, j];
                }
            }
        }

        // 결과 행렬 출력
        Console.WriteLine("행렬 A * B =");
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
```

## 03 스택 코드 출력 결과

```C#
internal class Program
{
    static void Main(string[] args)
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

// 출력: 5,4,3,2,1
```

## 04 큐 코드 출력 결과

```C#
internal class Program
{
    static void Main(string[] args)
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

// 출력: 1,2,3,4,5
```

## 05 해시테이블 코드 출력결과

```C#
namespace UsingHashtable
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Hashtable ht = new Hashtable();
            ht["회사"] = "Microsoft";
            ht["URL"] = "www.microsoft.com";

            Console.WriteLine("회사: {0}", ht["회사"]);
            Console.WriteLine("URL: {0}",ht["URL"]);
        }
    }
}

```
