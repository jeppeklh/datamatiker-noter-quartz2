tags: #C-sharp #Programmering #AdvancedTopics #Delegates

## Definition 
---
A delegate in C# is a type that represents references to [[Methods Overview|methods]] with a particular [[Parameters|parameter]] list and [[Return Values|return type]]. 

Delegates are used to pass [[Methods Overview|methods]] as arguments to other [[Methods Overview|methods]] and define callback [[Methods Overview|methods]].

#### Basics of Delegates
---
- **Type-Safe**: Delegates ensure that the signature of the [[Methods Overview|method]] matches the signature specified by the delegate type.
- **Multicast**: Delegates can reference multiple [[Methods Overview|methods]].
- **Used for Callbacks**: Delegates are commonly used to implement callback [[Methods Overview|methods]].
#### Declaring and Using Delegates
---
1. **Declare a Delegate**: Define the delegate type.
2. **Instantiate a Delegate**: Create an instance of the delegate, referencing a method.
3. **Invoke the Delegate**: Call the delegate, which in turn calls the referenced method(s).

#### Delegate Signature
---
A delegate signature defines the [[Methods Overview|method]]'s [[Return Values|return]] [[Datatypes|type]] and [[Parameters|parameter]] [[Datatypes|types]] that the delegate can reference. 

This ensures that any [[Methods Overview|method]] assigned to the delegate matches this signature. The delegate signature is declared when defining the delegate type.
```csharp
// Delegate signature: void MyDelegate(string message)
public delegate void MyDelegate(string message);
```
In this example, `MyDelegate` is a delegate type that can reference any method that takes a single `string` parameter and returns `void`.
## Syntax
---

```csharp
public class Program
{

	// Definér en delegate
	
	delegate void GreetDelegate(string message);

	
	public static void EnglishGreeting(string message)
	{
		Console.WriteLine("Hello, " + message);
	}
	public static void SpanishGreeting(string message)
	{
		Console.WriteLine("Hola, " + message);
	}
	


	public static void Main()
	{
		
		// Brug af delegate
		GreetDelegate greet = EnglishGreeting;
		greet("world"); // Output: Hello, world
		greet = SpanishGreeting;
		greet("mundo"); // Output: Hola, mundo
		Console.WriteLine("Hello World");
	}
}
```
## Multicast Delegates
---
Delegates can reference more than one [[Methods Overview|method]]. 
When invoked, they call all the [[Methods Overview|methods]] they reference, in order.

Deklaration af delegaten: 
Vi erklærer en delegate Notify, som repræsenterer metoder, der ikke tager nogen parametre og ikke returnerer noget.

Metodeoprettelse: 
Vi opretter to metoder;  **ShowMessage** og **LogMessage**, som hver især skriver en besked til konsollen.

Når vi kalder **Notify**, bliver alle tre metoder kaldt i den rækkefølge, de blev tilføjet.


```csharp
public class Program
{
    // Definer en delegate, der peger på metoder, der ikke returnerer noget og tager en string parameter.
    public delegate void Notify(string message);

    // Metoder der matcher delegate-signaturen
    public static void ShowMessage(string message)
    {
        Console.WriteLine("Message: " + message);
    }

    public static void LogMessage(string message)
    {
        Console.WriteLine("Log: " + message);
    }

    public static void Main()
    {
        // Opret en multicast delegate ved at tilføje metoder til delegate-objektet
        Notify notifyDelegate = ShowMessage;
        notifyDelegate += LogMessage;

        // Kalder alle metoder i multicast delegate
        notifyDelegate("Hello World"); //Message: Hello World
									   //Log: Hello World

        // Fjern en metode fra multicast delegate
        notifyDelegate -= ShowMessage; 

        // Kalder den resterende metode i multicast delegate
        notifyDelegate("Goodbye World"); //Log: Goodbye World
    }
}
```

## Generic Delegates
---
En generisk delegate gør det muligt at arbejde med forskellige datatyper uden at skulle definere flere forskellige delegater.

Vi erklærer en generisk delegate Operation```<T> ```, som kan tage to parametre af typen T og returnere en værdi af typen T. T er en generisk typeparameter, der kan erstattes med enhver datatype, når delegaten bruges.

Vi initialiserer en instans af den generiske delegate Operation```<int> ```  Add-metoden og kalder den med to heltal.

Vi initialiserer endnu en instans af den generiske delegate Operation```<string> ``` med Concatenate-metoden og kalder den med to strenge.


```csharp
public class Program
{
    // Definer en generisk delegate
    public delegate T Operation<T>(T a, T b);

    // Metode der tilføjer to værdier
    public static int Add(int x, int y)
    {
        return x + y;
    }

    // Metode der sammenkæder to strenge
    public static string Concatenate(string str1, string str2)
    {
        return str1 + str2;
    }

    public static void Main()
    {
        // Brug af den generiske delegate med int
        Operation<int> addOperation = Add;
        int result = addOperation(3, 4);
        Console.WriteLine("Addition Result: " + result);  // Output: 7

        // Brug af den generiske delegate med string
        Operation<string> concatenateOperation = Concatenate;
        string combined = concatenateOperation("Hello, ", "World!");
        Console.WriteLine("Concatenation Result: " + combined);  // Output: Hello, World!
    }
}
```


## Anonymous Methods
---
Delegates can also reference anonymous [[Methods Overview|methods]], which are [[Methods Overview|methods]] without a name, defined inline.
```csharp
public class Program
{
    public delegate void MyDelegate(string message);

    public static void Main()
    {
        MyDelegate del = delegate(string message)
        {
            Console.WriteLine(message);
        };

        del("Hello, Anonymous Method!");
        //Outputs:
        //Method1: Hello, World!
		//Method2: Hello, World!

    }
}
```

## Lambda Expressions
---
[[Lambda Expressions]] provide a more concise syntax for creating delegates. They are particularly useful in [[LINQ]] queries.
```csharp
public class Program
{
    public delegate void MyDelegate(string message);

    public static void Main()
    {
        MyDelegate del = (message) => { Console.WriteLine(message); };

        del("Hello, Lambda Expression!");
    }
}
```

## Built-in Delegates
---
The .NET framework provides built-in delegate types to simplify common delegate usage:
- [[Action]]
- [[Func]]
- [[Predicate]]

```csharp
public class Program
{
    public static void Main()
    {
        // Using Action
        Action<string> action = (message) => { Console.WriteLine(message); };
        action("Hello, Action!");

        // Using Func
        Func<int, int, int> add = (a, b) => a + b;
        int result = add(3, 4);
        Console.WriteLine("Sum: " + result);

        // Using Predicate
        Predicate<int> isEven = (number) => number % 2 == 0;
        bool isFourEven = isEven(4);
        Console.WriteLine("Is 4 even? " + isFourEven);
    }
}
```
## Related Topics
---
- [[Events and Delegates Overview]]
- [[Events]]

## Opgaver
---
- [[Uge34 - Delegates og Lambda Expressions (Svaret).pdf#page=1&selection=0,4,0,4|Uge 34 Opgaver]]

## Resources
---
- [Delegates læringobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_7/scormcontent/index.html#/lessons/jt-TPRwlQVWBIbcT8fVV7xD9gUMrrqPJ)
- [Lambdaudtryk læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_8/scormcontent/index.html#/lessons/_a6KeY2tA66kQMUd7hX1Vs5kcZ6mZyKQ)