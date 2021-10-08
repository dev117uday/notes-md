# OOPS in C\#

## Partial Classes and Methods

In C\#, you can split the implementation of a class, a struct, a method, or an interface in multiple `.cs` files using the `partial` [keyword](https://www.tutorialsteacher.com/csharp/csharp-keywords). The compiler will combine all the implementation from multiple `.cs` files when the program is compiled.

Consider the following `EmployeeProps.cs` and `EmployeeMethods.cs` files that contain the `Employee` 

```csharp
public partial class Employee
{
    public int EmpId { get; set; }
    public string Name { get; set; }
}
```

`EmployeeMethods.cs`

```csharp
public partial class Employee
{
    //constructor
    public Employee(int id, string name){
        this.EmpId = id;
        this.Name = name;
    }

    public void DisplayEmpInfo() {
        Console.WriteLine(this.EmpId + " " this.Name);
    }
}
```

* All the partial class definitions must be in the same assembly and namespace.
* All the parts must have the same accessibility like public or private, etc.
* If any part is declared abstract, sealed or base type then the whole class is declared of the same type.
* Different parts can have different base types and so the final class will inherit all the base types.
* The Partial modifier can only appear immediately before the keywords class, struct, or interface.
* Nested partial types are allowed.

Partial classes or structs can contain a method that split into two separate `.cs` files of the partial class or struct. One of the two `.cs` files must contain a signature of the method, and other file can contain an optional implementation of the partial method. Both declaration and implementation of a method must have the `partial` keyword.

* Partial methods must use the `partial` keyword and must return `void`
* Partial methods can have `in` or `ref` but not `out` parameters.
* Partial methods are implicitly private methods, so cannot be virtual.
* Partial methods can be static methods.
* Partial methods can be generic.

## Indexer

An indexer is a special type of property that allows a class or a structure to be accessed like an array for its internal collection. C\# allows us to define custom indexers, generic indexers, and also overload indexers.

```csharp
class StringDataStore
{
    private string[] strArr = new string[10]; 
    // internal data storage

    public string this[int index]
    {
        get
        {
            if (index < 0 || index >= strArr.Length)
                throw new 
          IndexOutOfRangeException("Index out of range");

                return strArr[index];
        }

        set
        {
            if (index < 0 ||  index >= strArr.Length)
                throw new 
          IndexOutOfRangeException("Index out of range");

            strArr[index] = value;
        }
    }
}
```

## Generics

C\# allows you to define generic classes, interfaces, abstract classes, fields, methods, static methods, properties, events, delegates, and operators using the [type parameter](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/generics/generic-type-parameters) and without the specific data type. A type parameter is a placeholder for a particular type specified when creating an instance of the generic type.

```csharp
class DataStore<T>
{
    public T Data { get; set; }
}

class KeyValuePair<TKey, TValue>
{
    public TKey Key { get; set; }
    public TValue Value { get; set; }
}
```

* A generic class increases the reusability. The more type parameters mean more reusable it becomes. However, too much generalization makes code difficult to understand and maintain.
* A generic class can be a base class to other generic or non-generic classes or abstract classes.
* A generic class can be derived from other generic or non-generic interfaces, classes, or abstract classes.

### Generic Methods

```csharp
class DataStore<T>
{
    private T[] _data = new T[10];

    public void AddOrUpdate(int index, T item)
    {
        if(index >= 0 && index < 10)
            _data[index] = item;
    }

    public T GetData(int index)
    {
        if(index >= 0 && index < 10)
            return _data[index];
        else 
            return default(T);
    }
}
```

## Generic Constraints

C\# allows you to use constraints to restrict client code to specify certain types while instantiating generic types. It will give a compile-time error if you try to instantiate a generic type using a type that is not allowed by the specified constraints.

```csharp
GenericTypeName<T> where T  : contraint1, constraint2

class DataStore<T> where T : class
{
    public T Data { get; set; }
}
```

### T : struct

The following example demonstrates the `struct` constraint that restricts type argument to be non-nullable value type only.

```csharp
class DataStore<T> where T : struct
{
    public T Data { get; set; }
}

// valid
DataStore<int> store = new DataStore<int>(); 

// valid
DataStore<char> store = new DataStore<char>(); 

// valid
DataStore<MyStruct> store = new DataStore<MyStruct>(); 

// compile-time error 
DataStore<string> store = new DataStore<string>();
```

## Exception Handling

