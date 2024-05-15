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
