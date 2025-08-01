tags: #C-sharp #Programmering #AdvancedTopics #MultiThreadingAndConcurrency #SynchronizationPrimitives

## Definition 
---
When working with multithreading, it's essential to ensure that multiple [[Threads|threads]] do not access shared resources simultaneously, leading to conflicts and inconsistencies. 

Synchronization primitives help manage access to these shared resources. 
## Lock
---
A lock is a mechanism to ensure that only one [[Threads|thread]] can access a resource at a time.

In C#, the `lock` statement is a shorthand for acquiring a monitor lock. It ensures that only one [[Threads|thread]] can enter the critical section at a time.

```csharp
private static readonly object lockObject = new object();

static void ThreadMethod()
{
    lock (lockObject)
    {
        // Critical section
        for (int i = 0; i < 10; i++)
        {
            Console.WriteLine("Thread: {0}", i);
            Thread.Sleep(1000);
        }
    }
}
```

## Mutex
---
A mutex (mutual exclusion) is similar to a [[#Lock|lock]] but can work across multiple processes.

Allows multiple [[Threads|threads]] or [[Processes|processes]] to coordinate their activities and ensure exclusive access to shared resources.

```csharp
using System.Threading;

class Program
{
    private static Mutex mutex = new Mutex();

    static void Main()
    {
        for (int i = 0; i < 3; i++)
        {
            new Thread(ThreadMethod).Start();
        }
    }

    static void ThreadMethod()
    {
        Console.WriteLine($"{Thread.CurrentThread.ManagedThreadId} waiting to enter critical section...");
        mutex.WaitOne(); // Wait for access
        Console.WriteLine($"{Thread.CurrentThread.ManagedThreadId} has entered critical section.");
        Thread.Sleep(2000); // Simulate work
        Console.WriteLine($"{Thread.CurrentThread.ManagedThreadId} is leaving critical section.");
        mutex.ReleaseMutex(); // Release access
    }
}
```

## Semaphore
---
A semaphore controls access to a resource by allowing a fixed number of [[Threads|threads]] to enter the critical section simultaneously.

Allows a specified number of [[Threads|threads]] to access a resource concurrently.

```csharp
using System.Threading;

class Program
{
    private static Semaphore semaphore = new Semaphore(2, 2); // Allow up to 2 threads

    static void Main()
    {
        for (int i = 0; i < 5; i++)
        {
            new Thread(ThreadMethod).Start();
        }
    }

    static void ThreadMethod()
    {
        Console.WriteLine($"{Thread.CurrentThread.ManagedThreadId} waiting to enter critical section...");
        semaphore.WaitOne(); // Wait for access
        Console.WriteLine($"{Thread.CurrentThread.ManagedThreadId} has entered critical section.");
        Thread.Sleep(2000); // Simulate work
        Console.WriteLine($"{Thread.CurrentThread.ManagedThreadId} is leaving critical section.");
        semaphore.Release(); // Release access
    }
}
```

## Other Synchronization Primitives
---
##### AutoResetEvent / ManualResetEvent
Used for signaling between threads. An `AutoResetEvent` automatically resets after releasing a single thread, while a `ManualResetEvent` must be manually reset.

##### ReaderWriterLockSlim 
Provides a lock that allows concurrent read access or exclusive write access.

## Related Topics
---
- [[Multithreading and Concurrency]]
- [[Threads]]
- [[Processes]]

## Resources
---
- Link
- 