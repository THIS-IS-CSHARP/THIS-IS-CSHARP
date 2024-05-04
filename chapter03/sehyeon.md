## 연습문제
### 01. 사용자로부터 사각형의 너비와 높이를 입력받고 넓이를 계산하는 프로그램 완성하기
```c#
using System; 

class Program {
  
  public static void Main (string[] args) {

    Console.WriteLine("사각형의 너비를 입력하세요.");
    string width = Console.ReadLine();

    Console.WriteLine("사각형의 높이를 입력하세요.");
    string height = Console.ReadLine();

    int result = int.Parse(width) * int.Parse(height);  // 사각형의 넓이 계산
    Console.WriteLine("사각형의 넓이는 : "+ result);  // 값 출력
    
  }
}

```

- `Console.ReadLine();` : 사용자로 부터 텍스트를 입력 받아서 값을 저장한다.

### 02. 다음코드에서 잘못된 부분을 찾고, 그 이유 설명하기
```C#
int a = 7.3;
float b = 3.14;
double c = a*b;
char d = "abc";
string e = '한';
```
타입에 맞는 값을 할당해야하는데 a, b, d, e 가 잘못된 코드이다. 
변수 c는 a, b가 double 타입으로 선언 되었다면 두수를 곱한 값이 c에 할당된다.

- `double a = 7.3;` : 실수형 값이 할당됨
- `float b = 3.14f;` : 부동 소수점 리터럴은 double 타입을 사용해야한다. 또는 값 뒤에 f나 F를 붙여서 float 타입을 명시해야한다.
- `stirng d = "abc";` : 문자열 형식으로 string 타입
- `char e = '한';` : 문자형식으로 char 타입을 사용해야한다.

### 03. 값 형식과 참조 형식의 차이는 무엇인가? 
**값 형식**은 스택에 **참조 형식**은 힙에 값이 저장된다. 
- 값형식 int, float, char, bool, enum
- 참조형식은 스택과 힙메모리를 모두 사용한다. 이때 값은 힙에 저장되고, 값의 주소는 스택에 저장된다. 참조 형식으로는 string, object 가 있고 null은 참조형식 변수의 기본값이다.

### 04. 박싱과 언박싱에 대해서 설명하기

- 박싱은 값을 내부에 래핑하고 힙 메모리에 저장한다.
- 값형삭(object)의 값이 직접 스택에 저장되고, 박싱하면 래핑해서 힙 메모리에 값을 저장한다.
- 박싱은 암시적이고, 언박싱은 명시적이다.
  ```C#
  object a = 20; // 암시적
  object b = (int)a;  // 명시적
  ```


#### 1️⃣ 박싱은 값형식을 object형식으로 변환하는 프로세스
![image](https://github.com/THIS-IS-CSHARP/THIS-IS-CSHARP/assets/107483199/da45e218-2cd7-4619-a7d5-a87f75e926ac)

#### 2️⃣ 언박싱은 object 형식에서 값형식으로 변환하는 프로세스
![image](https://github.com/THIS-IS-CSHARP/THIS-IS-CSHARP/assets/107483199/f8d9b1ff-15e6-4f17-a8c4-a05ccd3d546e)


### 05. 다음 코드를 컴파일 한후 a와 b는 각각 어떤 데이터 형식일까?
```C#
var a = 2020;
var b = "double";
```
a는 int타입으로 정수형이고, b는 string 타입으로 문자열 형식이다.
