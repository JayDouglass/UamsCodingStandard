C# coding standards
These standards are mostly copying Microsoft's internal coding standards.

# Naming conventions
* Classes: ProperCase
* Public fields, properties, and methods: ProperCase
* Private fields and methods: camelCase (with no preceding underscore)
* Tend to not use abbreviations. We have intellisense, so you aren't slowed down by extra keystrokes. 
* Try not to name things {something}Manager or similar. Often you can just leave the "Manager" part off and it's still clear what the class does. Adding words like that to the end of class adds no additional meaning. If you have trouble naming something, imagine yourself explaining it to another programmer and take note of the unique words you use, those are often good candidates for the name.
* Do not use hungarian notation (prefixing variables with the data type): strName, numAge, etc. 
* Do not pluralize class names. A class is a "blueprint" for a single instance of an entity.

```
public class EmployeeRequest {
	private int somethingPrivate;
	public int Id { get; set; }
	public void NormalizeName() { }
	private void somethingPrivate() { }
}
```

# Coding do's and don'ts
* One file per class
* Namespace structure matches folder structure
* Avoid static classes
 * In the context of a web application they can cause trouble because one instance is shared for all users.
 * Static classes are hard/impossible to unit test because they make it impossible to program in a dependency injected style, and you can not stub-out the class (to be discussed later, or google it).
* Do not put resource intensive code in the constructor (newing a class should be very quick). 
* Use implicity typed variables (these are still statically typed) (var asdf = "asdf";)
* Understand the difference between passing by reference and passing by value. Reference types are "already references". A lot of C# programmers think they need to use pass by ref when they don't need to. Look at stackoverflow for an explanation.
* Use exceptions instead of error codes for error handling. C# and .NET use exceptions for error handling, so that's what we use.
* Tend to not use try/catch blocks, and never swallow exceptions (silently failing). If you need logging, use a global error handler feature (global.asax), or wrap all of your code with a single try/catch in the entry point of your app (console app). Often there is nothing you can do to recover from an exception. Exceptions cause execution to stop and they "bubble up" the stack until they are handled by a try/catch block or the global error handler.
* Do not use try/catch blocks to "humanize" exception messages. There is nothing the end user can do about an error, so they don't need any detail.
* Nuget all the things
* Use appropriate data types when they exist, instead of using strings. 
 * DateTime, TimeSpan, bool, decimal (for money)


* How to add external dlls that are aren't in nuget
 * Create a "dlls" physical folder in the root of your solution (not the project folder)
 * Add your dlls to the physical folder
 * Create a solution folder called "dlls"
 * Click "Add existing item" in visual studio to add the dll to the solution
 * Add reference to project, browsing to the "dlls" folder
 * This avoids accidently adding reference that only works on your machine (because you referenced a dll that isn't in the solution)




