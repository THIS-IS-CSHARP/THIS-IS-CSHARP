## VITAMIN QUIZ 7-1
객체 노트북의 속성으로는 종류, 색상, 무게가 있다.
기능으로는 전원켜기, 충전하기가 있다.
```C#
class Notebook
{
    public string Name;
    public string Color;
    public int weight; 
    
    public void turnOn()
    {
      Console.WriteLine("컴퓨터 전원을 켜다.");
    }
    public void chargeUp()
    {
      Console.WriteLine("충전중...");
    }
}
```

## VITAMIN QUIZ 7-2
```C#
using System;

public static class StringExtensions
{
    public static string Append(this string originalString, string appendString)
    {
      return originalString + appendString;
    }
}

class Program {
  public static void Main (string[] args) {
    string original = "Hello";
    string appended = original.Append(", World!");
    Console.WriteLine(appended); // 출력: Hello, World!
  }
}
```

# 연습문제
## 01. 클래스와 객체, 인스턴스는 서로 어떤 차이가 있는가?
클래스는 데이터와 메서드로 이뤄어져 있고, 클래스를 만드는 이유는 현실에 있는 사물들을 구조화하기 위함이다.
즉, 클래스는 객체를 만들수 있는 틀이다. 어떤 특정 클래스에 생성된 객체와 인스턴스는 동일한 의미이다.

### 클래스(Class)
클래스는 객체를 생성하기 위한 청사진 또는 설계도이다.클래스는 데이터(속성)와 이를 조작하는 함수(메서드)로 구성된다. 클래스는 현실 세계의 사물이나 개념을 추상화
하여 프로그래밍 언어로 표현한 것이다. 예를 들어 자동차를 표현하기 위한 클래스는 Car라는 이름을 가질수 있고, 속성으로서는 색상, 모델, 연도 등이 있고, 메서드로는 주행, 정지 등이 있을수 있다.

### 객체(Object)
객체는 클래스를 기반으로 생성된 실체이다. 클래스가 설계도라면, 객체는 그 설계도를 바탕으로 만들어진 구체적인 사물이다. 객체는 클래스의 인스턴스이고, 클래스에서 정의된 속성과 메서드를 실제로 가지게된다. 예를 들어, Car클래스에서 생성된 myCar라는 객체는 빨간색 2023년형 스포츠가 일수 있다.

### 인스턴스(Instance)
인스턴스는 특정 클래스의 객체를 지칭하는 용어이다. 즉, 객체와 인스턴스는 사실상 같은 개념이지만, 문맥에 따라 용어가 달라질수 있다. 
객체는 일반적인 의미로 사용되고, 인스턴스는 특정 클래스의 구현체를 강조할 때 사용된다. 예를 들어 myCar는 Car클래스의 인스턴스이다.

### 요약
- 클래스: 객체를 만들기한 설계도로 데이터와 메서드로 구성되었다.
- 객체: 클래스의 설계도를 바탕으로 생성된 구체적인 실체이다.
- 인스턴스: 특정 클래스에서 생성된 객체를 의미하고, 객체와 동일한 의미로 사용된다.
