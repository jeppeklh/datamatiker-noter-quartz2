tags: #Programmering #SQL

Se først
[[Forudsætninger for at arbejde med Fase C]]

---

## Overview 
Ved at bruge  [[Repository Pattern]] kan man behandle [[Data|data]] fra [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|databasen]] som en samling af objekter i stedet for at interagere direkte med SQL-forespørgsler. 
Det gør applikationen lettere at vedligeholde, teste og udvide, fordi databaseforespørgsler centraliseres ét sted.

Vi bruger forsætter på samme eksempel fra [[Database Design|fase A]] og [[Database Implementering|fase B]].
![[Databasemodel eksempel 4.png]]

---

## Trin 1: Opret et generisk interface
Først definerer du et [[IRepo|generisk repository]] [[Abstraktion#Interface|interface]], der kan bruges som en kontrakt for [[CRUD Operations|CRUD]]-operationer.

```csharp
public interface IRepository<T> where T : class
{
    IEnumerable<T> GetAll();
    T GetById(int id);
    void Add(T entity);
    void Update(T entity);
    void Delete(int id);
}
```

---

## Trin 2: Opret et specifikt repository for en entitet
Derefter implementerer vi et konkret repository for entiteten Semester, som overholder `IRepository<Semester>` kontrakten.

```csharp
public class SemesterRepository : IRepository<Semester>
{
    private readonly string _connectionString;

    public SemesterRepository(string connectionString)
    {
        _connectionString = connectionString;
    }

    public IEnumerable<Semester> GetAll()
    {
        var semesters = new List<Semester>();
        string query = "SELECT * FROM SEMESTER";

        using (SqlConnection connection = new SqlConnection(_connectionString))
        {
            SqlCommand command = new SqlCommand(query, connection);
            connection.Open();

            using (SqlDataReader reader = command.ExecuteReader())
            {
                while (reader.Read())
                {
                    semesters.Add(new Semester
                    {
                        SemesterId = (int)reader["SemesterId"],
                        Number = (int)reader["Number"]
                    });
                }
            }
        }

        return semesters;
    }

    public Semester GetById(int id)
    {
        Semester semester = null;
        string query = "SELECT * FROM SEMESTER WHERE SemesterId = @SemesterId";

        using (SqlConnection connection = new SqlConnection(_connectionString))
        {
            SqlCommand command = new SqlCommand(query, connection);
            command.Parameters.AddWithValue("@SemesterId", id);
            connection.Open();

            using (SqlDataReader reader = command.ExecuteReader())
            {
                if (reader.Read())
                {
                    semester = new Semester
                    {
                        SemesterId = (int)reader["SemesterId"],
                        Number = (int)reader["Number"]
                    };
                }
            }
        }

        return semester;
    }

    public void Add(Semester semester)
    {
        string query = "INSERT INTO SEMESTER (Number) VALUES (@Number)";

        using (SqlConnection connection = new SqlConnection(_connectionString))
        {
            SqlCommand command = new SqlCommand(query, connection);
            command.Parameters.AddWithValue("@Number", semester.Number);
            connection.Open();
            command.ExecuteNonQuery();
        }
    }

    public void Update(Semester semester)
    {
        string query = "UPDATE SEMESTER SET Number = @Number WHERE SemesterId = @SemesterId";

        using (SqlConnection connection = new SqlConnection(_connectionString))
        {
            SqlCommand command = new SqlCommand(query, connection);
            command.Parameters.AddWithValue("@Number", semester.Number);
            command.Parameters.AddWithValue("@SemesterId", semester.SemesterId);
            connection.Open();
            command.ExecuteNonQuery();
        }
    }

    public void Delete(int id)
    {
        string query = "DELETE FROM SEMESTER WHERE SemesterId = @SemesterId";

        using (SqlConnection connection = new SqlConnection(_connectionString))
        {
            SqlCommand command = new SqlCommand(query, connection);
            command.Parameters.AddWithValue("@SemesterId", id);
            connection.Open();
            command.ExecuteNonQuery();
        }
    }
}
```

---

## Trin 3: Brug repository i din applikation
For at bruge SemesterRepository i din applikation kan du gøre det således: (dette eksempel er skrevet i en konsolapplikation):

```csharp
 string connectionString = "your_connection_string_here";
        IRepository<Semester> semesterRepository = new SemesterRepository(connectionString);

        // Adding a new semester
        semesterRepository.Add(new Semester { Number = 2024 });

        // Getting all semesters
        var semesters = semesterRepository.GetAll();
        foreach (var semester in semesters)
        {
            Console.WriteLine($"Semester ID: {semester.SemesterId}, Number: {semester.Number}");
        }

        // Updating a semester
        var firstSemester = semesterRepository.GetById(1);
        if (firstSemester != null)
        {
            firstSemester.Number = 2025;
            semesterRepository.Update(firstSemester);
        }

        // Deleting a semester
        semesterRepository.Delete(1);
```

---

## Trin 4: Gentag trin 2 og trin 3 for af de andre entiteter i din applikation
Når du arbejder med en ny entitet, f.eks. en Student-entitet, vil du oprette et nyt repository, StudentRepository, og bruge dette repository i din applikation for at håndtere Student-relaterede data.  

Ved at følge dette trin sikrer du, at hver entitet i din applikation har sit eget repository, som gør det nemt at håndtere data på en struktureret måde og opretholde en klar separation af ansvar.

---

## Related Topics
- Link
- 

---

## Resources
- [Databasetilgang via Csharp og .NET Læringobjekt](https://rise.articulate.com/share/65tiUowEA12ttXX3SsFPiF1jJxG8gdCJ#/lessons/BLQVQXe_qoLGYI0e0ecTR_ryD_SnX-s0)
- [Ado.NET tutorial](https://www.javatpoint.com/ado-net-tutorial)
- [Auto increment fields](https://www.w3schools.com/sql/sql_autoincrement.asp)