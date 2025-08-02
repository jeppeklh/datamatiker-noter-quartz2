tags: #C-sharp #Programmering #DatabaseAccess #Database #CRUD
> [!tldr] Definition
CRUD stands for [[#Create]], [[#Read]], [[#Update]], and [[#Delete]]. These are the four basic operations that can be performed on a [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]].

The operations are fundamental for interacting with [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|databases]].

---

## Create
This means to generate a new request or to add something.

---

### Example with txt 
```csharp
public void AddToRepository(Room room)
{
    rooms.Add(room);
    Persistence.SaveDataFile(rooms, fileName);
}
```

---

### Example with SQL database

---

## Read
This means to display all records.

---

### Example with txt file
```csharp
public List<Room> GetAll()
    {
        return rooms;
	}
```

---

## Update
This means to change the existing records.

---

### Example with txt file
```csharp
public void UpdateRepository(Room room)
{
    for (int i = 0; i < rooms.Count; i++)
    {
        if (rooms[i].RoomId == room.RoomId)
        {
            rooms[i] = room;
        }
    }
    Persistence.SaveDataFile(rooms, fileName);
}
```

---

## Delete
This means to delete existing records.

---

### Example with txt file
```csharp
public void DeleteFromRepository(Room room)
{
    for (int i = 0; i < rooms.Count; i++)
    {
        if (rooms[i].RoomId == room.RoomId)
        {
            rooms.Remove(rooms[i]);
        }
    }
    Persistence.SaveDataFile(rooms, fileName);
}
```

---

## Related Topics
- [[Database Access Overview]]
- [[Connecting to Databases]]

---

## Resources
![[Pasted image 20240919092333.png]]

```csharp
public IEnumerable<Semester> GetAllSemesters()
{
	var semesters = new List<Semester>();

	using (SqlConnection conn = new SqlConnection(_connectionString))
	{
		string query = "SELECT SemesterId, Number FROM SEMESTER";
		SqlCommand cmd = new SqlCommand(query, conn);
		conn.Open();;
		using (SqlDataReader reader = cmd.ExecuteReader())
		{
			while (reader.Read())
			{
				var semester = new Semester 
				{
					SemesterId = reader.GetInt32(0),
					Number = reader.GetInt32(1)
				};
			semesters.Add(semester);
			}
		}
	}
	return semesters;
}
```

```csharp
public Semester GetSemesterById(int semesterId) 
{
	Semester semester = null;

	using (SqlConnection conn = new SqlConnection(_connectionString))
	{
		string query = "SELECT SemesterId, Number FROM SEMESTER WHERE SemesterId = @SemesterId";
		SqlCommand cmd = new SqlCommand(query, conn);
		cmd.Parameters.AddWithValue("@SemesterId", semesterId);
		conn.Open();;
		
		using (SqlDataReader reader = cmd.ExecuteReader())
		{
			while (reader.Read())
			{
				semester = new Semester 
				{
					SemesterId = reader.GetInt32(0),
					Number = reader.GetInt32(1)
				};
			}
		}
	}
	return semester;
}
```


```csharp
public void AddSemester(Semester semester) 
{
	using (SqlConnection conn = new SqlConnection(_connectionString))
	{
		string query = "INSERT INTO SEMESTER (SemesterId, Numver) VALUES (@SemesterId, @Number)";
		SqlCommand cmd = new SqlCommand(query, conn);
		cmd.Parameters.AddWithValue("@SemesterId", semester.SemesterId);
		cmd.Parameters.AddWithValue("@Number", semester.Number);
		conn.Open();
		cmd.ExecuteNonQuery();
	}
}
```

```csharp
Public void UpdateSemester(Semester semester)
{
	using (SqlConnection conn = new SqlConnection(_connectionString))
	{
		string query = "UPDATE SEMESTER SET NUMBER = @NUMBER WHERE SEMESTERId = @SemesterId";
		SqlCommand cmd = new SqlCommand(query, conn);
		cmd.Parameters.AddWithValue("@SemesterId", semester.SemsterId);
		cmd.Parameters.AddWithValue("@Number", semester.Number);
		conn.Open();
		cmd.ExecuteNonQuery();
	}
}
```

```csharp
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
```


ExecuteReader method is used to execute a SQL Command or storedprocedure returns a set of rows from the database.

ExecuteNonQuery method is used to execute SQL Command or the stored procedure performs INSERT, UPDATE, or Delete operations. It doesn't return any data from the database. Instead, it returns an integer specifying the number of rows inserted, updated or deleted.

ExecuteScalar method is used to execute SQL Commands or storeprocedure, after executing return a single value from the database. It also returns the first column of the first row in the result set from a database.