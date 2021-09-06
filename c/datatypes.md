# DataTypes

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

