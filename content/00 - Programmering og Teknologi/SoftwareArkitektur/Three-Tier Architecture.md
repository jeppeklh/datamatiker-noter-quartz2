---
aliases:
  - Trelagsarkitekturen
  - Trelagsarkitektur
---
tags: #C-sharp #Programmering #DesignPattern #Three-TierArchitecture

> [!tldr] Definition
> Three-Tier Architecture, is a software design pattern that separates an application into three distinct layers: the [[#Presentation Layer (UI Layer)|Presentation Layer]], the [[#Application Layer (Buisness Logic Layer)|Application Layer]], and the [[#Data Layer (Domain Layer)|Domain Layer]]. 

This separation allows for better manageability, scalability, and modularity.

---

## Presentation Layer (UI Layer)
The Presentation Layer is the topmost layer of the application. 
It is responsible for displaying the user interface and handling user interactions. 
This layer communicates with the [[#Application Layer (Buisness Logic Layer)|Application Layer]] to process user inputs and display results.
##### Example
In a web application, this layer consists of HTML, CSS, and JavaScript that render the UI in a web browser.

---

## Application Layer (Buisness Logic Layer)
The Application Layer acts as a bridge between the [[#Presentation Layer (UI Layer)|Presentation Layer]] and the [[#Data Layer (Domain Layer)|Domain Layer]]. 
It contains components such as repositories, controllers, and datahandlers.

Repositories handle the storage and retrieval of data from the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]]. 
Controllers handle user requests and coordinate the data flow between the [[#Presentation Layer (UI Layer)|Presentation Layer]] and the [[#Data Layer (Domain Layer)|Domain Layer]]. 
Datahandlers format data for storage or display.
##### Example
In an e-commerce application, this layer includes components that manage user sessions, process orders, and interact with the domain classes representing products, customers, and orders.

---

## Data Layer (Domain Layer)
The Domain Layer contains the core functionality and business logic of the application. 

This layer includes domain classes that represent real-world objects and concepts relevant to the business domain.

The layer ensures the business rules and logic are applied consistently across the application.
##### Example
In a library system, the domain layer would include classes like Book, Customer, Loan, and Librarian, each encapsulating the behavior and attributes specific to these entities.

---

## Advantages of Three-Tier Architecture
- **Separation of Concerns**: Each layer has a distinct responsibility, making the application easier to manage and maintain.
- **Scalability**: Individual layers can be scaled independently based on the application’s requirements.
- **Flexibility**: Changes in one layer typically do not affect the other layers, allowing for easier updates and modifications.
- **Reusability**: Common functionalities can be reused across different parts of the application.

---

## Disadvantages of Three-Tier Architecture
- **Complexity**: Introducing multiple layers can add complexity to the application’s design and development.
- **Performance Overhead**: Communication between layers can introduce performance overhead, especially in distributed systems.

---

## Related Topics
- Link
- 

---

## Resources
- Link
- 


![[Trelagsarkitektur.png]]