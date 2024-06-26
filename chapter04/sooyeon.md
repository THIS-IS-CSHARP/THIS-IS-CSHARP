## 연습문제

## 1. i++ 와 ++i 의 차이점은 무엇인가요?

### 정답

i++ 는 후위 증가 연산자로 해당 문장의 실행이 끝난 후에 변수의 값이 1 증가하고, ++i 는 전위 증가 연산자로 변수의 값을 1 증가한 뒤에 해당 문장이 실행된다.

<br>

## 2.  다음 보기 중에서 그 결과가 다른 것을 찾으세요(변수 i를 초기화해서 각 보기를 실행해보면 그 결과가 나옵니다. 고민을 좀 해본 후에 답을 확인해보세요.)

1️⃣ i = i + 1;

2️⃣ i++;

3️⃣ ++i;

4️⃣ i += 1;

### 정답

2️⃣번 - 후위 증가 연산자로 해당문장이 실행되고 1이 증가한다.

```csharp
using System;
class Result {
  static void Main() {
    int i = 1;
    Console.WriteLine("{0}",i=i+1); // 출력 : 2
    
    i = 1;
    Console.WriteLine("{0}",i++); // 출력 : 1
    
    i = 1;
    Console.WriteLine("{0}",++i); // 출력 : 2
    
    i = 1;
    Console.WriteLine("{0}",i+=1); // 출력 : 2
    
  }
}
```

<br>


## 3. 다음 코드에서 a와 b는 각각 얼마일까요?

```
int a = 8 >> 1;
int b = a >> 2;
```

### 정답

a = 4, b = 1

오른쪽 시프트 연산은 왼쪽값을 2로 오른쪽 값의 횟수만큼 나눈다.

따라서 a는 8 / 2 로 4가 되고, b는 4 / 2 /2 로 1이 된다.

 
<br>



## 4. 다음 코드에서 a는 얼마일까요?

```
int a = 0xF0 | 0x0F;
```

### 정답

a는 255

16진수의 비트 연산을 해야하는데, 0xF0 은 10진수로 15*16 = 240, 0x0F는 10진수로 15이다. 10진수를 2진수로 변경하면 0xF0 은 11110000  0x0F는 1111이 된다. 이 두 수를 논리합 연산하면 아래와 같다.

11110000

00001111

---

11111111

따라서 a는 255가 된다.

<br>


## 5. 다음 코드에서 b는 어떤 값을 가질까요?

```
int a = 10;
string b = a == 0 ? "가나다" : "ABC";
```

### 정답

b는 “ABC”

조건 연산자를 사용하면 조건이 참일 경우 : 앞의 값을, 거짓일 경우 : 뒤의 값을 반환한다.
