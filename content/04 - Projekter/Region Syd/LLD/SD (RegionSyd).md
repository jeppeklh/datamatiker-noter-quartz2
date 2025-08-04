	## Iteration 1
---
#### Load From File
```plantuml
@startuml
actor Client

Client -> TaskRepo: LoadFromFile()
activate TaskRepo

TaskRepo -> TaskRepo: Clear task list

TaskRepo -> StreamReader: new StreamReader(filePath)
activate StreamReader

loop Read each line until null
    StreamReader -> StreamReader: ReadLine()
    
    TaskRepo -> TaskRepo: Parse line (split by comma)

    alt TryParse successful
        TaskRepo -> Task: Create new Task
        Task -> TaskRepo: Add Task to List of tasks
    end
end
deactivate StreamReader

TaskRepo -> Client: Return
deactivate TaskRepo
@enduml

```


## Iteration 2
---
#### Delete Assignment

```plantuml
@startuml
actor Disponent
participant AssignmentWindowViewModel as AWMV
participant DeleteWindowViewModel as DWMV
participant AssignmentRepo as Repo
participant DeleteWindow as DW
participant AssignmentVMS as VMS

Disponent -> AWMV: Delete Assignment
AWMV --> DWMV: create(assignmentRepo, AssignmentVMS, SelectedAssignmentVM)
AWMV --> DW: create DeleteWindow(deletewindowviewmodel)
DWMV -> DW: Set DataContext
AWMV --> DW: ShowDialog()

alt User confirms deletion
    DWMV -> Repo: Delete(SelectedAssignmentVM.Assignment.AssignmentID)
    DWMV -> VMS: Remove(SelectedAssignmentVM)
    DWMV -> Disponent: Show success message
    DWMV -> DW: Close()
else User cancels deletion
    DWMV -> DW: Close()
end

@enduml
```


##### Alternativt Delete Assignment

Fordi ShowDialog() venter med at execute kode indtil det bliver lukket kan vi gøre sådan her.
Have et boolean flag i DeleteWindowViewModel. 
ConfirmDelete() sætter det til true.
Cancel() sæetter det til false.

I AssignmentWindowViewModel tjekker vi it et if statement om deleteWindowVM.IsConfirmed.
Hvis det er så kalder vi Delete() på repository og Remove på ObservableCollection (Alt dette i AssignmentWindowViewModel).



```plantuml
@startuml
actor Disponent

participant AssignmentWindow
participant AssignmentWindowViewModel
participant DeleteWindow
participant DeleteWindowViewModel
participant AssignmentRepo

Disponent -> AssignmentWindow: Delete Assignment
AssignmentWindow -> AssignmentWindowViewModel: OpenDeleteWindow()
AssignmentWindowViewModel --> DeleteWindowViewModel: create()
AssignmentWindowViewModel -> DeleteWindow: ShowDialog()

alt Disponent confirms deletion
    DeleteWindow -> DeleteWindowViewModel: ConfirmDeleteCommand()
    DeleteWindowViewModel -> DeleteWindowViewModel: IsConfirmed = true
    DeleteWindowViewModel -> DeleteWindow: Close DeleteWindow

    AssignmentWindowViewModel -> DeleteWindowViewModel: Check IsConfirmed
    AssignmentWindowViewModel -> AssignmentRepo: Delete(selectedAssignment.AssignmentID)
        AssignmentWindowViewModel -> AssignmentWindowViewModel: Remove(SelectedAssignmentVM)
    AssignmentRepo --> AssignmentWindowViewModel: Confirm deletion


    AssignmentWindowViewModel -> Disponent: Show "Assignment deleted"
else Disponent cancels deletion
    DeleteWindow -> DeleteWindowViewModel: CancelCommand()
    DeleteWindowViewModel -> DeleteWindowViewModel: IsConfirmed = false
    DeleteWindowViewModel -> DeleteWindow: Close DeleteWindow

    AssignmentWindowViewModel -> DeleteWindowViewModel: Check IsConfirmed
    AssignmentWindowViewModel -> Disponent: Show "Deletion canceled"
end
@enduml


```