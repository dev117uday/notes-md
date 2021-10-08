# List

![](../../.gitbook/assets/image.png)

```csharp
using System;
using System.Collections.Generic;

public class Program
{
	public static void Main()
	{

		List<string> lst = new List<string>();

		// Adding data to list
		lst.Add("uday");
		lst.Add("uday2");
		lst.Add("uday3");

		// Accessing and modifying data in list
		Console.WriteLine($"All hail {lst[0]}");
		lst[0] = "uday yadav";
		Console.WriteLine($"Correction : All hail {lst[0]}");

		Console.WriteLine("Variants");
		foreach (var variant in lst)
		{
			Console.WriteLine($"variant : {variant}");
		}

		// Insert at position 1, moving all elements to right
		lst.Insert(1, "uday2 yadav");
		Console.WriteLine("Variants");
		foreach (var variant in lst)
		{
			Console.WriteLine($"variant : {variant}");
		}

		lst.Add(null);
		// removes the first occurance of null
		lst.Remove(null);
		// removes the third element in list
		lst.RemoveAt(3);
		// remove the first occurence matching this
		lst.Remove("uday2 yadav");

		Console.WriteLine("Variants");
		foreach (var variant in lst)
		{
			Console.WriteLine($"variant : {variant}");
		}

		// Find whether the element is in the list or not
		Console.WriteLine(lst.Contains("uday yadav"));
		Console.WriteLine(lst.Contains("uday yadav2"));

		// sort the list
		lst.Sort();
	}
}
```

