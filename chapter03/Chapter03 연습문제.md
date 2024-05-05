# chapter03 연습문제

## 1. 다음과 같이 사용자로부터 사각형의 너비와 높이를 입력받아 넓이를 계산하는 프로그램을 완성하세요. 다음 코드 중 주석 부분을 바꾸면 됩니다.
```
사각형의 너비를 입력하세요.
30
사각형의 높이를 입력하세요.
40
사각형의 넓이는 : 1200
```
```C#
using System;
namespace RectArea
{
    class MainApp{
        public static void Main(){
            Console.WriteLine("사각형의 너비를 입렵하세요");
            string width = Console.ReadLine();
            
            Console.WriteLine("사각형의 높이를 입렵하세요");
            string height = Console.ReadLine();
            
            // 이곳에 사각형의 넓이를 계산하고
            // 출력하는 루틴을 추가하세요.
        }   
    }
}
```

### 정답
```C#
using System;
namespace RectArea
{
    class MainApp{
        public static void Main(){
            Console.WriteLine("사각형의 너비를 입렵하세요");
            string width = Console.ReadLine();
            
            Console.WriteLine("사각형의 높이를 입렵하세요");
            string height = Console.ReadLine();
            
            int rectArea = int.Parse(width) * int.Parse(height); // 사각형의 넓이 계산
            Console.WriteLine("사각형의 넓이 : {0}",rectArea); // 값 출력
        }   
    }
}
```

<br>

## 2. 다음 코드에서 잘못된 부분을 찾고, 그 이유를 설명하세요.
```
int a = 7.3;
float b = 3.14;
double c = a*b;
char d = "abc";
string e = '한';
```

### 정답
 a, b, d, e 가 잘못되었다.
> `int a = 7.3;` : 실수형 값이 할당되어 float이나 double 형식을 사용해야한다. <br>
> `float b = 3.14;` : float 형식은 접미사 f나 F를 붙여서 float 타입을 명시해야한다. <br>
> `char d = "abc";` : "abc"는 문자열로 string 형식을 사용해야한다. <br>
> `string e = '한';` :  '한'은 단일 문자로 char 형식을 사용해야한다.

<br>

## 3. 값 형식과 참조 형식의 차이는 무엇인가요?
### 정답
값 형식은 변수가 값을 담는 데이터 형식을 말하고, 참조 형식은 변수가 값 대신 값이 있는 곳의 위치를 담는 데이터 형식을 말한다.
> 값형식 int, float, char, bool, enum <br>
> 참조형식은 스택과 힙메모리를 모두 사용한다. 이때 값은 힙에 저장되고, 값이 저장된 힙메모리의 주소는 스택에 저장된다. <br>
> 참조 형식으로는 string, object 가 있고 null은 참조형식 변수의 기본값이다. <br>

<br>

## 4. 박싱과 언박싱을 설명하세요.
### 정답
박싱(Boxing): 박싱은 스택메모리에 있던 값 형식 데이터를 참조 형식으로 변환하는 과정이다. 값 형식을 박싱하면 값이 담긴 새로운 객체가 힙(heap)에 생성되고, 
당 객체에 대한 참조(주소값)가 반환된다.
```
int i = 10; // 값 형식
object obj = i; // 박싱
```
<br>

언박싱(Unboxing): 언박싱은 박싱의 반대 과정으로, 힙 메모리의 박싱된 객체에서 값을 추출하는 것을 의미한다.
```
object obj = 10; // 박싱된 정수
int i = (int)obj; // 언박싱
```

#### 1️⃣ 박싱은 값형식을 object형식으로 변환하는 프로세스
![image](https://github.com/THIS-IS-CSHARP/THIS-IS-CSHARP/assets/107483199/da45e218-2cd7-4619-a7d5-a87f75e926ac)

#### 2️⃣ 언박싱은 object 형식에서 값형식으로 변환하는 프로세스
![image](https://github.com/THIS-IS-CSHARP/THIS-IS-CSHARP/assets/107483199/f8d9b1ff-15e6-4f17-a8c4-a05ccd3d546e)

<br>

## 5. 다음 코드를 컴파일한 후의 a와 b는 각각 어떤 데이터 형식이겠습니까?
```
var a = 2020;
var b = "double";
```

### 정답
var를 사용해서 변수를 선언하면 컴파일러가 자동으로 해당 변수의 형식을 지정해 준다. 따라서 a는 int형, b는 string형이 된다.
