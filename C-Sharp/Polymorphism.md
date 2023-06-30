# Polymorphism
Is a core concept in object-oriented programming that allows objects of different classes to be treated as objects of a common base class. It enables you to write code that can work with objects of multiple types, providing flexibility, extensibility, and code reusability.

At its core, polymorphism allows you to perform operations on objects without knowing their specific types but rather relying on their shared interface or base class. This concept is often summarized as "one interface, multiple implementations".

<iframe width="100%" height="400px" src="https://www.youtube.com/embed/tIWm3I_Zu7I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

There are two main forms of polymorphism: compile-time polymorphism (also known as static polymorphism or method overloading) and runtime polymorphism (also known as dynamic polymorphism or method overriding).

![[Polymorphism.png]]

# Compile-Time Polymorphism 
In compile-time polymorphism (a.k.a. Method Overloading), multiple methods with the same name but different parameters are defined in a class. The appropriate method to execute is determined by the arguments provided at compile-time. The compiler resolves which method to call based on the number, types, and order of the parameters.

```cs
class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }

    public double Add(double a, double b)
    {
        return a + b;
    }
}
```

In the above example, the **Add()** method is overloaded with two different parameter types: *int* and *double*. The appropriate method is selected based on the argument types during compilation.

# Runtime Polymorphism
In runtime polymorphism (a.k.a. Method Overriding), a derived class overrides a method defined in its base class. The overridden method in the derived class provides its own implementation, while still adhering to the same method signature (name, return type, and parameters). The decision of which method to call is made dynamically at runtime, based on the actual type of the object.

```cs
class Animal
{
    public virtual void MakeSound()
    {
        Console.WriteLine("Animal makes a sound.");
    }
}

class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Dog barks.");
    }
}

class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Cat meows.");
    }
}
```

In this example, the *Animal* class defines a virtual method called **MakeSound()**. The *Dog* and *Cat* classes inherit from *Animal* and override the **MakeSound()** method with their own implementations. At runtime, when calling the **MakeSound()** method on a *Dog* or *Cat* object, the appropriate overridden method is invoked based on the actual type of the object.