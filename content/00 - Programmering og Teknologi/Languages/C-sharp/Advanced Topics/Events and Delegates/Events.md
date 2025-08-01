tags: #C-sharp #Programmering #AdvancedTopics #Events

## Definition 
---
Events in C# provide a way for a [[Classes|class]] to notify other [[Classes|classes]] or [[Objects|objects]] when something of interest occurs. 
They are based on [[Delegates|delegates]].

They provide a powerful way to implement the [[Observer Pattern|observer pattern]], allowing for decoupled communication between [[Objects|objects]].
#### Basics of Events
---
- **Publisher**: The [[Classes|class]] that sends (or raises) the event.
- **Subscriber**: The [[Classes|class]] that receives (or handles) the event.
- **Event Handler**: A [[Delegates|delegate]] that defines the signature of the [[Methods Overview|method]] that will handle the event.

#### Defining an Event
---
1. **Declare a Delegate**: Define a [[Delegates|delegate]] that specifies the signature of the event handler [[Methods Overview|method]]
2. **Declare an Event**: Use the `event` keyword to declare an event based on the [[Delegates|delegate]].
3. **Raise an Event**: Write a [[Methods Overview|method]] to raise the event, typically using the [[#Invoke Method|Invoke]] [[Methods Overview|method]].
## Syntax
---
```csharp
// Step 1: Declare a delegate
public delegate void EventHandler(object sender, EventArgs e);

// Step 2: Declare an event based on the delegate
public class Publisher
{
    public event EventHandler SomethingHappened;

    // Step 3: Raise the event
    protected virtual void OnSomethingHappened(EventArgs e)
    {
        SomethingHappened?.Invoke(this, e);
    }
}
```

## Invoke Method
---
The `Invoke` method is used to call (or raise) the event. The line 
```csharp
SomethingHappened?.Invoke(this, e);
```
ensures that the event is not `null` before invoking it. This is a shorthand for:
```csharp
if (SomethingHappened != null)
{
    SomethingHappened(this, e);
}
```
In this context:
- `SomethingHappened` is the event.
- `this` refers to the current instance of the class raising the event.
- `e` is the event data, typically an instance of `EventArgs` or a [[Nedarvning#Derived class|derived class]].

## Subscribing to an Event
---
To handle an event, a subscriber must:
1. Define a [[Methods Overview|method]] that matches the [[Delegates|delegate]] signature.
2. Attach the [[Methods Overview|method]] to the event using the `+=` operator.

```csharp
// Publisher class
public class Publisher
{
    public event EventHandler SomethingHappened;

    public void DoSomething()
    {
        // Some logic
        OnSomethingHappened(EventArgs.Empty);
    }

    protected virtual void OnSomethingHappened(EventArgs e)
    {
        SomethingHappened?.Invoke(this, e);
    }
}

// Subscriber class
public class Subscriber
{
    public void Subscribe(Publisher pub)
    {
        pub.SomethingHappened += HandleEvent;
    }

    private void HandleEvent(object sender, EventArgs e)
    {
        Console.WriteLine("Event received");
    }
}

// Usage
public class Program
{
    public static void Main()
    {
        Publisher pub = new Publisher();
        Subscriber sub = new Subscriber();
        sub.Subscribe(pub);

        pub.DoSomething();  // This will trigger the event and call HandleEvent
    }
}
```

## Key Concepts
---
- **EventHandler Delegate**: A predefined delegate used for most events in the .NET framework. It has the following signature:
```csharp
public delegate void EventHandler(object sender, EventArgs e);
```
- **EventArgs Class**: The base class for classes containing event data. If no data is needed, `EventArgs.Empty` can be used.
- **Custom Event Data**: If an event needs to pass custom data, derive a class from `EventArgs`.
```csharp
public class CustomEventArgs : EventArgs
{
    public string Message { get; }

    public CustomEventArgs(string message)
    {
        Message = message;
    }
}

public event EventHandler<CustomEventArgs> CustomEvent;

protected virtual void OnCustomEvent(CustomEventArgs e)
{
    CustomEvent?.Invoke(this, e);
}
```

## Related Topics
---
- [[Events and Delegates Overview]]
- [[Delegates]]

## Resources
---
- [Events Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_13/scormcontent/index.html#/lessons/7BFnyWppRlPaZ0-674hmKMxRGjxecE7O)
- 