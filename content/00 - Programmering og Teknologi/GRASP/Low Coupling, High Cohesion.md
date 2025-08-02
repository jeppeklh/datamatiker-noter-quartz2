tags: #Programmering #Concept #Principle

> [!tldr] Definition
> **Low Coupling, High Cohesion** is a fundamental principle in software design that aims to create systems that are easier to maintain, understand, and extend. 
> 
> It focuses on the relationships between different modules or components within a system.

---

## Low Coupling
**Low coupling** refers to minimizing the dependencies between different parts of a system. When components are loosely coupled, changes in one component are less likely to affect others, making the system more modular and easier to maintain.

- **Benefits of Low Coupling**:
    
    - **Modularity**: Enhances the ability to update, replace, or change parts of the system without affecting other parts.
    - **Maintainability**: Easier to identify and fix bugs as changes in one module are less likely to introduce issues in others.
    - **Reusability**: Components with low coupling are more likely to be reusable in different contexts or applications.
    - **Testability**: Individual components can be tested in isolation, simplifying unit testing and debugging.

---

### Examples
- **Using Interfaces and Dependency Injection**: By relying on interfaces rather than concrete implementations, components depend on abstractions which can be easily swapped out.
- **Event-Driven Architecture**: Components communicate through events, reducing direct dependencies.

---

## High Cohesion
**High cohesion** refers to ensuring that the elements within a module or component are closely related and focused on a single task or purpose. When a module has high cohesion, it performs a specific set of related functions and has a clear responsibility.

- **Benefits of High Cohesion**:
    
    - **Understandability**: Easier to understand the purpose and behavior of a component as its responsibilities are clearly defined.
    - **Maintainability**: Simplifies changes and enhancements as related functionality is grouped together.
    - **Reusability**: Highly cohesive modules are more self-contained and easier to reuse in different contexts.
    - **Robustness**: High cohesion often leads to more robust and reliable components as they are focused and less complex.

---

### Examples
- [[Single Responsibility Principle]]: Ensuring that a class or module has only one reason to change by encapsulating closely related functionalities.
- **Modular Design**: Grouping related functionalities into modules or components that serve a specific purpose.

---

## Applying Low Coupling and High Cohesion
Combining low coupling and high cohesion leads to a well-structured system where components are independent yet focused. Here are some strategies to achieve this balance:

- **Modularization**: Break down the system into well-defined modules with clear interfaces.
- **Encapsulation**: Hide the internal details of a module from other parts of the system.
- **Design Patterns**: Use design patterns like MVC, [[Repo/00 - Programmering og Teknologi/Languages/C-sharp/Design Patterns/MVVM|MVVM]], and dependency injection to structure code effectively.
- **Separation of Concerns**: Separate different concerns into distinct modules or layers.

---

## Related Topics
- Link
- 

---

## Resources
- Link
- 