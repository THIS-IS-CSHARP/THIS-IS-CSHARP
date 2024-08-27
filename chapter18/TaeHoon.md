# 비타민 퀴즈 18-1 (639P)
### SeqNRand 예제 프로그램에서 생성한 파일을 읽는 프로그램을 만들어보세요. 방금 만든 SeqNRand 예제 프로그램은 파일의 0, 1, 2, 3번지에 데이터를 기록하고 다시 8번지에 데이터를 기록했습니다. FileStream 클래스의 ReadByte() 메소드와 Seek() 메소드를 이용해서 SeqNRand 프로그램에서 생성한 파일의 내용을 읽어 출력하는 프로그램을 작성해보세요.

```cs
using System;
using System.IO;

namespace Vitamin18_1
{
    class MainApp
    {
        static void Main(string[] args)
        {
            Stream outStream = new FileStream("a.dat", FileMode.Create);
            outStream.WriteByte(0x01);
            outStream.WriteByte(0x02);
            outStream.WriteByte(0x03);
            outStream.Seek(5, SeekOrigin.Current);
            outStream.WriteByte(0x04);
            outStream.Close();

            Stream inStream = new FileStream("a.dat", FileMode.Open);
            Console.WriteLine((Byte)inStream.ReadByte());
            Console.WriteLine((Byte)inStream.ReadByte());
            Console.WriteLine((Byte)inStream.ReadByte());
            inStream.Seek(5, SeekOrigin.Current);
            Console.WriteLine((Byte)inStream.ReadByte());
            inStream.Close();
        }
    }
}
```
### 실행결과
```
1
2
3
4
```

# 비타민 퀴즈 18-2 (646P)
### BinaryWriter는 문자열을 저장할 때 첫 번째 바이트를 문자열의 길이로 사용합니다. 그렇다면 BinaryWriter의 Write() 메소드는 255자를 넘어서는 문자를 기록할 수 없는 것일까요? 프로그램을 작성해서 실험해보세요.
```cs
using System;
using System.IO;

namespace Vitamin18_2
{
    class MainApp
    {
        static void Main(string[] args)
        {
            string length256 = new string('A', 256);

            using (BinaryWriter bw = 
                new BinaryWriter(
                    new FileStream("a.dat", FileMode.Create)))
            {
                bw.Write(length256);
            }

            using (BinaryReader br =
                new BinaryReader(
                    new FileStream("a.dat", FileMode.Open)))
            {
                //Console.WriteLine($"{br.ReadString()}");
                Console.WriteLine(br.ReadByte());
                Console.WriteLine(br.ReadByte());
                Console.WriteLine(br.ReadByte());
                Console.WriteLine(br.ReadByte());
            }
                
        }
    }
}
```
### 실행결과
```
128
2
65
65
```
BinaryWriter와 BinaryReader를 사용하여 문자열을 기록하고 읽을 때,  
문자열의 길이는 7비트 가변 길이 정수 (Variable Length Quantity, VLQ) 방식으로 저장.  
이 방식에서는 문자열의 길이를 효율적으로 표현하기 위해 한 개 이상의 바이트를 사용.  

7비트 VLQ 방식으로 문자열 길이가 256일 때  
1. 문자열 길이를 2진수로 변환 / 256₁₀ = 100000000₂ (9비트)  
2. 2진수 숫자를 7자리(7비트)씩 쪼갬 / 10,0000000  
3. 추가 바이트가 있음을 나타내기 위해 뒤에 있는 7비트의 제일 앞자리에 1을 붙임 / 10,1000000  
4. 첫 번째 바이트는 마지막 7비트다. 1000000₂ = 128₁₀, 10₂ = 2₁₀  
5. (65는 A의 아스키 코드)  

# 비타민 퀴즈 18-3 (654P)
###
```cs
using System;
using System.IO;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace Serialization
{
    class NameCard
    {
        public string Name { get; set; }
        [JsonIgnore]
        public string Phone { get; set; }
        public int Age { get; set; }
    }

    class Mainapp
    {
        static void Main(string[] args)
        {
            var fileName = "a.json";

            using (Stream ws = new FileStream(fileName, FileMode.Create))
            {
                NameCard nc = new NameCard()
                {
                    Name = "박상현",
                    Phone = "010-123-4567",
                    Age = 33
                };

                string jsonString = JsonSerializer.Serialize<NameCard>(nc);
                byte[] jsonBytes = System.Text.Encoding.UTF8.GetBytes(jsonString);
                ws.Write(jsonBytes, 0, jsonBytes.Length);
            }

            using (Stream rs = new FileStream(fileName, FileMode.Open))
            {
                byte[] jsonBytes = new byte[rs.Length];
                rs.Read(jsonBytes, 0, jsonBytes.Length);
                string jsonString = System.Text.Encoding.UTF8.GetString(jsonBytes);

                NameCard nc2 = JsonSerializer.Deserialize<NameCard>(jsonString);

                Console.WriteLine($"Name: {nc2.Name}");
                Console.WriteLine($"Phone: {nc2.Phone}");
                Console.WriteLine($"Age: {nc2.Age}");
            }
        }
    }
}
```

### 실행 결과
```
Name: 박상현
Phone:
Age: 33
```