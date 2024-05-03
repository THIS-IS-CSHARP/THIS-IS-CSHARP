### 비타민 3-1 (052P)

코드: CS0266
설명: 암시적으로 'long' 형식을 'sbyte' 형식으로 변환할 수 없습니다. 명시적 변환이 있습니다. 캐스트가 있는지 확인하세요.

### 비타민 3-2 (058P)
2147483647
-2147483648

### 비타민 3-3 (065P)
char a = "안";
char b = '안녕';
string d = '안';
string e = '안녕';

### 연습문제 3-1 (115P)
```csharp
namespace RectArea
{
    class MainApp
    {
        public static void Main()
        {
            Console.WriteLine("사각형의 너비를 입력하세요.");
            string width = Console.ReadLine();

            Console.WriteLine("사각형의 높이를 입력하세요.");
            string height = Console.ReadLine();

            int area = int.Parse(width) * int.Parse(height);

            Console.WriteLine("사각형의 넓이는 : " + area);
        }
    }
}
```

### 연습문제 3-2
```csharp
int a = 7.3; // 타입을 float로 바꾸고, 값에 접미사F를 붙여주거나 혹은 double 타입으로 바꿔줘야 한다.
float b = 3.14; //값에 접미사 F 필요
char d = "abc"; // string 타입 데이터
string e = '한'; // char 타입 데이터
```

### 연습문제 3-3
값 형식:
변수가 값을 저장하고 있는 스택 메모리의 주소를 갖고 있음

참조 형식:
변수가 ‘값을 저장하고 있는 힙메모리의 주소’를 갖고 있는 스택 메모리의 주소를 갖고 있음

### 연습문제 3-4
박싱:
스택 메모리에 있던 값 형식 데이터를 힙메모리에 보내 객체 형식에 담는 것

언박싱:
힙 메모리의 객체에 담긴 값을 스택 메모리의 값 형식 데이터로 꺼내는 것

### 연습문제 3-5
컴파일러가 타입을 추론하여 var a는 int 타입으로, var b는 string 타입으로 지정해준다.
