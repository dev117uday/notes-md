# C\#

### Basics

* has object-oriented design
* has a garbage collector
* has nullable type to guard against that dont refer to allocated objects
* has Exception handling
* has Lambda functions
* All C\# types, including primitive types such as `int` and `double` , inherit from a single root `object`
* C\# supports both user-defined `reference types` and `value types`

### Types and variables

* An identifier may be a C\# reserved word, if it's prefixed by `@` 
* A struct type is similar to a class type in that it represents a structure with data members and function

  members. However, unlike classes, structs are value types and don't typically require heap allocation. struct types don't support user-specified inheritance, and all struct types implicitly inherit from type object .

### Concepts

* `namespaces`
  * to organise the code at big modules, project level
  * alias namespace using : `using PATB = ProjectA.TeamB`
* `string`
  * use `@` in-front of a string to print the whole string as it is.
* Types in C\#
  * Value type : `int`,`float`,`double`
  * Reference type : `interface`,`Class`
  * by default value types are non nullable \(something will be default\), to make them nullable use `?`
  * ex : declare `bool` with `null`, because they cant be `false` or `true`  without any decision
  * ex : if a value is null and you have to assign it to another variable some default value and at the same time want the value store in a variable if not null use the `??` operator
  * use : `int availableTickets = ticketsSold ?? 100;`
* Methods
  * to pass variable as value, just pass, to pass variable by reference, use `ref` keyword in both places
  * you can use the `out` in c\# to return multiple variables
  * use `params` keyword to make arguments optional
  * to override a function that is present in parent class, use the `virtual` keyword in parent class,and use `override` in the child class
  * use the `new` keyword to override the parent class methods from the child class
  * you can use the `base` keyword to call the function from the parent class

### Accessibility 

Each member of a class has an associated accessibility, which controls the regions of program text that can access the member. There are six possible forms of accessibility. The access modifiers are summarized below.

* `public` : Access isn't limited.
* `private` : Access is limited to this class
* `protected` : Access is limited to this class or classes derived from this class.
* `internal` : Access is limited to the current assembly \( .exe or .dll \).
* `protected internal` : Access is limited to this class, classes derived from this class, or classes within the same assembly.
* `private protected` : Access is limited to this class or classes derived from this type within the same assembly.

### Init-only properties

```aspnet
public class Person
{
    public string? FirstName { get; init; }
    public string? LastName { get; init; }
}

// OK
var person = new Person { FirstName = "Mads", LastName = "Nielsen" }; 
// ERROR!
person.LastName = "Torgersen"; 
```

### Records

If you find yourself wanting the whole object to be `immutable` and behave like a value, then you should consider declaring it as a record:

```text
public record Person
{
    public string? FirstName { get; init; }
    public string? LastName { get; init; }
}

var person = new Person { FirstName = "Mads", LastName = "Nielsen" };
var otherPerson = person with { LastName = "Torgersen" };

var originalPerson = otherPerson with { LastName = "Nielsen" };
```

We would now have `ReferenceEquals(person, originalPerson)` = false \(they aren’t the same object\) but `Equals(person, originalPerson)` = true \(they have the same value\).

### IEnumerable

Enumerator for _non-generic collection_

### ActionResult

Action Result is actually a data type. When it is used with action method, it is called return type. As you know, an action is referred to as a method of the controller, the Action Result is the result of action when it executes. In fact, Action Result is a return type.

