## 연습문제01
```C#
namespace 연습문제01
{

    class NameCard
    {
        private int age;
        private string name;

        public int Age
        {
            get; set;
        }
        public string Name
        {
            get;set;
        }
    }
    internal class Program
    {

        static void Main(string[] args)
        {
            NameCard myCard = new NameCard();
            myCard.Age = 20;
            myCard.Name = "세현";

            Console.WriteLine("나이: {0}, 이름: {1}", myCard.Age, myCard.Name);
        }
    }
}

```

## 연습문제02
```C#
namespace 연습문제02
{
    internal class Program
    {
        static void Main(string[] args)
        {

            var nameCard = new { Name = "김세현", Age = 20 };
            Console.WriteLine("이름: {0}, 나이: {1}", nameCard.Name, nameCard.Age);

            var complex = new {Real=3, Imaginary = -12};
            Console.WriteLine("Real: {0}, Imaginary: {1}", complex.Real, complex.Imaginary);
            
        }
    }
}
```
