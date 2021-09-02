# Keywords

### Modifier Keywords

Modifier keywords are specific keywords that indicate who can modify types and type members. Modifiers allow or prevent certain parts of programs from being modified by other parts.



| Keyword | Description |
| :--- | :--- |
| abstract | The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation. An abstract class cannot be instantiated |
| async | Use the `async` modifier to specify that a method is asynchronous. just like node.js `async` await but better. |
| const | You use the `const` keyword to declare a constant field or a constant local |
| [event](https://www.tutorialsteacher.com/csharp/csharp-event) | The `event` keyword is used to declare an event in a publisher class. |
| `extern` | The `extern` modifier is used to declare a method that is implemented externally |
| new modifier | When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class. When you hide an inherited member, the derived version of the member replaces the base class version |
| in modifier | [https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/in-generic-modifier](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/in-generic-modifier) |
| out | [https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/out-generic-modifier](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/out-generic-modifier) |
| override | The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event. |
| [partial](https://www.tutorialsteacher.com/csharp/csharp-partial-class) | It is possible to split the definition of a class, a struct, an interface or a method over two or more source files. Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled. |
| `readonly` | A `readonly` field can't be assigned after the constructor exits |
| sealed | When applied to a class, the `sealed` modifier prevents other classes from inheriting from it |
| [static](https://www.tutorialsteacher.com/csharp/csharp-static) | Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object |
| unsafe | The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers |
| virtual | The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class. |
| volatile | The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time. The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons |

### Access Modifier Keywords

| Keyword | Description |
| :--- | :--- |
| public | Allows any part of the program to access the type and its members. |
| private | Restricts other parts of the program from accessing the type and its members.  |
| internal | Allows other program code in the same assembly to access the type or its members. This is default access modifiers if no modifier is specified. |
| protected | Allows codes in the same class or a class that derives from that class to access the type or its members. |
| [protected internal](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/protected-internal) | The type or member can be accessed by any code in the assembly in which it's declared, or from within a derived `class` in another assembly. |
| [private protected](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/private-protected) | The type or member can be accessed only within its declaring assembly, by code in the same `class` or in a type that is derived from that `class` |

### Statement Keywords



<table>
  <thead>
    <tr>
      <th style="text-align:left">Keyword</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">if</td>
      <td style="text-align:left"><code> if ( condition ) {}</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">else</td>
      <td style="text-align:left"><code>if ( condition ) {} else { statement }</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">switch</td>
      <td style="text-align:left"><code>switch ( expression ) { case 1 : ... }</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">case</td>
      <td style="text-align:left">
        <p><code>switch(expression) { </code>
        </p>
        <p><code>   case x: // code block break; </code>
        </p>
        <p><code>   case y: // code block break; </code>
        </p>
        <p><code>   default: // code block break; </code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">do</td>
      <td style="text-align:left">
        <p><code>do { </code>
        </p>
        <p><code>   // code block to be executed </code>
        </p>
        <p><code>} while (condition);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">for</td>
      <td style="text-align:left">
        <p><code>for (statement 1; statement 2; statement 3) { </code>
        </p>
        <p><code>   // code block to be executed </code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">foreach</td>
      <td style="text-align:left">
        <p><code>var fibNumbers = new List { 0, 1, 1, 2, 3, 5, 8, 13 }; </code>
        </p>
        <p><code>foreach (int element in fibNumbers) { </code>
        </p>
        <p><code>    Console.Write($&quot;{element} &quot;); </code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">in</td>
      <td style="text-align:left"><code>The in keyword causes arguments to be passed by reference but ensures the argument is not modified </code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Example : in</td>
      <td style="text-align:left">
        <p><code>int readonlyArgument = 44; </code>
        </p>
        <p><code>void InArgExample(in int number) { </code>
        </p>
        <p><code>    // Uncomment the following line to see error CS8331 </code>
        </p>
        <p><code>    //number = 19; </code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">while</td>
      <td style="text-align:left">
        <p><code>while(condition) {</code>
        </p>
        <p><code>    //code block </code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">break</td>
      <td style="text-align:left">
        <p><code>for (int i = 0; i &lt; 10; i++) { </code>
        </p>
        <p><code>   if (i == 4) { break; } </code>
        </p>
        <p><code>   Console.WriteLine(i); </code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">continue</td>
      <td style="text-align:left">
        <p><code>for (int i = 0; i &lt; 10; i++) {</code>
        </p>
        <p><code>   if (i == 4) { continue; } </code>
        </p>
        <p><code>   Console.WriteLine(i); </code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">default</td>
      <td style="text-align:left">Default in switch case, <em>aka</em> the break condition</td>
    </tr>
    <tr>
      <td style="text-align:left">goto</td>
      <td style="text-align:left">The goto is C# unconditional jump statement. When encountered, program
        flow jumps to the location specified by the goto.</td>
    </tr>
    <tr>
      <td style="text-align:left">ex : goto</td>
      <td style="text-align:left">
        <p><b>Never ending loop</b>
        </p>
        <p><code>static void Main(string[] args) { </code>
        </p>
        <p><code>  SomeLabel: </code>
        </p>
        <p><code>    for (int i = 0; i &lt; 10; i++) </code>
        </p>
        <p><code>      { </code>
        </p>
        <p><code>        if (i == 5) { </code>
        </p>
        <p><code>          Console.WriteLine(&quot;Exiting&quot;); </code>
        </p>
        <p><code>          goto SomeLabel; </code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">ex : goto</td>
      <td style="text-align:left">
        <p><b><code>This will break out of the loop</code></b>
        </p>
        <p><code>static void Main(string[] args) {</code>
        </p>
        <p><code>  for (int i = 0; i &lt; 10; i++) { </code>
        </p>
        <p><code>    if (i == 5) { </code>
        </p>
        <p><code>      Console.WriteLine(&quot;Exiting&quot;); </code>
        </p>
        <p><code>      goto SomeLabel; </code>
        </p>
        <p><code>    }</code>
        </p>
        <p><code>  } </code>
        </p>
        <p><code>SomeLabel: </code>
        </p>
        <p><code>  Console.WriteLine(&quot;Done&quot;); </code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">return</td>
      <td style="text-align:left">
        <p>final gift from the function, after which its execution ends</p>
        <p><code>return 4;</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">yield</td>
      <td style="text-align:left">it generates something on demand</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p><code>static void Main(string[] args) { </code>
        </p>
        <p><code> foreach (var item in func(2,4)) { </code>
        </p>
        <p><code>  Console.WriteLine(item); </code>
        </p>
        <p><code> } </code>
        </p>
        <p><code>}</code>
        </p>
        <p><code>public static IEnumerable func(int start, int end) { </code>
        </p>
        <p><code> for (int i = start; i &lt; end; i++) { </code>
        </p>
        <p><code>  yield return i+5; </code>
        </p>
        <p><code> } </code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">throw/try/catch</td>
      <td style="text-align:left">
        <p><code>try { </code>
        </p>
        <p><code>  throw new NullReferenceException(&quot;Student object is null.&quot;); </code>
        </p>
        <p><code>} catch(Exception ex) { </code>
        </p>
        <p><code>  Console.WriteLine(ex.Message ); </code>
        </p>
        <p><code>} finally {</code>
        </p>
        <p><code>  Console.WriteLine(&quot;Done with try catch&quot;)</code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/throw">https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/throw</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">checked</td>
      <td style="text-align:left">The <code>checked</code> keyword is used to explicitly enable overflow checking
        for integral-type arithmetic operations and conversions.</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p><code>try { </code>
        </p>
        <p><code>  int ten = 10;</code>
        </p>
        <p><code>  Console.WriteLine(checked(2147483647 + ten));</code>
        </p>
        <p><code>} catch (Exception e) { Console.WriteLine(e.Message); </code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">unchecked</td>
      <td style="text-align:left">The unchecked keyword is used to suppress overflow-checking for integral-type
        arithmetic operations and conversions. It will let the integer overflow
        its value</td>
    </tr>
    <tr>
      <td style="text-align:left">fixed</td>
      <td style="text-align:left">The <code>fixed</code> statement prevents the garbage collector from relocating
        a movable variable. The <code>fixed</code> statement is only permitted in
        an <a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/unsafe">unsafe</a> context.
        You can also use the <code>fixed</code> keyword to create <a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/unsafe-code#fixed-size-buffers">fixed size buffers</a>.</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left"><a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/fixed-statement">https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/fixed-statement</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">lock</td>
      <td style="text-align:left">The <code>lock</code> statement acquires the mutual-exclusion lock for a
        given object, executes a statement block, and then releases the lock. While
        a lock is held, the thread that holds the lock can again acquire and release
        the lock. Any other thread is blocked from acquiring the lock and waits
        until the lock is released.</td>
    </tr>
  </tbody>
</table>

### Method Parameter Keyword

<table>
  <thead>
    <tr>
      <th style="text-align:left">Keyword</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">params</td>
      <td style="text-align:left">you can specify a <a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/method-parameters">method parameter</a> that
        takes a variable number of arguments. The parameter type must be a single-dimensional
        array.</td>
    </tr>
    <tr>
      <td style="text-align:left">&lt;code&gt;&lt;/code&gt;</td>
      <td style="text-align:left">
        <p><code>public static void UseParams(params int[] list) { </code>
        </p>
        <p><code>  for (int i = 0; i &lt; list.Length; i++) { </code>
        </p>
        <p><code>    Console.Write(list[i] + &quot; &quot;); </code>
        </p>
        <p><code>  } </code>
        </p>
        <p><code>  Console.WriteLine(); </code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">ref</td>
      <td style="text-align:left">The <code>ref</code> keyword indicates that a value is passed by reference.</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left"><code>void SomeFunction(ref int num)</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">out</td>
      <td style="text-align:left">The <code>out</code> keyword causes arguments to be passed by reference.
        It makes the formal parameter an alias for the argument, which must be
        a variable. In other words, any operation on the parameter is made on the
        argument.</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p><code>int initializeInMethod;</code>
        </p>
        <p><code>OutArgExample(out initializeInMethod); </code>
        </p>
        <p><code>void OutArgExample(out int number) { </code>
        </p>
        <p><code>  number = 44; </code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>

### Namespace Keywords

<table>
  <thead>
    <tr>
      <th style="text-align:left">Keyword</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">. operator</td>
      <td style="text-align:left">to acess methods of object</td>
    </tr>
    <tr>
      <td style="text-align:left">:: operator</td>
      <td style="text-align:left">Use the namespace alias qualifier <code>::</code> to access a member of
        an aliased namespace. You can use the <code>::</code> qualifier only between
        two identifiers. The left-hand identifier can be any of the following aliases</td>
    </tr>
    <tr>
      <td style="text-align:left">extern alias</td>
      <td style="text-align:left">To reference two versions of assemblies that have the same fully-qualified
        type names.</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p><code>extern alias GridV1;</code>
        </p>
        <p><code>extern alias GridV2; </code>
        </p>
        <p><code>using Class1V1 = GridV1::Namespace.Class1;</code>
        </p>
        <p><code>using Class1V2 = GridV2::Namespace.Class1;</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">using</td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>The <a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/using-statement">using statement</a> defines
            a scope at the end of which an object will be disposed.</li>
          <li>The <a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/using-directive">using directive</a> creates
            an alias for a namespace or imports types defined in other namespaces.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

### Operator Keywords

<table>
  <thead>
    <tr>
      <th style="text-align:left">Keyword</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">as</td>
      <td style="text-align:left">The <b>as</b> operator is used to perform conversion between compatible
        reference types or Nullable types. This operator returns the object when
        they are compatible with the given type and <em><b>return null if the conversion is not possible</b></em> instead
        of raising an exception</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p><code>object obj = &quot;hello&quot;; </code>
        </p>
        <p><code>string str = obj as string;</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">await</td>
      <td style="text-align:left">wait for async method to return or convert Task&lt;T&gt; to T</td>
    </tr>
    <tr>
      <td style="text-align:left">is</td>
      <td style="text-align:left">The <code>is</code> operator checks if the result of an expression is compatible
        with a given type</td>
    </tr>
    <tr>
      <td style="text-align:left">new</td>
      <td style="text-align:left">The <code>new</code> operator creates a new instance of a type.</td>
    </tr>
    <tr>
      <td style="text-align:left">sizeof</td>
      <td style="text-align:left">The <code>sizeof</code> operator returns the number of bytes occupied by
        a variable of a given type.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://www.geeksforgeeks.org/typeof-operator-keyword-in-c-sharp/">typeof</a>
      </td>
      <td style="text-align:left">The <b>typeof </b>is an operator keyword which is used to get a type at
        the compile-time.</td>
    </tr>
    <tr>
      <td style="text-align:left">stackalloc</td>
      <td style="text-align:left">
        <p>A <code>stackalloc</code> expression allocates a block of memory on the
          stack. A stack allocated memory block created during the method execution
          is automatically discarded when that method returns. You cannot explicitly
          free the memory allocated with <code>stackalloc</code>
        </p>
        <p>&lt;code&gt;&lt;/code&gt;<a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/stackalloc"><code>https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/stackalloc</code></a>&lt;code&gt;&lt;/code&gt;</p>
      </td>
    </tr>
  </tbody>
</table>

### Base Keyword

| Keyword | Description |
| :--- | :--- |
| this | The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method. |
| base | The `base` keyword is used to access members of the base class from within a derived class |

### Literal keywords

<table>
  <thead>
    <tr>
      <th style="text-align:left">Keyword</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">false</td>
      <td style="text-align:left"><code>not true</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">true</td>
      <td style="text-align:left"><code>not false</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">value</td>
      <td style="text-align:left"><code>value</code> is used in the <code>set</code> accessor in <a href="https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties">property</a> and
        <a
        href="https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/indexers/">indexer</a>declarations</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p><code>public virtual int Number </code>
        </p>
        <p><code>{ </code>
        </p>
        <p><code>  get { return num; } </code>
        </p>
        <p><code>  set { num = value; } </code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">void</td>
      <td style="text-align:left">You use <code>void</code> as the return type of a <a href="https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/methods">method</a> (or
        a <a href="https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/local-functions">local function</a>)
        to specify that the method doesn&apos;t return a value.</td>
    </tr>
    <tr>
      <td style="text-align:left">null</td>
      <td style="text-align:left">one that does not refer to any object. null is <b>the default value of reference-type variables</b>
      </td>
    </tr>
  </tbody>
</table>

### Contextual keyword

| Keyword | Description |
| :--- | :--- |
| var | used to declare implicit type variables |
| _**dynamic**_ | The type is a static type, but an object of type dynamic bypasses static type checking. In most cases, it functions like it has type object |
| global | global refers to the global namespace, it can be used to solve problems whereby you may redefine types |
|  | `global :: System.Console.WriteLine("hello world");` |
| set | object initializer \| goes along with get |

