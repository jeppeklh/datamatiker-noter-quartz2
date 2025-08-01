tags: #C-sharp #Programmering #Networking #HTTP

## Definition 
---
> [!tldr] Definition
HTTP requests i C# bliver typisk lavet i `HttpClient`-klassen, which is part of the `System.Net.Http` namespace. 
>
Klassen giver et simplet interface til at sende HTTP requests og modtage HTTP responses fra en resource identificeret af et URI


## Key Methods
---
- **GetAsync:** Sends a GET request to the specified URI.
- **PostAsync:** Sends a POST request to the specified URI with a specified value.
- **PutAsync:** Sends a PUT request to the specified URI with a specified value.
- **DeleteAsync:** Sends a DELETE request to the specified URI.
  
  


### Example: GET Request
---
```csharp
using System;
using System.Net.Http;
using System.Threading.Tasks;

class HttpClientExample
{
    static async Task Main()
    {
        HttpClient client = new HttpClient();
        HttpResponseMessage response = await client.GetAsync("https://api.example.com/data");
        response.EnsureSuccessStatusCode();
        string responseBody = await response.Content.ReadAsStringAsync();

        Console.WriteLine(responseBody);
    }
}
```


### Example: POST Request
---
```csharp
using System;
using System.Net.Http;
using System.Text;
using System.Threading.Tasks;

class HttpClientPostExample
{
    static async Task Main()
    {
        HttpClient client = new HttpClient();
        string json = "{\"name\":\"value\"}";
        StringContent content = new StringContent(json, Encoding.UTF8, "application/json");

        HttpResponseMessage response = await client.PostAsync("https://api.example.com/data", content);
        response.EnsureSuccessStatusCode();
        string responseBody = await response.Content.ReadAsStringAsync();

        Console.WriteLine(responseBody);
    }
}
```


## Related Topics
---
- [[Networking Overivew]]
- [[Basics of Networking]]

## Resources
---
- [HttpClient Class](https://docs.microsoft.com/en-us/dotnet/api/system.net.http.httpclient)
- [Making HTTP Requests in .NET](https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/console-webapiclient)