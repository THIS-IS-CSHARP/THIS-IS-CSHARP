## 연습문제
### 01.
증가 연산자는 변수의 앞에 사용하는지 뒤에 사용하는지에 따라 연산 방식이 달라진다.
- i++;: 후위 증가 연산자로, 현재 문장이 종료된 후에 i의 값을 1씩 증가, 다시 말해 문장에서 i를 사용한 후 i의 값을 증가 시킨다.
- ++i;: 전위 증가 연산자로, 현재 문장을 실행하기 전에 i의 값을 1씩 증가

### 02.
```C#
i = i + 1;  //1
i++;  //2
++i;  //3 
i+=1;  //4
```
1번은 변수 i에 1을 더한 값을 i에 다시 대입한다. <br>
2번은 후위 증가연산자로 현재 문장이 종료된후에 i의 값을 1씩 증가<br>
3번은 전위 증가연산자로 현재 문장을 실행하기 전에 i의 값을 1씩 증가<br>
4번은 1번도 동일,+=할당 연산자를 사용하여 i에 1을 더한값을 i에 할당한다.<br>

### 03.
int a = 8 >> 1;
int b = a >> 2;

8을 2진수로 표현하면 1000이다. 이때  >> 1 연산을 수행하면 모든 비트가 오른쪽으로 한칸씩 이동하게 되어 0100이 된다.
8로 우측으로 1개를 잃어버렸을때, 10진수로 4라는 값이 출력됨 <br>
따라서  int a = 8 >> 1;은 변수에 4를 할당한다.
![image](https://github.com/THIS-IS-CSHARP/THIS-IS-CSHARP/assets/107483199/876d9db6-17e4-487b-9a14-44857c294757)


4을 2진수로 표현하면 0100이다. >> 2 연산을 수행하면 0001이 된다. 10진수로 1이라는 값이 출력됨<br>
따라서 b의 값은 1이 된다.
![image](https://github.com/THIS-IS-CSHARP/THIS-IS-CSHARP/assets/107483199/5ede5a72-7261-4e8e-93f3-620faf7a8d0c)

### 04.
- 0x는 해당 숫자가 16진수임을 나타내는 접두사이다.
- 뒤에 나오는 숫자들이 16진수입니다. 예를 들어, 0xF0에서 F는 16진수로 15를 의미하고, 0x0F에서 F도 16진수로 15를 의미한다.
- 두 값을 OR 연산하면 결과는 16진수로 0xFF가 된다. 이를 2진수로 변환하면 11111111된다.
- 이진수 인자를 모두 더하면 a의 값은 255가 된다.

### 05.
 a == 0 이 거짓이므로, b = "ABC"이다.

