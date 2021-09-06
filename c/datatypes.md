# Everything Data in C\#

![](../.gitbook/assets/image%20%2810%29.png)



| Type | Description | Range | Suffix |
| :--- | :--- | :--- | :--- |
| byte | 8-bit unsigned integer | 0 to 255 |  |
| sbyte | 8-bit signed integer | -128 to 127 |  |
| short | 16-bit signed integer | -32,768 to 32,767 |  |
| ushort | 16-bit unsigned integer | 0 to 65,535 |  |
| int | 32-bit signed integer | -2,147,483,648 to 2,147,483,647 |  |
| uint | 32-bit unsigned integer | 0 to 4,294,967,295 | u |
| long | 64-bit signed integer | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 | l |
| ulong | 64-bit unsigned integer | 0 to 18,446,744,073,709,551,615 | ul |
| float | 32-bit Single-precision floating point type | -3.402823e38 to 3.402823e38 | f |
| double | 64-bit double-precision floating point type | -1.79769313486232e308 to 1.79769313486232e308 | d |
| decimal | 128-bit decimal type for financial and monetary calculations | \(+ or -\)1.0 x 10e-28 to 7.9 x 10e28 | m |
| char | 16-bit single Unicode character | Any valid character, e.g. a,\*, \x0058 \(hex\), or\u0058 \(Unicode\) |  |
| bool | 8-bit logical true/false value | True or False |  |
| object | Base type of all other types. |  |  |
| string | A sequence of Unicode characters |  |  |
| DateTime | Represents date and time | 0:00:00am 1/1/01 to 11:59:59pm 12/31/9999 |  |



| Alias | .NET Type | Type |
| :--- | :--- | :--- |
| byte | System.Byte | struct |
| sbyte | System.SByte | struct |
| int | System.Int32 | struct |
| uint | System.UInt32 | struct |
| short | System.Int16 | struct |
| ushort | System.UInt16 | struct |
| long | System.Int64 | struct |
| ulong | System.UInt64 | struct |
| float | System.Single | struct |
| double | System.Double | struct |
| char | System.Char | struct |
| bool | System.Boolean | struct |
| object | System.Object | Class |
| string | System.String | Class |
| decimal | System.Decimal | struct |
| DateTime | System.DateTime | struct |

### Anonymous Datatype

```csharp
var student = new { Id = 1, FirstName = "James",
                        LastName = "Bond" };

Console.WriteLine(student.ToString());

var student = new { 
  Id = 1, 
  FirstName = "James", 
  LastName = "Bond",
  Address = new { 
    Id = 1, 
    City = "London", 
    Country = "UK" 
   }
};
```

## Dynamic Types

```csharp
using System;

dynamic MyDynamicVar = 100;
Console.WriteLine("Value: {0}, Type: {1}", 
    MyDynamicVar, MyDynamicVar.GetType());

MyDynamicVar = "Hello World!!";
Console.WriteLine("Value: {0}, Type: {1}", 
    MyDynamicVar, MyDynamicVar.GetType());

MyDynamicVar = true;
Console.WriteLine("Value: {0}, Type: {1}", 
    MyDynamicVar, MyDynamicVar.GetType());

MyDynamicVar = DateTime.Now;
Console.WriteLine("Value: {0}, Type: {1}", 
    MyDynamicVar, MyDynamicVar.GetType());
```

## Nullable Types

```csharp
Nullable<int> i = null;

Nullable<int> i = null;

    if (i.HasValue)
        Console.WriteLine(i.Value); // or Console.WriteLine(i)
    else
        Console.WriteLine("Null");
```

**Accessing the value using** `NullableType.value` **will throw a runtime exception if `nullable` type is null or not assigned any value.**

### **ShortHand**

```csharp
int? i = null;
double? D = null;

int? i = null;
int j = i ?? 0;
Console.WriteLine(j);
```

## Value vs Reference Types

### Value Types

A data type is a value type if it holds a data value within its own memory space. It means the variables of these data types directly contain values.

The following data types are all of value type:

* bool
* byte
* char
* decimal
* double
* enum
* float
* int
* long
* sbyte
* short
* struct
* uint
* ulong
* ushort

### Reference Type <a id="reference-type"></a>

Unlike value types, a reference type doesn't store its value directly. Instead, it stores the address where the value is being stored. In other words, a reference type contains a pointer to another memory location that holds the data.

The followings are reference type data types:

* String
* Arrays \(even if their elements are value types\)
* Class
* Delegate

## Interface

An interface includes the declarations of related functionalities. The entities that implement the interface must provide the implementation of declared functionalities.

1. Interface can contain declarations of method, properties, indexers, and events.
2. Interface cannot include private, protected, or internal members. All the members are public by default.
3. Interface cannot contain fields, and auto-implemented properties.
4. A class or a struct can implement one or more interfaces implicitly or explicitly. Use public modifier when implementing interface implicitly, whereas don't use it in case of explicit implementation.
5. Implement interface explicitly using `InterfaceName.MemberName`.
6. An interface can inherit one or more interfaces.

```csharp
interface IFile
{
    void ReadFile();
    void WriteFile(string text);
}
```

_**You cannot apply access modifiers to interface members. All the members are public by default. If you use an access modifier in an interface, then the C\# compiler will give a compile-time error**_

An interface can only contain declarations but not implementations

### Explicit Implementation

An interface can be implemented explicitly using `<InterfaceName>.<MemberName>`. Explicit implementation is useful when class is implementing multiple interfaces; thereby, it is more readable and eliminates the confusion. It is also useful if interfaces have the same method name coincidently.

```csharp
interface IFile
{
    void ReadFile();
    void WriteFile(string text);
}
    
class FileInfo : IFile
{
    void IFile.ReadFile()
    {
        Console.WriteLine("Reading File");
    }

    void IFile.WriteFile(string text)
    {
        Console.WriteLine("Writing to file");
    }
}
```

### Implementing Multiple Interfaces

```csharp
interface IFile
{
    void ReadFile();
}

interface IBinaryFile
{
    void OpenBinaryFile();
    void ReadFile();
}

class FileInfo : IFile, IBinaryFile
{
    void IFile.ReadFile()
    {
        Console.WriteLine("Reading Text File");
    }

    void IBinaryFile.OpenBinaryFile()
    {
        Console.WriteLine("Opening Binary File");
    }

    void IBinaryFile.ReadFile()
    {
        Console.WriteLine("Reading Binary File");
    }

    public void Search(string text)
    {
        Console.WriteLine("Searching in File");
    }
}
```

