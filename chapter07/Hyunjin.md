# 1. 클래스와 객체, 인스턴스는 서로 어떤 점이 다른가요?

# 답변
클래스는 필드와 메서드로 이루어져 있으며, 객체의의 속성과 기능을 정의 한다
인스턴스는 클래스를 가지고 객체를 생성한 결과이다

# 2. 다음 코드에서 오류를 찾고, 오류의 원인을 설명하세요.

```
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
# 답변
B d = new A(); A클래스는 B클래스의 부모 클래스 이기때문에 부모 클래스의 인스턴스를 자식 클래스의 타입으로 할당 불가능하다

# 3. this 키워드와 base 키워드에 대해 설명하세요.

# 답변
this 현재 자신을 가리키고(참조하고), base는 부모 클래스를 가르킨다

# 4. 구조체에 대한 다음 설명 중 틀린 것을 모두 찾으세요.
1. struct 키워드를 이용하여 선언한다.
2. 복사할 때 얕은 복사가 이루어진다.
3. 참조 형식이다.
4. 메소드를 가질 수 있다.

# 답변
2. 복사할 때 얕은 복사가 이루어진다.
3. 참조 형식이다.

