# 비타민 퀴즈 11-1 (436P)

### • 앞의 예제 프로그램에는 실행 결과가 없습니다. 여러분이 코드 곳곳에 출력문을 삽입해서 동작과정을 확인해보세요.

### • 인터페이스를 구현하는 클래스로 형식 매개변수를 제약하는 일반화 코드 추가 해보기.

```cs
using System;

namespace Vitamin11_1
{
    class StructArray<T> where T : struct
    {
        public T[] Array { get; set; }
        public StructArray(int size)
        {
            Array = new T[size];
        }
    }

    class RefArray<T> where T : class
    {
        public T[] Array { get; set; }
        public RefArray(int size)
        {
            Array = new T[size];
        }
    }

    interface IBase
    {
        void PrintClass();
    }

    class Base : IBase
    {
        public virtual void PrintClass()
        {
            Console.WriteLine("This is Base class");
        }
    }
    class Derived : Base
    {
        public override void PrintClass()
        {
            Console.WriteLine("This is Derived class");
        }
    }
    class BaseArray<U> where U : Base
    {
        public U[] Array { get; set; }
        public BaseArray(int size)
        {
            Array = new U[size];
        }

        public void CopyArray<T>(T[] Source) where T : U
        {
            Source.CopyTo(Array, 0);
        }
    }

    class MainApp
    {
        public static T CreateInstance<T>() where T : new()
        {
            return new T();
        }

        static void Main(string[] args)
        {
            // StructArray
            StructArray<int> a = new StructArray<int>(3);
            a.Array[0] = 0;
            a.Array[1] = 1;
            a.Array[2] = 2;
            Console.WriteLine($"a 타입 : {a.GetType().Name}");
            Console.WriteLine($"a.Array 타입 : {a.Array.GetType().Name}");
            int i = 0;
            foreach (var item in a.Array)
            {
                Console.WriteLine($"a.Array[{i}] = {item} ");
                i++;
            }

            // RefArray
            RefArray<StructArray<double>> b = new RefArray<StructArray<double>>(3);
            b.Array[0] = new StructArray<double>(5);
            b.Array[1] = new StructArray<double>(10);
            b.Array[2] = new StructArray<double>(1005);
            Console.WriteLine();
            Console.WriteLine($"b타입 : {b.GetType().Name}");
            Console.WriteLine($"b.Array 타입 : {b.Array.GetType().Name}");
            int j = 0;
            foreach (var structArray in b.Array)
            {
                Console.WriteLine($"b.Array[{j}]의 길이 : {structArray.Array.Length}");
                j++;
            }

            // BaseArray<Base>
            BaseArray<Base> c = new BaseArray<Base>(3);
            c.Array[0] = new Base();
            c.Array[1] = new Derived();
            c.Array[2] = CreateInstance<Base>();
            Console.WriteLine();
            Console.WriteLine($"c타입 : {c.GetType().Name}");
            Console.WriteLine($"c.Array 타입 : {c.Array.GetType().Name}");
            int k = 0;
            foreach (var item in c.Array)
            {
                Console.WriteLine($"c.Array[{k}]의 타입 : {item.GetType().Name}");
                k++;
            }

            // BaseArray<Derived>
            BaseArray<Derived> d = new BaseArray<Derived>(3);
            d.Array[0] = new Derived(); // Base 형식은 여기에 할당할 수 없다.
            d.Array[1] = CreateInstance<Derived>();
            d.Array[2] = CreateInstance<Derived>();
            Console.WriteLine();
            Console.WriteLine($"d타입 : {d.GetType().Name}");
            Console.WriteLine($"d.Array 타입 : {d.Array.GetType().Name}");
            int l = 0;
            foreach (var item in d.Array)
            {
                Console.WriteLine($"d.Array[{l}]의 타입 : {item.GetType().Name}");
                l++;
            }

            // CopyArray
            BaseArray<Derived> e = new BaseArray<Derived>(3);
            e.CopyArray<Derived>(d.Array);
            Console.WriteLine();
            Console.WriteLine($"e타입 : {e.GetType().Name}");
            Console.WriteLine($"e.Array 타입 : {e.Array.GetType().Name}");
            int m = 0;
            foreach (var item in e.Array)
            {
                Console.WriteLine($"e.Array[{m}]의 타입 : {item.GetType().Name}");
                m++;
            }
        }
    }
}
```

