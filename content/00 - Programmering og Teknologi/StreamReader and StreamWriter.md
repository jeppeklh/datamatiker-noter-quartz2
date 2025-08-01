Both classes are useful when you want to read or write character-based data. Both of these classes deal with Unicode characters.
## StreamReader
Used to read text from a file

```csharp
public static void SaveDataFile<T>(List<T> entities, string fileName) where T : IEntity
{
    string pathName = Path.Combine(targetDirectory, fileName);
    try
    {
        using StreamWriter sw = new(pathName);
        foreach (IEntity entity in entities)
        {
            sw.WriteLine(entity.ToString());
        }
    }
    catch (Exception e)
    {
        Console.WriteLine("Exception: " + e.Message);
    }
}
```

## StreamWriter
Used to write text to a file

```csharp
 public static string[] LoadDataFile(string fileName)
 {
    
     string pathName = Path.Combine(targetDirectory, fileName);
     if (!File.Exists(pathName))
     {
         using StreamWriter sw = new(pathName);
     }

     using StreamReader sr = new(pathName);
     string[] lines = sr.ReadToEnd().Split(new string[] { "\r\n", "\r", "\n" }, StringSplitOptions.None);

     return lines;
 }
```