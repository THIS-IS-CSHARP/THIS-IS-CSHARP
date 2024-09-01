## 01. 다음 코드에서 문제를 찾고, 원인 설명

```C#

static void Main(string[] args)
{
    Queue queue = new Queue();
    queue.Enqueue(10);
    queue.Enqueue("한글");
    queue.Enqueue(3.14);

    Queue<int> queue2 = new Queue<int>();
    queue2.Enqueue(10);
    //queue2.Enqueue('한글');
    //queue2.Enqueue(3.14);
}

```

#### Queue ququ: 타입 안정성 부족
- 비제네릭 클래스로 사용될때, 안정성이 보장되지않아 어떤 타입도 넣을수 있음
- 이 경우 런타임 시 잘못된 타입을 사용하는 오류갑 발생할수 있어, 형식 매개변수 <T> 를 사용하는 것이 좋다.

#### queue2: int 타입만 허용
- string, double 타입을 추가하려고해 컴파일 시 오류 발생

## 02. 다음 코드에서 들어갈 내용

```C#
static void Main(string[] args)
{
    Dictionary<string, string> dic = new Dictionary<string, string>();
    dic["하나"] = "one";
    dic["둘"] = "two";

    Console.WriteLine(dic["하나"]);
    Console.WriteLine(dic["둘"]);

}

```
- Hashtable의 일반화 버전으로 dic["하나"] = "one"; Key와 Value 가 string으로 되어 있으므로 형식 매개변수는 string 
