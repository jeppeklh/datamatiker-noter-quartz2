
> [!tldr] Definition
> A class should only have 1 responsibility or job

---

## Example
#### Before SRP
Here the Employee class have 2 purposes.
- Calculating the bonus
- Saving the data to the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]]

```csharp
// A class that violates SRP
public class Employee 
{
	public string Name {get; set;}
	public double Salary {get; set;}

	// Method for calculationg employee bonus
	public double CalculateBonus(double bonusPercentage) 
	{
		return Salary * bonusPercentage;
	}
	// Method for saving employee data to the databse
	public void SaveEmplyeeToDatabase() 
	{
		Console.WriteLine("Saving employee data to the database...");
		// Code for saving employee data to the database
	}
}
```
#### After SRP
Now the Employee class have been split into 3 different classes
- EmployeeData - representing employee data
- BonusCalculator - calculating employee bonuses
- EmployeeDatabaseManager - saving employee data to the [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]]


```csharp
public class Employee 
{
	public string Name {get; set;}
	public double Salary {get; set;}
}

// A class respinsible for calculating employee bonus
public class BonusCalculator
{
	public double CalculateBonus(EmployeeData employeeData, double bonusPercentage)
	{
		return employeeData.Salary * bonusPercentage;
	}
}

// A class responsible for saving employee data to the database
public class EmplyeeDatabaseManager 
{
	public void SaveEmployeeToDatabase(EmployeeData employeeData)
	{
		Console.WriteLine("Saving employee data to the database...");
		//Code for saving employee data to the databse
	}
}
```