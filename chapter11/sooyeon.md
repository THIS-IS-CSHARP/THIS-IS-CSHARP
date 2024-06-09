# 연습문제

## 1. 다음 코드에서 문제를 찾고, 그 원인을 설명하세요.

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

class HelloWorld {
  static void Main() {
    Queue queue = new Queue();
    queue.Enqueue(10);
    queue.Enqueue("한글");
    queue.Enqueue(3.14);
    
    while (queue.Count > 0)
        Console.WriteLine(queue.Dequeue());
  
    Queue<int> queue2 = new Queue<int>();
    queue2.Enqueue(10);
    queue2.Enqueue("한글");
    queue2.Enqueue(3.14);
    
    while (queue2.Count > 0)
        Console.WriteLine(queue2.Dequeue());
  }
}
```

### 정답

queue2에 string 형식과, duoble 형식을  Enqueue  하면 문제가 발생한다. queue2의 형식 매개변수는 int 형식으로 queue2는 int 형식 외에는 입력을 허용하지 않기 때문이다.

## 2. 다음 코드에서 1️⃣에 들어갈 내용은 무엇입니까?

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

class HelloWorld {
  static void Main() {
    Dictionary</* 1️⃣ */> dic = new Dictionary</* 1️⃣ */>();
    
    dic["하나"] = "one";
    dic["둘"] = "two";
    dic["셋"] = "three";
    dic["넷"] = "four";
    dic["다섯"] = "five";
    
    Console.WriteLine(dic["하나"]);
    Console.WriteLine(dic["둘"]);
    Console.WriteLine(dic["셋"]);
    Console.WriteLine(dic["넷"]);
    Console.WriteLine(dic["다섯"]);
  }
}
```

### 정답

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

class HelloWorld {
  static void Main() {
    Dictionary<string, string> dic = new Dictionary<string, string>();
    
    dic["하나"] = "one";
    dic["둘"] = "two";
    dic["셋"] = "three";
    dic["넷"] = "four";
    dic["다섯"] = "five";
    
    Console.WriteLine(dic["하나"]);
    Console.WriteLine(dic["둘"]);
    Console.WriteLine(dic["셋"]);
    Console.WriteLine(dic["넷"]);
    Console.WriteLine(dic["다섯"]);
  }
}
```
