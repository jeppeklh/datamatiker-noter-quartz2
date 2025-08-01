## Ref

```csharp
static void Main()
{
	int number = 5;
	Console.WriteLine("Before: " + number); // Output: Before: 5
	
	ModifyNumberRef(ref number);
	Console.WriteLine("After: " + number);  // Output: After: 10
}

static void ModifyNumberRef(ref int num)
{
	num = num * 2;
}

```
Here the ModifyNumberRef() [[Methods Overview|method]] changes the value of the defined varuable (number) in the main [[Methods Overview|method]]
(number will after the [[Methods Overview|method]] call permantly be 10 in the main [[Methods Overview|method]] (unless it is changed later ofc))
## Out

```csharp
static void Main()
{
	int result;
	CalculateResult(out result);
	Console.WriteLine("Result: " + result); // Output: Result: 10
}

static void CalculateResult(out int result)
{
	result = 5 * 2;
}

```
Here the Calculate() [[Methods Overview|method]] initialize defined variable (result) in the main [[Methods Overview|method]]
(result will after the [[Methods Overview|method]] call permantly be 10 in the main [[Methods Overview|method]] (unless it is changed later ofc))

## Ref vs Out
So [[#Out|out]] is essentially the same as [[#Ref|ref]]. The only difference is that with out we dont need to have the variable initialized beforehand. It just need to be declared.
