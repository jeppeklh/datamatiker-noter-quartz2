> [!tldr] Definition
> Et markup-sprog, der bruges til at skrive dynamisk webindhold i ASP.NET. 
> Det kombinerer HTML med C#-kode og gør det muligt at skrive server-side logik direkte i visningsfiler, som renderes af browseren. Razor-syntax bruger `@`-tegnet til at skifte mellem HTML og C#.
>
> Razor-syntax gør det nemt at blande HTML og C#-kode for at skabe dynamiske og interaktive webapplikationer.

---

## Eksempler
> [!example] Indlejret C#-kode
>
>```html
><p>Current date and time: @DateTime.Now</p>
>```
>Dette viser den aktuelle dato og tid.

> [!example] Variabler og udtryk
>```csharp
>@{
 >   var name = "John";
>   var age = 30;
>}
><p>Name: @name</p>
>```
>
Dette definerer variabler og viser deres værdier.

> [!example] Condtional Statements
>```csharp
>@{
 >   var isLoggedIn = true;
> }
>@if (isLoggedIn)
>{
 >   <p>Welcome back!</p>
>}
>else
>{
 >   <p>Please log in.</p>
>}
>```
Dette viser forskellige meddelelser baseret på en betingelse.


> [!example] Loops
>```csharp
>@{
 >   var items = new List<string> { "Item 1", "Item 2", "Item 3" };
> }
><ul>
 >   @foreach (var item in items)
 >   {
 >       <li>@item</li>
 >   }
></ul>
>```
Dette gennemløber en liste og viser hvert element som en liste-post.

---

## Resourcer
- [Blazor Læringsobjekt (Razor)](https://scorm.itslearning.com/data/3289/C20150/ims_import_36/scormcontent/index.html#/lessons/QXCS_VYZyBmGXS-uKNu2L1k4of-VOwLp)
- [Razor Fundatmentals Youtube Video](https://www.youtube.com/watch?v=bsJr9afpCGY&t=6s&ab_channel=CodeAFuture)