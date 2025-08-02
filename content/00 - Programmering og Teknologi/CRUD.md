> [!tldr] Definition
> The acronym CRUD is made up of four words. Those four words are taken from the first letters of the SQL commands. And is often used for datahandling.

---

## Create
This means to generate a new request or to add something.

#### Example with txt 
```csharp
public void AddToRepository(Room room)
{
    rooms.Add(room);
    Persistence.SaveDataFile(rooms, fileName);
}
```

---

## Read
This means to display all records.
#### Example with txt file
```csharp
public List<Room> GetAll()
    {
        return rooms;
	}
```

---

## Update
This means to change the existing records.
#### Example with txt file
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
#### Example with txt file
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
