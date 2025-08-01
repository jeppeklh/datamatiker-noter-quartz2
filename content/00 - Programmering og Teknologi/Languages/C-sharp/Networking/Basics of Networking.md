tags: #C-sharp #Programmering #Networking 

## Definition 
---
The basics of networking in C# involve understanding how to use the [[.NET]] framework to perform network operations. 

This includes sending and receiving data over networks, working with different protocols, and understanding key networking concepts such as sockets and endpoints.
## Key Concepts
---
- **Sockets:** A socket is an endpoint for sending or receiving data across a computer network.
- **TCP and UDP:** Two core protocols for network communication. TCP is connection-oriented, while UDP is connectionless.
- **Endpoints:** An endpoint is a combination of an IP address and a port number that identifies a network service on a host.
### Example: TCP Client
---
```csharp
using System;
using System.Net.Sockets;
using System.Text;

class TcpClientExample
{
    static void Main()
    {
        TcpClient client = new TcpClient("example.com", 80);
        NetworkStream stream = client.GetStream();

        string request = "GET / HTTP/1.1\r\nHost: example.com\r\n\r\n";
        byte[] data = Encoding.ASCII.GetBytes(request);
        stream.Write(data, 0, data.Length);

        byte[] buffer = new byte[256];
        int bytesRead = stream.Read(buffer, 0, buffer.Length);
        string response = Encoding.ASCII.GetString(buffer, 0, bytesRead);

        Console.WriteLine(response);

        stream.Close();
        client.Close();
    }
}

```


## Related Topics
---
- [[Networking Overivew]]
- [[HTTP Requests]]

## Resources
---
- [TcpClient Class](https://learn.microsoft.com/en-us/dotnet/api/system.net.sockets.tcpclient?view=net-8.0)