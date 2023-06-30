# Abstraction
In object-oriented programming (OOP), abstraction is a concept that allows you to create models or representations of real-world objects or concepts in a simplified and generalized manner. It involves capturing only the essential characteristics and behaviors of an object while hiding the unnecessary details.

Abstraction helps you manage complexity by focusing on what an object does rather than how it does it. It provides a way to define common interfaces, base classes, or abstract classes that represent a group of related objects with shared behaviors. These abstractions serve as blueprints or contracts that define the expected functionality without specifying the exact implementation.

# Abstract Keyword
The *abstract* keyword is used for classes and methods:

- **Abstract class:** is a restricted class that cannot be used to create objects (to access it, it must be inherited from another class).
  
- **Abstract method:** can only be used in an abstract class, and it does not have a body. The body is provided by the derived class (inherited from).

An abstract class can have both abstract and regular methods:

```cs
abstract class Animal 
{
  public abstract void animalSound();
  
  public void sleep() 
  {
    Console.WriteLine("Zzz");
  }
}
```

It's not possible to create a instance of the class *Animals*, because the *abstract*  modifier implies that are missing components or incomplete implementation in the class.

```cs
// Abstract class
abstract class Animal
{
  // Abstract method (does not have a body)
  public abstract void animalSound();
  // Regular method
  public void sleep()
  {
    Console.WriteLine("Zzz");
  }
}

// Derived class (inherit from Animal)
class Pig : Animal
{
  public override void animalSound()
  {
    // The body of animalSound() is provided here
    Console.WriteLine("The pig says: wee wee");
  }
}

class Program
{
  static void Main(string[] args)
  {
    Pig myPig = new Pig(); // Create a Pig object
    myPig.animalSound();  // Call the abstract method
    myPig.sleep();  // Call the regular method
  }
}
```