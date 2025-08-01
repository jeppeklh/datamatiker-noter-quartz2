Koden i do-kodeblokken kører en enkelt gang, hvorefter den tjekker om betingelsen er opfyldt (sand). Hvis den er opfyldt, kører koden i do-kodeblokken gentagne gange, indtil betingelsen ikke er opfyldt længere, dvs. falsk
## Example

```csharp
int i = 0;
do 
{
  Console.WriteLine(i);
  i++;
}
while (i < 5);
```