### 실행결과

```
a 타입 : StructArray`1
a.Array 타입 : Int32[]
a.Array[0] = 0
a.Array[1] = 1
a.Array[2] = 2

b타입 : RefArray`1
b.Array 타입 : StructArray`1[]
b.Array[0]의 길이 : 5
b.Array[1]의 길이 : 10
b.Array[2]의 길이 : 1005

c타입 : BaseArray`1
c.Array 타입 : Base[]
c.Array[0]의 타입 : Base
c.Array[1]의 타입 : Derived
c.Array[2]의 타입 : Base

d타입 : BaseArray`1
d.Array 타입 : Derived[]
d.Array[0]의 타입 : Derived
d.Array[1]의 타입 : Derived
d.Array[2]의 타입 : Derived

e타입 : BaseArray`1
e.Array 타입 : Derived[]
e.Array[0]의 타입 : Derived
e.Array[1]의 타입 : Derived
e.Array[2]의 타입 : Derived
```

### 인터페이스를 구현하는 클래스로 형식 매개 변수 제약

```cs
interface IBase
{
    void DisplayInfo();
}
```

1. `IBase` 인터페이스를 추가하고 `DisplayInfo` 메서드를 선언.

```cs
class Base: IBase
{
    public virtual void DisplayInfo()
    {
        Console.WriteLine("This is Base class");
    }
}
```

2. `Base` 클래스는 `IBase` 인터페이스를 구현(상속)하고 `DisplayInfo` 메서드를 정의.  
   `Derived` 클래스는 `Base` 클래스를 상속하고 `DisplayInfo` 메서드를 오버라이딩.

```cs
class BaseArray<U> where U : Base
{
    ...
}
```

3. 인터페이스 `IBase`를 구현하는 클래스 `Base`로 `BaseArray`의 형식 매개변수 `U`를 제약.

### d.Array에 Base 형식을 할당할 수 없는 이유

```cs
class BaseArray<U> where U : Base
{
    public U[] Array { get; set; }
    ...
}
```

`BaseArray<U>` 클래스의 타입 `U`는 `Base`의 인터페이스를 상속하는 클래스이도록 제한되어 있다.  
`BaseArray<Derived>`의 객체 d의 `Array`는 `Derived` 타입 객체만을 포함할 수 있다.  
`Derived`의 하위 타입이 아니라 상위 타입이기 때문에 `Base` 형식을 할당할 수 없다.

# 연습문제 11-1

### 다음 코드에서 문제를 찾고, 그 원인을 설명하세요.

```cs
Queue queue = new Queue();
queue.Enqueue(10);
queue.Enqueue("한글");
queue.Enqueue(3.14);

Queue<int> queue2 = new Queue<int>();
queue2.Enqueue(10);
queue2.Enqueue("한글");
queue2.Enqueue(3.14);
```

일반화 클래스의 객체인 queue2는 형식 매개변수에 입력한 형식(int) 외에는 입력을 허용하지 않는다. (437P)

# 연습문제 11-2

### 다음 코드에서 1️⃣에 들어갈 내용은 무엇입니까?

```cs
Dictionary</*1️⃣*/> dic = new Dictionary</*1️⃣*/>();

dic["하나"] = "one";
dic["둘"] = "two";
dic["셋"] = "three";
dic["y"] = "four";
dic["다섯"] = "five";

Console.WriteLine(dic["하나"]);
Console.WriteLine(dic["="]);
Console.WriteLine(dic["셋"]);
Console.WriteLine(dic["y"]);
Console.WriteLine(dic["다섯"]);
```

### 정답

키와 값 모두 문자열 타입이므로 string, string
