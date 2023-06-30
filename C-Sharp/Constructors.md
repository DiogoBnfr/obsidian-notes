Is a special method or function within a class that is used to initialize and create objects of that class. When an object is instantiated or created from a class, the constructor is called automatically.

The constructor has the same name as the class and is typically used to set initial values for the object's attributes or to perform any necessary setup tasks. It helps ensure that the object being created is in a valid and usable state.

# Constructor Overloading
Constructor overloading is the act of providing more than one way to initialize an object.  So, the instance don't compulsorily need to have all the fields filled to be considered valid or usable.

```csharp
public class Person
{
    private string name;
    private int age;
    private string address;

    // Constructor with name parameter
    public Person(string name)
    {
        this.name = name;
    }

    // Constructor with name and age parameters
    public Person(string name, int age)
    {
        this.name = name;
        this.age = age;
    }

    // Constructor with name, age, and address parameters
    public Person(string name, int age, string address)
    {
        this.name = name;
        this.age = age;
        this.address = address;
    }

    // Rest of the class...
}
```

# Constructor Chaining
Also known as constructor delegation, is a mechanism in object-oriented programming where one constructor calls another constructor within the same class. This allows for reusing common initialization logic and avoids code duplication.

In constructor chaining, constructors are linked together, and each constructor can invoke another constructor using the *this* keyword. By chaining constructors, you can provide different levels of initialization while avoiding redundant code.

```csharp
public class Person
{
    private string name;
    private int age;
    private string address;

    // Default constructor
    public Person() : this("Unknown", 0, "Unknown")
    {
        // Delegating to the parameterized constructor with default values
    }

    // Parameterized constructor
    public Person(string name, int age, string address)
    {
        this.name = name;
        this.age = age;
        this.address = address;
    }

    // Rest of the class...
}
```