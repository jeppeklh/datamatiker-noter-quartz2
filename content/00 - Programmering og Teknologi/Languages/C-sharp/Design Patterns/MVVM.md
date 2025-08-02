tags: #C-sharp #Programmering #DesignPattern #MVVM
View -> ViewModel -> Model
View is dependent on ViewModel which is dependent on Model

---

## Model
This represents the data and the business logic of the application. It could be anything from a simple data structure to a complex object-oriented model.

---

## View
This is the user interface or what the user sees and interacts with. It's responsible for displaying the data from the ViewModel and capturing user input.

---

## ViewModel
This acts as an intermediary between the Model and the View. It exposes data from the Model to the View and handles user interactions from the View, typically containing the presentation logic. It also provides commands and data manipulation [[Methods Overview|methods]] that the View can bind to.

The key idea behind MVVM is the separation of concerns: the Model represents the data, the View represents the UI, and the ViewModel acts as a link between them, handling the presentation logic. This separation makes the code more modular, testable, and maintainable.

![[MVVM.png]]

The repository would be placed in the Model- or ViewModel-layer