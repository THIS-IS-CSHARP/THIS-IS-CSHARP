# 비타민 퀴즈 16-1

### 앞의 예제 프로그램에서 테스트해보지 않은 (Type 형식) 메소드를 테스트하는 예제 프로그램을 만들어보세요.

```cs
using System.Reflection;

namespace Vitamin16_1
{
    delegate void MyDelegate(int a);

    class Market
    {
        public event MyDelegate CustomerEvent;
    }

    class Array_Generic<T>
    {
        private T[] array;
        public T GetElement(int index)
        {
            return array[index];
        }
    }

    class MainApp
    {
        static void PrintConstructors(Type type)
        {
            Console.WriteLine("-------- Constructors --------");
            ConstructorInfo[] constructors = type.GetConstructors();
            foreach (var constructor in constructors)
            {
                Console.WriteLine(constructor);
            }
        }

        static void PrintEvents(Type type)
        {
            Console.WriteLine("-------- Events --------");
            EventInfo[] events = type.GetEvents();
            foreach (var eventInfo in events)
            {
                Console.WriteLine(eventInfo);
            }
        }

        static void PrintGenericArguments(Type type)
        {
            Console.WriteLine("-------- GenericArguments --------");
            Type[] genericArguments = type.GetGenericArguments();
            foreach (var args in genericArguments)
            {
                Console.WriteLine(args);
            }
        }

        static void PrintMembers(Type type)
        {
            Console.WriteLine("-------- Members --------");
            MemberInfo[] members = type.GetMembers();
            foreach (var member in members)
            {
                Console.WriteLine(member);
            }
        }

        static void PrintNestedTypes(Type type)
        {
            Console.WriteLine("-------- NestedTypes --------");
            Type[] nestedTypes = type.GetNestedTypes();
            foreach (var nestedType in nestedTypes)
            {
                Console.WriteLine(nestedType);
            }
        }

        static void Main(string[] args)
        {
            string str = "Hello World";
            Type typeStr = str.GetType();
            PrintConstructors(typeStr);

            Market market = new Market();
            Type typeEvent = market.GetType();
            PrintEvents(typeEvent);

            Array_Generic<int> intarr = new Array_Generic<int>();
            Type typeGenArg = intarr.GetType();
            PrintGenericArguments(typeGenArg);

            double num = 1;
            Type typeInt = num.GetType();
            PrintMembers(typeInt);

            Dictionary<string, string> dict = new Dictionary<string, string>();
            dict["하나"] = "one";
            Type typeNested = dict.GetType();
            PrintNestedTypes(typeNested);
        }
    }
}
```

### 실행결과

```
-------- Constructors --------
Void .ctor(Char[])
Void .ctor(Char[], Int32, Int32)
Void .ctor(Char*)
Void .ctor(Char*, Int32, Int32)
Void .ctor(SByte*)
Void .ctor(SByte*, Int32, Int32)
Void .ctor(SByte*, Int32, Int32, System.Text.Encoding)
Void .ctor(Char, Int32)
Void .ctor(System.ReadOnlySpan`1[System.Char])
-------- Events --------
Vitamin16_1.MyDelegate CustomerEvent
-------- GenericArguments --------
System.Int32
-------- Members --------
Boolean IsFinite(Double)
Boolean IsInfinity(Double)
Boolean IsNaN(Double)
Boolean IsNegative(Double)
Boolean IsNegativeInfinity(Double)
Boolean IsNormal(Double)
Boolean IsPositiveInfinity(Double)
Boolean IsSubnormal(Double)
Int32 CompareTo(System.Object)
Int32 CompareTo(Double)
Boolean Equals(System.Object)
...
System.Type GetType()
Double MinValue
Double MaxValue
Double Epsilon
Double NegativeInfinity
Double PositiveInfinity
Double NaN
Double NegativeZero
Double E
Double Pi
Double Tau
-------- NestedTypes --------
System.Collections.Generic.Dictionary`2+Enumerator[TKey,TValue]
System.Collections.Generic.Dictionary`2+KeyCollection[TKey,TValue]
System.Collections.Generic.Dictionary`2+ValueCollection[TKey,TValue]
```

# 연습문제 16-1

### 다음 코드 중에서 올바로 동작하지 않는 것을 고르세요.

```
1. Type t = myObject.GetType();
2. Type t = typeof("int");
3. Type t =Type.GetType(int);
4. Type t =Type.GetType("System.Int32");
```

### 정답

3. Type t =Type.GetType(int);

Type.GetType() 메소드는 형식의 전체 이름, 즉 네임스페이스를 포함한 형식이름을 인수로 받는다. (572P)

# 연습문제 16-2

### 애트리뷰트와 주석의 차이는 무엇 입니까 ?

둘다 데이터(코드)를 설명하는 데이터, 메타데이터이지만  
애트리뷰트는 클래스나 메서드 등에 메타데이터를 추가하여 컴파일러나 런타임에서 특정 동작을 제어하거나 정보를 제공하는 데 사용됩니다.  
반면, 주석은 코드의 이해를 돕기 위해 개발자가 추가하는 설명으로, 컴파일러에 의해 무시되며 코드 실행에 영향을 미치지 않습니다.
