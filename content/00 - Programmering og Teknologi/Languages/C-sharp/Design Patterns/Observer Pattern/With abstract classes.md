![[Observer Pattern Abstract classes.png]]
## C-sharp
#### Subject
```csharp
 public abstract class Subject
 {
     List<Observer> observers = new List<Observer>();
     
     public void Attach(Observer o)
     {
         observers.Add(o);
     }
     public void Detach(Observer o)
     {
         observers.Remove(o);
     }
     public void Notify()
     {
         foreach (Observer o in observers)
         {
             o.Update();
         }
     }
 }
 ```
#### ConcreteSubject
```csharp
public class YouTuber : Subject
{
    private string _message;
    public string Message
    {
        get { return _message; }
        set 
        {
            _message = value;`
            Notify(); 
        }
    }
}
```
#### Observer
```csharp
 public abstract class Observer
 {
     public abstract void Update();
 }
```
#### ConreteObserver
```csharp
public class Person : Observer
{
    private YouTuber youTuber; // ConcreteSubject
    private string _message;
    public string Message
    {
        get { return _message; }
        set { _message = value; }
    }
    
    public Person(YouTuber youTuber)
    {
        this.youTuber= youTuber;
    }
   
	public override void Update()
    {
        _message = youTuber.Message;
    }
}
```
