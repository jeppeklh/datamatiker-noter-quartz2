tags: #C-sharp #Programmering #AdvancedTopics #MultiThreadingAndConcurrency

> [!tldr] Definition
A thread is the smallest unit of execution within a [[Processes|process]]. 

A [[Processes|process]]. can have multiple threads, which share the same memory space and resources of the [[Processes|process]].

---

## Key Concepts
##### Concurrency
Threads allow a [[Processes|process]]. to perform multiple tasks concurrently, improving the efficiency and responsiveness of applications.

##### Shared Resources
Threads within a [[Processes|process]]. share the same memory and resources, which requires careful synchronization to avoid conflicts.

##### Thread States
Threads can be in various states: new, runnable, blocked, waiting, timed waiting, terminated.

---

## Creating and Managing Threads
##### Creating a Thread
Use the `System.Threading.Thread` [[Classes|class]] to create and manage threads.
```csharp
using System;
using System.Threading;

class ThreadExample
{
    static void Main()
    {
        Thread thread = new Thread(new ThreadStart(ThreadMethod));
        thread.Start();

        Console.WriteLine("Main thread continues to run...");
        thread.Join();
        Console.WriteLine("Thread finished.");
    }

    static void ThreadMethod()
    {
        for (int i = 0; i < 10; i++)
        {
            Console.WriteLine("Thread: {0}", i);
            Thread.Sleep(1000);
        }
    }
}
```

##### Synchronization
Use [[Synchronization Primitives#Lock|locks]], [[Synchronization Primitives#Mutex|mutexes]], [[Synchronization Primitives#Semaphore|semaphores]], and [[Synchronization Primitives#Other Synchronization Primitives|other synchronization primitives]] to manage access to shared resources.
```csharp
private static readonly object lockObject = new object();

static void ThreadMethod()
{
    lock (lockObject)
    {
        for (int i = 0; i < 10; i++)
        {
            Console.WriteLine("Thread: {0}", i);
            Thread.Sleep(1000);
        }
    }
}
```

##### Thread Pooling
Use the thread pool to manage a collection of worker threads efficiently.
```csharp
using System;
using System.Threading;

class ThreadPoolExample
{
    static void Main()
    {
        ThreadPool.QueueUserWorkItem(ThreadPoolMethod);
        Console.WriteLine("Main thread does some work, then sleeps.");
        Thread.Sleep(1000);
        Console.WriteLine("Main thread exits.");
    }

    static void ThreadPoolMethod(Object stateInfo)
    {
        Console.WriteLine("Hello from the thread pool.");
    }
}
```

---

## Related Topics
- [[Multithreading and Concurrency]]
- [[Processes]]

---

## Resources
[Threads Læringobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_28/scormcontent/index.html#/lessons/1FNBudRzrXkqm_I-F67Iz4M4U13LPz_1)
[Singleton Pattern C#](https://csharpindepth.com/articles/singleton)
[Threading with Monitor in C#](https://www.c-sharpcorner.com/UploadFile/1d42da/threading-with-monitor-in-C-Sharp/)
[Threadig with Semaphore in C#](https://www.c-sharpcorner.com/UploadFile/1d42da/threading-with-semaphore-in-C-Sharp/)
[C# - Interlocked examples](https://www.dotnetperls.com/interlocked)