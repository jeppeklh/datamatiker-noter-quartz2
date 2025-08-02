tags: #C-sharp #Programmering #AdvancedTopics #MultiThreadingAndConcurrency

> [!tldr] Definition
> A process is an instance of a program that is executed independently and managed by the operating system. 
> It contains the program code and its current activity.

---

## Key Concepts
##### Isolation
Each process runs in its own memory space and does not share memory directly with other processes, providing isolation and stability.

##### Resource Management
Processes are allocated resources like memory, file handles, and CPU time by the operating system.

##### Process Control Block (PCB)
The PCB is a data structure used by the operating system to store all information about a process, including its state, program counter, and memory allocation.

---

## Creating and Managing Processes
##### Creating a Process
Use the `System.Diagnostics.Process` class to create and manage processes.

```csharp
using System.Diagnostics;

public void StartProcess()
{
    Process process = new Process();
    process.StartInfo.FileName = "notepad.exe";
    process.Start();
}
```

##### Process States
Processes can be in various states: new, ready, running, waiting, terminated.

##### Inter-process Communication (IPC)
Mechanisms like pipes, shared memory, and message queues allow processes to communicate and synchronize with each other.

---

## Example
```csharp
using System;
using System.Diagnostics;

class ProcessExample
{
    static void Main()
    {
        Process process = new Process();
        process.StartInfo.FileName = "notepad.exe";
        process.Start();

        Console.WriteLine("Process started. Press any key to exit.");
        Console.ReadKey();

        if (!process.HasExited)
        {
            process.Kill();
            Console.WriteLine("Process killed.");
        }
    }
}
```

---

## Related Topics
- 

---

## Resources
-  [Microsoft Documentation on Processes](https://learn.microsoft.com/en-us/dotnet/api/system.diagnostics.process?view=net-8.0)
- [Processer Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_27/scormcontent/index.html#/lessons/kbsy3lmCrvuPoGJegE4u_HBUsodKm-F4)