# SOLID em C#

* Exemplos seguindo os princípios SOLID em C#.
* https://www.freecodecamp.org/news/what-are-the-solid-principles-in-csharp/

## S - Single Responsibility Principle

```C#
public class User
{
 public string Username { get; set; }
 public string Email { get; set; }
}
```
```C#
public class EmailSender
{
 public void SendEmail(string message, string recipient)
 {
   // Email sending logic
   Console.WriteLine($"Sending email to {recipient}: {message}");
 }
}
```
```C#
public class UserService
{
 public void RegisterUser(User user)
 {
   // Register user logic...

   EmailSender emailSender = new EmailSender();
   emailSender.SendEmail("Welcome to our platform!", user.Email);
 }
}
```

## O - Open Closed Principle

```C#
public abstract class Shape
{
 public abstract double CalculateArea();
}
```

```C#
public class Circle : Shape
{
 public double Radius { get; set; }

 public override double CalculateArea()
 {
   return Math.PI * Math.Pow(Radius, 2);
 }
}
```

```C#
public class Rectangle : Shape
{
 public double Length { get; set; }
 public double Width { get; set; }

 public override double CalculateArea()
 {
   return Length * Width;
 }
}
```

## L - Liskov Substitution Principle

```C#
public abstract class Shape
{
 public abstract double Area { get; }
}
```

```C#
public class Rectangle : Shape
{
 public double Width { get; set; }

 public double Height { get; set; }

 public override double Area => Width * Height;
}
```

```C#
public class Square : Shape
{
 private double sideLength;

 public double SideLength
 {
   get => sideLength;
   set
   {
     sideLength = value;
   }
 }

 public override double Area => sideLength * sideLength;
}
```

```C#
// Program.cs

Shape rectangle = new Rectangle { Width = 5, Height = 4 };

Console.WriteLine($"Area of the rectangle: {rectangle.Area}");

Shape square = new Square { SideLength = 5 };

Console.WriteLine($"Area of the square: {square.Area}")
```

## I - Interface Segregation Principle

```C#
public interface IShape2D
{
 double Area();
}
```

```C#
public interface IShape3D
{
 double Area();
 double Volume();
}
```

```C#
public class Circle : IShape2D
{
 public double Radius { get; set; }

 public double Area()
 {
   return Math.PI * Math.Pow(Radius, 2);
 }
}
```

```C#
public class Sphere : IShape3D
{
 public double Radius { get; set; }

 public double Area()
 {
   return 4 * Math.PI * Math.Pow(Radius, 2);
 }

 public double Volume()
 {
   return (4.0 / 3.0) * Math.PI * Math.Pow(Radius, 3);
 }
}
```

## D - Dependency Inversion Principle

```C#
public interface IEngine
{
 void Start();
}
```

```C#
public class Engine : IEngine
{
 public void Start()
 {
   System.Console.WriteLine("Engine started.");
 }
}
```

```C#
public class Car
{
 private IEngine engine;

 public Car(IEngine engine)
 {
   this.engine = engine;
 }

 public void StartCar()
 {
   engine.Start();
   System.Console.WriteLine("Car started.");
 }
}
```

```C#
var engine = new Engine(); // concrete implementation to be "injected" into the car

var car = new Car(engine);

car.StartCar();
```