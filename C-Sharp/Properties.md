Properties provide a way to encapsulate the access to class fields or variables. They are used to define the external interface for accessing and modifying the values of private fields in an object.

Properties combine the features of fields and methods, allowing you to control how values are read from or written to the underlying fields. They provide a level of abstraction that helps maintain encapsulation and enables you to add additional logic or validation when accessing or modifying the values.

```csharp
class Person
{
  private string name; // field

  public string Name   // property
  {
    get { return name; }   // get method
    set { name = value; }  // set method
  }
}
```

**Explaining the example:**
1. The *Name* property is associated with the *name* field. It is a good practice to use the same name for both the property and the private field, but with an uppercase first letter.
2. The *get* method returns the value of the variable *name*.
3. The *set* method assigns a *value* to the *name* variable. The *value* keyword represents the value we assign to the property.

```csharp
Person person = new Person();
person.Name = "John"; // set the value using the setter
string name = person.Name; // get the value using the getter
```