| Exception Class | Description |
| :--- | :--- |
| [ArgumentException](https://docs.microsoft.com/en-us/dotnet/api/system.argumentexception?view=netframework-4.8) | Raised when a non-null argument that is passed to a method is invalid. |
| [ArgumentNullException](https://docs.microsoft.com/en-us/dotnet/api/system.argumentnullexception?view=netframework-4.8) | Raised when null argument is passed to a method. |
| [ArgumentOutOfRangeException](https://docs.microsoft.com/en-us/dotnet/api/system.argumentoutofrangeexception?view=netframework-4.8) | Raised when the value of an argument is outside the range of valid values. |
| [DivideByZeroException](https://docs.microsoft.com/en-us/dotnet/api/system.dividebyzeroexception?view=netframework-4.8) | Raised when an integer value is divide by zero. |
| [FileNotFoundException](https://docs.microsoft.com/en-us/dotnet/api/system.io.filenotfoundexception?view=netframework-4.8) | Raised when a physical file does not exist at the specified location. |
| [FormatException](https://docs.microsoft.com/en-us/dotnet/api/system.formatexception?view=netframework-4.8) | Raised when a value is not in an appropriate format to be converted from a string by a conversion method such as Parse. |
| [IndexOutOfRangeException](https://docs.microsoft.com/en-us/dotnet/api/system.indexoutofrangeexception?view=netframework-4.8) | Raised when an array index is outside the lower or upper bounds of an array or collection. |
| [InvalidOperationException](https://docs.microsoft.com/en-us/dotnet/api/system.invalidoperationexception?view=netframework-4.8) | Raised when a method call is invalid in an object's current state. |
| [KeyNotFoundException](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.keynotfoundexception?view=netframework-4.8) | Raised when the specified key for accessing a member in a collection is not exists. |
| [NotSupportedException](https://docs.microsoft.com/en-us/dotnet/api/system.notsupportedexception?view=netframework-4.8) | Raised when a method or operation is not supported. |
| [NullReferenceException](https://docs.microsoft.com/en-us/dotnet/api/system.nullreferenceexception?view=netframework-4.8) | Raised when program access members of null object. |
| [OverflowException](https://docs.microsoft.com/en-us/dotnet/api/system.overflowexception?view=netframework-4.8) | Raised when an arithmetic, casting, or conversion operation results in an overflow. |
| [OutOfMemoryException](https://docs.microsoft.com/en-us/dotnet/api/system.outofmemoryexception?view=netframework-4.8) | Raised when a program does not get enough memory to execute the code. |
| [StackOverflowException](https://docs.microsoft.com/en-us/dotnet/api/system.stackoverflowexception?view=netframework-4.8) | Raised when a stack in memory overflows. |
| [TimeoutException](https://docs.microsoft.com/en-us/dotnet/api/system.timeoutexception?view=netframework-4.8) | The time interval allotted to an operation has expired. |

```csharp
try
{
    // put the code here that may raise exceptions
}
catch
{
    // handle exception here
}
finally
{
    // final cleanup code
}
```

## Multiple Exception Handling

```csharp
Console.Write("Please enter a number to divide 100: ");

try
{
    int num = int.Parse(Console.ReadLine());

    int result = 100 / num;

    Console.WriteLine("100 / {0} = {1}", num, result);
}
catch(DivideByZeroException ex)
{
    Console.Write("Cannot divide by zero. Please try again.");
}
catch(InvalidOperationException ex)
{
    Console.Write("Invalid operation. Please try again.");
}
catch(FormatException  ex)
{
    Console.Write("Not a valid format. Please try again.");
}
catch(Exception  ex)
{
    Console.Write("Error occurred! Please try again.");
}
```

## Custom Exception handling

```csharp
class Student
{
    public int StudentID { get; set; }
    public string StudentName { get; set; }
}

[Serializable]
class InvalidStudentNameException : Exception
{
    public InvalidStudentNameException() {  }

    public InvalidStudentNameException(string name)
: base(String.Format("Invalid Student Name: {0}", name))
    {

    }
}
```

## Multilevel inheritance

```csharp
static void Main(string[] args)
{
    try
    {
        Method1();
    }
    catch(Exception ex)
    {
        Console.WriteLine(ex.StackTrace);
    }                      
}

static void Method1()
{
    try
    {
        Method2();
    }
    catch(Exception ex)
    {
        throw ex;
    } 
}

static void Method2()
{
    string str = null;
    try
    {
        Console.WriteLine(str[0]);
    }
    catch(Exception ex)
    {
        throw;
    } 
}
```

