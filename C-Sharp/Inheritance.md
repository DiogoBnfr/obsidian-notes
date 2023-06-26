Is a fundamental object-oriented programming concept that allows you to create new classes based on existing classes. It enables code reuse and promotes a hierarchical organization of classes.

Inheritance establishes an "is-a" relationship between classes, where a derived class (also known as a subclass or child class) inherits the properties, methods, and behavior of a base class (also known as a superclass or parent class). The derived class can then extend or specialize the functionality of the base class by adding new members or modifying the existing ones.

```csharp
class Vehicle  // base class (parent) 
{
  public string brand = "Ford";  // Vehicle field
  public void honk()             // Vehicle method 
  {                    
    Console.WriteLine("Tuut, tuut!");
  }
}

class Car : Vehicle  // derived class (child)
{
  public string modelName = "Mustang";  // Car field
}

class Program
{
  static void Main(string[] args)
  {
    // Create a myCar object
    Car myCar = new Car();

    // Call the honk() method (From the Vehicle class) on the myCar object
    myCar.honk();

    // Display the value of the brand field (from the Vehicle class) and the value of the modelName from the Car class
    Console.WriteLine(myCar.brand + " " + myCar.modelName);
  }
}
```

# Sealed Keyword
If you don't want other classes to inherit from a class, you can use the `sealed` keyword. By marking a class as **sealed**, you prevent it from being used as a base class for any other class. This effectively restricts inheritance and ensures that the sealed class cannot be further derived.

```csharp
class BaseClass
{
	// Class members
}
sealed class SealedClass : BaseClass
{
	// Class members
}
// Compilation error: Cannot derive from sealed type 'SealedClass'
class DerivedClass : SealedClass
{
	// Class members
}
```