# 연습문제
## 1. 클래스와 객체, 인스턴스는 서로 어떤 점이 다른가요?

### 정답

클래스는 객체가 가지게 될 속성과 기능을 정의한다. 인스터스는 클래스로 생성한 객체를 의미한다.

## 2. 다음 코드에서 오류를 찾고, 오류의 원인을 설명하세요.

```csharp
class A
{
}

class B:A
{
}

class C
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

### 정답

B d = new A(); 에서 오류가 발생한다. A클래스는 B클래스의 부모 클래스로 B클래스 형식으로는 선언이 불가능하다.

## 3. this 키워드와 base 키워드에 대해 설명하세요.

### 정답

this는 해당 객체 자신을 의미하고,  base는 부모 클래스를 의미한다.

## 4. 구조체에 대한 다음 설명 중 틀린 것을 모두 찾으세요.

1️⃣ struct 키워드를 이용하여 선언한다.

2️⃣ 복사할 때 얕은 복사가 이루어진다.

3️⃣ 참조 형식이다.

4️⃣ 메소드를 가질 수 있다.

### 정답

2️⃣ - 구조체에서는 깊은 복사가 일어난다.

3️⃣ - 구조체는 값 형식으로 스택 메모리에 할당된다. 

## 5. 다음 코드를 컴파일 및 실행이 가능하도록 수정하세요.

```csharp
using System;

namespace ReadonlyMethod
{   
    struct ACSetting
    {
        public double currentInCelsius;
        public double target;
        
        public readonly double GetFahrenheit()
        {
            target = currentInCelsius * 1.8 + 32;
            return target;
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

### 정답

```csharp
using System;

namespace ReadonlyMethod
{   
    struct ACSetting
    {
        public double currentInCelsius;
        public double target;
        
        // readonly 제한자 제거
        public double GetFahrenheit()
        {
            // target 필드를 직접 수정하지 않고 계산 결과를 반환
            return currentInCelsius * 1.8 + 32;
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
           Console.WriteLine($"{acs.target}"); // target 필드의 초기값 출력
       }
    }
}
```

## 6. 다형성은 무엇이며, 오버라이딩과 무슨 관계가 있는지 설명하세요.

### 정답

다형성은 객체가 여러 형태를 가질 수 있음을 의미한다. 부모 클래스에서 정의한 메서드를 자식클래스에서 재정의 하는 오버라이딩을 통해 부모 클래스의 타입으로 선언한 객체가 여러 형태의 메서드를 사용할 수 있게 되는 다형성을 가질 수 있게 된다.

## 7. 다음 코드에서 switch 식을 제거하고, switch 문으로 동일한 기능을 작성하세요.

```csharp
private static double GetDiscountRate(object client)
{
  return client switch
  {
      ("학생",int n) when n < 18 => 0.2, //학생 & 18세 미만
      ("학생",_) => 0.1, //학생 & 18세 이상
      ("일반",int n) when n < 18 => 0.1, //일반 & 18세 미만
      ("일반",_) => 0.5, //일반 & 18세 미만
      _ => 0,
  };
}
```

### 정답

```csharp

  private static double GetDiscountRate(object client)
{
  string clientType;
  int clientAge;

  if (client is (string, int))
  {
      (clientType, clientAge) = (string, int)client;
  }
  else
  {
      return 0;
  }

  switch (clientType)
  {
      case "학생":
          if (clientAge < 18)
          {
              return 0.2;
          }
          else
          {
              return 0.1;
          }
      case "일반":
          if (clientAge < 18)
          {
              return 0.1;
          }
          else
          {
              return 0.5;
          }
      default:
          return 0;
  }
}
```
