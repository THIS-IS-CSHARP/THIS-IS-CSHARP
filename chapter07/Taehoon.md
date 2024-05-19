# 비타민 퀴즈 7-1 (237P)
### 책상 위에 놓여 있는 아무 물건이나 골라서 속성과 기능을 뽑아보세요.
```
물건: 지갑

속성
재질, 크기, 색상

기능
지폐 보관, 카드 보관, 신분증 보관
```

# 비타민 퀴즈 7-2 (295P)
### string 클래스에 문자열 매개변수를 입력받아 기존의 문자열 뒤에 붙여 반환하는 Append () 확장 메소드를 추가해보세요. 이 확장 메소드의 사용 예는 다음 같습니다.

```csharp
string hello = "Hello";
Console.WriteLine(hello.Append(", World!")); // "Hello, World!"
```

### 비타민 퀴즈 7-2 정답
```csharp
namespace Vitamin7_2
{
    public static class vita
    {
        public static string Append(this string string1, string string2)
        {
            string result = string1 + string2;
            return result;
        }
    }

}
```

# 연습문제 7-1
### 클래스와 객체, 인스턴스는 서로 어떤 차이점이 있나요?
```
클래스는 객체를 만들기 위한 설계도이며 데이터 형식이다.

객체는 클래스로부터 생성자에 의해서 만들어진다.

객체를 인스턴스(instance: 실체)라고 부르기도 한다.

객체는 실체가 있어 메모리를 차지한다.
```

# 연습문제 7-2
### 다음 코드에서 오류를 찾고, 오류의 원인을 설명하세요.
```csharp
Class A
{
}

Class B : A
{
}

Class C
{
	public static void Main()
	{
		A a = new A();
		B b = new B();
		A c = new B();
		B d = new A();
	}
}
```

B d = new A();

부모 클래스의 객체 new A()를 자식 클래스B의 변수d에 할당하는 것은 허용되지 않는다.

(”개는 포유류다” 의 역인 “포유류는 개다”가 거짓인 것처럼..).

(272P 파생 클래스의 인스턴스는 기반 클래스의 인스턴스로도 사용할 수 있다.)

# 연습문제 7-3
### this 키워드와 base 키워드에 대해 설명하세요.
```
this는 객체 내부에서 자신의 필드나 메소드에 접근할 때 this 키워드를 사용한다. (255P)

base는 자식 클래스에서 부모 클래스에 접근 할 때 사용한다. (267P)
```

# 연습문제 7-4
### 구조체에 대한 다음 설명 중 틀린 것을 모두 찾으세요.

##### 1.struct 키워드를 이용하여 선언한다.

##### 2.복사할 때 얕은 복사가 이루어진다.

##### 3.참조형식이다.

##### 4.메소드를 가질 수 있다.

```
값 형식이기 때문에, 깊은 복사가 이루어진다. 2, 3번
```

# 연습문제 7-5
### 다음 코드를 컴파일 및 실행이 가능하도록 수정하세요.
```csharp
using System;

namespace Ex7_5
{

    struct ACSetting 
    {
        public double currentInCelsius; //현재 온도
        public double target; //희망 온도

        public readonly double GetFahrenheit()
        {
            target = currentInCelsius * 1.8 + 32; //화씨(F) 계산 결과를 target에 저장
            return target // target 반환
        }
    }
    class MainApp
    {
        static void Main(string[] args)
        {
            ACSetting acs;
            acs.currentInCelsius = 25;
            acs.target = 25;

            Console.WriteLine($"{acs.GetFahrenheit()}");
            Console.WriteLine($"{acs.target}");
        }
    }
}

```

### 연습문제 7-5 정답
```csharp
using System;

namespace Ex7_5
{

    struct ACSetting 
    {
        public double currentInCelsius; //현재 온도
        public double target; //희망 온도

        public readonly double GetFahrenheit()
        {
            return currentInCelsius * 1.8 + 32; //화씨(F) 계산 결과를 target에 저장
            
        }
    }
    class MainApp
    {
        static void Main(string[] args)
        {
            ACSetting acs;
            acs.currentInCelsius = 25;
            acs.target = 25;

            Console.WriteLine($"{acs.GetFahrenheit()}");
            Console.WriteLine($"{acs.target}");
        }
    }
}

```

# 연습문제 7-6
### 다형성은 무엇이며, 오버라이딩과 무슨 관계가 있는지 설명하세요.
```
다형성은 객체가 여러가지 형태를 가질 수 있음을 의미한다. 
부모 클래스의 메서드를 자식 클래스가 오버라이딩, 재정의 하는 것을 통해 다형성을 실현 하는 것이다. (276P)
```

# 연습문제 7-7

```csharp
private static double GetDiscountRate(object client)
{
    return client switch
    {
        ("학생", int n) when n < 18 => 0.2 // 학생 & 18세 미만
        ("학생", _) => 0.1 // 학생 & 18세 이상
        ("일반", int n) when n < 18 => 0.1 // 일반 & 18세 미만
        ("일반", _) => 0.05 // 일반 & 18세 이상
        _ => 0,
    }
}
```
### 다음 코드에서 switch 식을 제거하고 switch 문으로 동일한 기능을 작성하세요.
```csharp
class Program
{
    private static double GetDiscountRate(object client)
    {
        double discountRate = 0;
        
        switch (client)
        {
            case ("학생", int n) when n < 18:
                discountRate = 0.2;
                break;
            case ("학생", _):
                discountRate = 0.1;
                break;
            case ("일반", int n) when n < 18:
                discountRate = 0.1;
                break;
            case ("일반", _):
                discountRate = 0.05;
                break;
            default:
                discountRate = 0;
                break;
        }
        return discountRate;
    }
}
```

https://cafe.naver.com/thisiscsharp/757  
switch 문에 case로 튜플을 사용할 수 있다.