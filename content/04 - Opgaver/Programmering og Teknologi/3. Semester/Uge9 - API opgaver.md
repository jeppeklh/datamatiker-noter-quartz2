## Opgave 2
Opret en MVC-applikation, der viser vejrudsigten ved at hente data fra valgte ovenstående API via httpClient.

**Hint: I får brug for at deserialisere data til C#-objekter. Deserialisering er, når data fra en fil eller streng omdannes tilbage til et brugbart objekt i et program. Det kan gøres således:**

[Serialisering dokmentation](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/how-to?pivots=dotnet-core-3-1)
[Github Løsning](https://github.com/Team-6-UCL-datamatiker/270225Gruppe6Opgaver/tree/master/270225Gruppe6Opgaver)

Vi laver et MVC projekt.

Opretter en model klasse WeatherData med alt det data vi vil vise fra det vi henter fra APIøøen på JSON-format (vi kan se dette format via postman).

```csharp
public class WeatherData
{
	public string name { get; set; }
	public int timezone { get; set; }
	public int visibility { get; set; }
	public Coord coord { get; set; }
	public List<Weather> weather { get; set; }
	public Main main { get; set; }
	public Wind wind { get; set; }
	public Clouds clouds { get; set; }
	public Sys sys { get; set; }
}

public class Coord
{
	public double lon { get; set; }
	public double lat { get; set; }
}

public class Weather
{
	public int id { get; set; }
	public string main { get; set; }
	public string description { get; set; }
	public string icon { get; set; }
}

public class Main
{
	public double temp { get; set; }
	public double feels_like { get; set; }
	public double temp_min { get; set; }
	public double temp_max { get; set; }
	public int pressure { get; set; }
	public int humidity { get; set; }
	public int sea_level { get; set; }
	public int grnd_level { get; set; }

}

public class Wind
{
	public double speed { get; set; }
	public int deg { get; set; }
}
public class Clouds
{
	public int all { get; set; }
}

public class Sys
{
	public double sunrise { get; set; }
	public double sunset { get; set; }
	public string country { get; set; }

}
```

Vi laver vorews controller. Hvor vi har skrevet vores API-key. Vi laver en HttpGet [[Action method]]. Denne metoder henter dataene på Json-format og Deserialiserer de data til et WeatherData objekt i C#

```csharp
public class WeatherController : Controller
{
	private string apiKey = "414a97767435cbb52a942be59deffd2d";

	[HttpGet]
	public async Task<IActionResult> Weather(string city = "Copenhagen")
	{
		using (HttpClient client = new HttpClient())
		{
			string url = $"https://api.openweathermap.org/data/2.5/weather?q={city}&appid={apiKey}&units=metric";

			HttpResponseMessage response = await client.GetAsync(url);

			if (response.IsSuccessStatusCode)
			{
				string json = await response.Content.ReadAsStringAsync();

				WeatherData weather = JsonSerializer.Deserialize<WeatherData>(json);
				
				return View(weather);
			}

			else
			{
				return NotFound();
			}
		}
	}
}
```

Nu laver vi så et razor view, der indeholder alle de data vi vil vise:
```html
﻿@model WeatherData

@{
	double daylength = (@Model.sys.sunset - @Model.sys.sunrise)/60/60;
	string icon = @Model.weather[0].icon;
}

<h1> Vejret i @Model.name </h1>
<div style="background-color:lightblue; display: flex; flex-direction: column">
	<p> Temperature: @Model.main.temp</p>
	<div style="background-color:white; display: flex; align-items:center">
	<p> Description: @Model.weather[0].description</p>
	<img src="@($"https://openweathermap.org/img/wn/{icon}.png")" height="100" width="100"/>
	</div>
	<p> Feels like: @Model.main.feels_like</p>
	<p> Min temperature: @Model.main.temp_min</p>
	<p> Max temperature: @Model.main.temp_max</p>
	<p> Day length: @daylength</p>
	<p> Visibility: @Model.visibility</p>
	<p> Longitude: @Model.coord.lon</p>
	<p> Latitude: @Model.coord.lat</p>
	<p> Country: @Model.sys.country</p>
	<p> Timezone: @Model.timezone</p>
	<p> WIND: @Model.wind.speed</p>
	<p> sunrise: @Model.sys.sunrise</p>
	<p> sunset: @Model.sys.sunset</p>
</div>
```

Vi husker også at skrive routen ind i Program.cs filen så vi kan tilgå den via urlen
```csharp
app.MapControllerRoute(
	name: "weatherRoute",
	pattern: "{controller=Weather}/{action=Weather}/{id?}");
```

Dette angiver formatet af routen. Hvis der ikke bliver angivet en controller, er defaulten WeatherController. Hvis der ikker bliver angivet en [[Action method]] er defaulten Weather-metoden. Id har vi ikke brug for i dette tilfælde.
Vi gav dog vores Weather-action-method en valgfri parameter - nemlig byen. Dette betyder at vi kan skrive således i URL'en for at få f.eks. Londons info
`dinserver/Weather?city=London`
Bemærk at vi ikke behøver at angive Action metoden i urlen fordi defaulten er Weather