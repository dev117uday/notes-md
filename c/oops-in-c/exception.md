# Exception

![](../../.gitbook/assets/image%20%2813%29.png)



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

### Multiple Exception Handling

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

### Custom Exception handling

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

### Multilevel inheritance

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



