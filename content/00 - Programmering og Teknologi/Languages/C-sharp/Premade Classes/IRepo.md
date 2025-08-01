Interface for CRUD operations.
Used in Repository Pattern.



```csharp
public interface IRepo<T>
{
// Create
void Add(T entity);

// Read
T GetById(int id);
IEnumerable<T> GetAll();

// Update
void Update(T entity);

// Delete
void Remove(int id);
}
```

LoadFromFile() and SaveToFile() methods would typically not be in the interface.
It would however still be in the Repo Class(es).
#### Implemented Example 
---
```csharp
public class MovieRepo : IRepo<Movie>
{
  private List<Movie> movies = [];
  
  public void Add(Movie movie)
  {
      movies.Add(movie);
  }
}
```
Simplified to only 1 method. For the sake of the example.