
## Abstract classes
Classes that cannot be instantiated directly and may contain [[Abstraktion#Abstract Method|abstract methods]], serving as blueprints for other [[#Class|classes]]. (must be [[Nedarvning#Overriding|overwritten]] in the [[Nedarvning#Derived class|derived class]])

Se [[Abstraktion]]

## Acces modifiers
Bruges til at sætte access level/visibility for [[#Class|klasser]], [[#Field-variables|fields]], metoder og [[#Properties|properties]]
- [[Access modifiers#public|public]]
- [[Access modifiers#private|private]]
- [[Access modifiers#internal|internal]]
- [[Access modifiers#protected|protected]]
- [[Access modifiers#protected internal|protected internal]]
- [[Access modifiers#private protected|private protected]]

## Applikation
Et stykke software der løser et bestemt problem.
## Break
Keyword der bruges til at forlade en [[#Loops|løkke]]/[[#Forgrening|forgrening]]

Se [[Repo/00 - Programmering og Teknologi/Languages/C-sharp/Control Flows/Branching Logic/Switch#Break|break]]

## Class
En C#-klasse er en skabelon, der beskriver en familie af [[#Object|objekter]] via dets data og adfærd

## Class library
Collection of pre-written classes and components compiled into a DLL for reuse in other projects.

## Constructor
Det er en speciel metode, der bliver kaldt hver gang et [[#Object|objekt]] fra den [[#Class|klasse]] bliver [[#Instanciering|instancieret]]

## CRUD
Metoder der ofte bliver brugt i forbindelse med datahandling
- [[CRUD#Create|Create]]
- [[CRUD#Read|Read]] 
- [[CRUD#Update|Update]]
- [[CRUD#Delete|Delete]]

Se [[CRUD]]
## Datatypes
- [[string]]
- [[char]]
- [[bool]]
- [[int]]
- [[double]]
- [[float]]
- [[decimal]]


## Datarepræsentation
Datarepræsentation er information, som bliver anvendt i et program sammen med programmets adfærd

## Debugging
The process of detecting and correcting errors in a program.

Se [[Debugging|debugging]]

## Declaration
(type) (variabelnavn);
```csharp
int i;
string myString;
```

## Default

Keyword der specificerer noget kode til at køre, hvis ingen case er mødt

Bruges i [[Repo/00 - Programmering og Teknologi/Languages/C-sharp/Control Flows/Branching Logic/Switch]]
Se [[Repo/00 - Programmering og Teknologi/Languages/C-sharp/Control Flows/Branching Logic/Switch#Default|default]]

## Delegates og Events
Et event er en beskyttet version af en delegate


## Encapsulation
En måde at beskytte data på
At gøre sin data [[Access modifiers#private|private]], så den ikke kan ændres udefra, og derfor er mere sikker

Se [[Indkapsling]]

## Field-variables
andre navne:
Fields
Felt-variabler
attributes
member-variables
se [[#Backing field]]

## Forgrening
#### If-else
Der tjekkes om en betingelse er opfyldt. Hvis ja, afvikles kodekroppen, ellers afvikles andet kode

Se [[If-variants]]
#### Switch
Use the `switch` statement to select one of many code blocks to be executed.

Se [[Repo/00 - Programmering og Teknologi/Languages/C-sharp/Control Flows/Branching Logic/Switch]]

## Inheritance
OOP principle where a class ([[Nedarvning#Derived class|subclass]]) inherits properties and behaviors from another [[#Class|class]] ([[Nedarvning#Base class|superclass]]), promoting code reuse.

se [[Nedarvning]]

## Initialisering
Er en initialisering:
```csharp
string Test = "Hej"; 
```

Er ikke! Se [[#Declaration|erklæring]]
```csharp
int i; 
```


## Instanciering
```cs
MyClass myObject = new MyClass();
```

## Interface
En kontrakt omkring bl.a. klassefunktionalitet, som en [[#Class|klasse]] kan implementere

Se [[Abstraktion#Interface|interface]]

## Instruktion
En ordre et computerprogram giver til processeren

## Kodeblok
En del af koden der er grupperet sammen
Består af flere [[#Statement|statements]]

## Loops
Loops are used to execute one or more [[#Statement|statements]] multiple times until a specified condition is fulfilled.
 - [[For loop|For]]
 - [[Foreach loop|Foreach]]
 - [[While loop|While]]
 - [[Do-While loop|Do-While]]
#### for vs while
[[For loop|For-loop]] bruges, når man ved, hvor mange gange en sekvens skal itereres; [[While loop|while-loop]] kan bruges, når man vil afbryde løkken baseret på en betingelse i stedet for antal gange

## Namespace
#### Kan man tilgå en klasse fra et andet namespace?
Ja, ved brug af reference til det andet namespace

## OOP-Principles
[[Indkapsling]], [[Polymorfi]], [[Nedarvning]], [[Abstraktion]]
## Object
Et objekt er en [[#Instanciering|instans]] af en [[#Class|klasse]]

## Overloading
Når flere metoder deler samme navn, men har forskellige parametre
Kan ikke have forskellige [[#Datatypes|datatypes]]
Der bruges [[Polymorfi]]

## Out
It is similar to [[#Ref|ref]] keyword. But the main difference between [[#Ref|ref]] and out keyword is that [[#Ref|ref]] needs that the variable must be [[#Initialisering|initialized]] before it passed to the [[Methods Overview|method]].

Se [[ref and out#Out|out]]

## Properties
Properties muliggør det at tilgå en [[Access modifiers#private|private]] værdi uden at komprimere sikkerheden i sine data
Se [[Indkapsling|Indkapsling]]

## Ref
The ref keyword in C# is used for passing or returning references of values to or from [[Methods Overview|methods]].

Ligenene [[ref and out#Out|out]]
Se [[ref and out#Ref|ref]]


#### Backing field
Et [[Access modifiers#private|private]] [[#Field-variables|felt]] som gemmer data og kan tilgås gennem en [[Access modifiers#public|public]] property

#### Auto-implemented property
```csharp
public string FirstName { get; set; }
```
Se [[Indkapsling]]

## Return
Keyword der bruges til at komme ud af en metode

## Scope
En variabel kan kun benyttes inden for det virkefelt, den er [[#Declaration|erklæret]] i

## SOLO
Præstrukturel, unistrukturel, multistrukturel, relationelt og udvidet 

## Statement
Et statement gør noget, men returnerer ikke noget, hvorimod en expression returnerer en værdi

Er et statement
```csharp
String name;
```
 Er et statement
```csharp
if(true) 
{
	// Code
} 
```
Ikke et statement
```csharp
// Kommentar
```


## StreamReader
Læser data fra en fil

Se [[StreamReader and StreamWriter#StreamReader|StreamReader]]

## StreamWriter
Skriver data til en fil

Se [[StreamReader and StreamWriter#StreamWriter|StreamWriter]]

## String Interpolation
En anden måde at lave [[string#Concatination|string concatination]] på

se [[string#Interpolation|interpolation]]

## TryParse
Der returneres en [[#|boolesk]] værdi, som angiver om konverteringen lykkedes, og hvis den gjorde, sættes [[#int]]-parameteren lig med [[#string|tekststrengens]] heltalsværdi.
```csharp
int.TryParse(minString, out minInt)
```


## Typecasting
```csharp
int myInt = (int) myDouble;
```

## Unittest
Hvor du tester individuelle dele af din kode, om de virker som test-designeren forventer

Vi har brugt [[MSTest]]
