Is a short name for "enumeration". Is a distinct type that represents a set of named constants. It allows you to define a set of related values that can be assigned to a variable, parameter, or property. Enums are useful when you have a fixed set of values that a variable can take, providing clarity and type safety in your code.

```csharp
enum MyEnum
{
    Value1,
    Value2,
    Value3
}
```

In this specific example, we can refer to these values in two ways: using the index, which is an integer value that normally corresponds to the position of the value, or using the name directly.

For example, using the name:

```cs
MyEnum myVariable = MyEnum.Value2;
Console.WriteLine(myVariable); // Output: Value2
```

Example, using the index:

```cs
MyEnum myVariable = (MyEnum)1;
Console.WriteLine(myVariable); // Output: Value1
```

However, there may be cases where you want to retrieve the index or position of a specific enum value, such as the position of  `Value3`. In this case, you can use the same type casting logic as in the previous example. See:

```cs
MyEnum myVariable = (int)MyEnum.Value3;
Console.WriteLine(myVariable); // Output: 2
```

In this case, `myVariable` is assigned the enum value `Value3` using the index 2. By explicitly casting `myVariable` to `int`, you can retrieve the underlying integer value, which represents the position of `Value3`.