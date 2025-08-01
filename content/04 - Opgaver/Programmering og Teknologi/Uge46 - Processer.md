
## Øvelse 1 - Terminologi
---
Del teamet op i to mindre grupper, og brug Ordet rundt til at reflektere over følgende:

Formålet med en ”CPU” og ”RAM”
- CPU (Central Processing Unit): Den primære enhed for beregning i en computer, udfører instruktioner fra programmer.
- RAM (Random Access Memory): Midlertidig hukommelse til hurtig adgang af data for aktive programmer.

Forskellen mellem et “Program” og en “Proces"
- Program: En samling af instruktioner eller kode gemt på disken (statisk).
- Proces: Et program i gang, som bruger CPU og hukommelse (dynamisk).

Formål og rolle for en ”Process Control Block” (”PCB”)
- En datastruktur, som operativsystemet bruger til at gemme information om en proces, fx proces-ID, tilstand og prioritet.

Forskellen mellem “User or application processes”, “System program processes” og “OS processes”
- **User/Application Processes**: Processer startet af brugere, fx teksteditor.
- **System Program Processes**: Processer, der understøtter applikationer, fx netværkstjenester.
- **OS Processes**: Processer, der understøtter OS-funktioner, fx hukommelsesstyring.

Forskellen mellem ”privileged mode” og ”user mode”
- Privileged Mode: Tillader adgang til alle systemressourcer (bruges af OS-processer).
- User Mode: Begrænset adgang til systemressourcer (bruges af applikationer

**Sørg for, at alle får mulighed for at tale.**

Tidsramme: ca. 20 minutter

## Øvelse 2 - Procesmodellen
---
Beskriv følgende sammen med din makker:

Process state
- Eksempelvis "New", "Ready", "Running", "Waiting", "Terminated".

State transition ifm. proces-tilstande
- Transitions kan fx være "Ready" til "Running", når CPU’en tildeles processen, eller "Running" til "Waiting", hvis processen venter på en ressource.

![](https://filerepository.itslearning.com/a729132d-6c10-42b1-bbd6-b514ffca0b10?Token=WTwHANkMAAA7GDZnAAAAACAAdqWFu-qRIO7CnQaQIF_FqXY0hraYSVCpD5YDRi-onVQAAA)

Forskellen på ”Wait-mode” og ”Ready-mode” i figur 2.
- Wait-mode: Processen venter på en ressource.
- Ready-mode: Processen er klar til at få CPU-tid.

Forskellen på tilstandsændringerne ”5 – Interrupted” og ”3 – Needs something”
- **Interrupted (5)**: Processen bliver afbrudt af OS, fx ved en timeout.
- **Needs something (3)**: Processen har brug for en ressource, den venter på.

Hvad kræves af OS for, at tilstandsændringen ”4 – Got what it needed” kan opstå?
- OS’et skal kunne afbryde andre processer eller styre ressourcer effektivt, så de nødvendige ressourcer kan frigøres.

Hvad kræves af et multi-process OS for, at tilstandsændringen ”2 – Gets CPU time” kan udføres, når der er flere processer i tilstand ”Ready”?
- OS’et skal have en scheduler, der kan tildele CPU-tid til processer, der er "Ready".

#### Advarsel
---
Advarsel: Via ”Jobliste” kan du ændre betingelser for kørende processer, herunder standse dem. Hvis du manipulerer med operativsystemets processer, kan du ændre betingelser for andre processer, som afhænger af dem, hermed kan dit system blive ustabilt og uforudsigeligt. Det er ekstremt sjældent, at sådanne konsekvenser ikke kan neutraliseres med en genstart af systemet, men vi giver ingen garantier. Det anbefales derfor, at du ikke manipulerer med processer, medmindre du har et komplet overblik over konsekvenserne.

## Øvelse 3 - Inspektion af Jobliste (Task Manager)
---
I ”gamle dage” betød tastekombinationen ”Ctrl+Alt+Delete”, at PC’en genstartede (reboot’ede), men i dag giver tastekombinationen (i Windows 11 etc.) bl.a. adgang til ”Jobliste”, hvilket du skal se nærmere på i denne øvelse.

#### Øvelse 3.1 - Udforsk og overvej
---
Gå sammen med din sidemakker, og udfør følgende:

Åbn ”Jobliste” på din PC, og udforsk de enkelte faneblade overfladisk (det er helt ufarligt så længe du ikke piller… )
Udforsk fanebladet ”Processer” nøjere.
Bemærk, at flere processer har en foranstillet pil (”>”) som gør, at du kan få yderligere informationer om bagvedliggende processer. Bemærk, også at du får flere muligheder, hvis du højreklikker på et procesnavn.
Prøv om du kan gætte, hvad forskellen mellem ”Apps”, ”Baggrundsprocesser” og ”Windows-processer” er.

## Øvelse 4 - C# processer
---
Benyt parprogrammering i de følgende øvelser.

Iagttag nedenstående program:

```csharp
using System;
using System.Diagnostics;
using System.Threading;

namespace Process01
{

class Program
{

	static void Main(string[] args)
	{
		bool running = true;
		string programName = "Process01"; // skal hedde det same som
										  // konsolapplikationen
		if (args.Length == 0)
		{
			Console.Write("Indtast antal processer, der skal startes : ");
			int antal = int.Parse(Console.ReadLine());
			
			for (int i = 0; i < antal; i++)
			{
				Console.WriteLine($"Starter proces {i}");
				Process process = new Process();
				process.StartInfo.FileName = programName;
				process.StartInfo.Arguments = "\"" + programName + $", version {i}" + "\"";
				process.StartInfo.WindowStyle = ProcessWindowStyle.Normal;
				process.Start();
			}
		}
		else
		{
			int current = 0;
			const int number = 5000;
			const int sleeptime = 5;
			while (running)
			{
				current++;
				Console.WriteLine(args[0] + $", counting to {number}....: " + current);
				Thread.Sleep(sleeptime);
				running = (current < number);
			}
		}
	}
}
}
```

#### Øvelse 4.1 - Hvad kommer der til at ske?
---
Udfør følgende:

Læs først koden igennem og se, om du kan forudsige, hvad den gør.
Vend dine tanker med din sidemakker.

#### Øvelse 4.2 - Flere processer
---
Udfør følgende:

Opret en konsolapplikation med projektnavnet “Process01” (VIGTIGT!)
Erstat klassen ”Program” med koden i bilaget
Kør koden, og lad programmet starte 3 processer
Var din forudsigelse fra tidligere korrekt?
Åbn ”Jobliste”, og undersøg de kørende Apps
Bemærk, hvad der sker, når dine processer standser

#### Øvelse 4.3 - Virtuel hukommelsese
---
Du har måske tænkt tanken: ’Hvad så, hvis jeg løber tør for RAM? Fryser maskinen så?’

I ovenstående tilfælde vil din maskine benytte sig af den virtuelle hukommelse, altså i det tilfælde, at du har benyttet dig af alt den RAM, du har i din maskine (for eksempelvis: 8GB eller 16GB RAM). Men ”Hvad er virtuel hukommelse?”. Virtuel hukommelse er i virkeligheden blot en sidefil, der oprettes på en af dine eksisterende partitioner (en opdeling af diskens lager) i maskinen, hvilket også betyder, at hastigheden af denne sidefil er begrænset af hastigheden på din disk. I gamle dage, hvor man havde harddiske (HDD), var denne sidefil meget langsom. Dette er dog ikke et problem, man som sådan bemærker i moderne maskiner, hvor man har Solid State Diske (SSD).

Formålet med denne øvelse er at fylde din RAM ud og observere, at denne sidefil tages i brug.

Udfør følgende:

Åbn ”Avancerede systemindstillinger”, og klik på ”Indstillinger” ved ”Ydeevne”. Under indstillinger for ydeevne, skal du vælge fanen ”Avanceret” og se, hvor stor en sidefil, der er tildelt som virtuel hukommelse. Husk dette tal
Åbn ”Denne pc” og start det ovenstående program igen, denne gang med markant flere processer (prøv dig frem, notér, hvornår at sidefilen tages i brug)
Bemærk, hvad der sker med den ledige plads, hvis du vælger at starte programmet med mange processer, og bemærk, hvad der sker med den ledige plads, når dine processer standser
**Note:** Hvis du ikke kan se nogen ændring under ”Denne pc”, så benyt dig af F5

## Frivillig - Process Control Block (PCB)
---
I denne opgave skal du oprette en C#-applikation, hvor du skal implementere en process control block – denne øvelse arbejder vi videre på i næste opgave (Ex52), hvor vi vil implementere en prioritetskø (priority queue).

## Frivillig - Oprettelse af PCB
---
Udfør følgende:

Opret en ny konsolapplikation med navnet ”Scheduling”
Opret en C#-klasse med navnet ’PCB’ til at repræsentere en ’process control block’, som du har hørt om i forberedelsen. PCB-klassen er meget forsimplet og har kun følgende properties og metode:
public string ProcessName { get; set; }  
	Angiver navnet på processen, som PCB’en repræsenterer
public int ProcessPriority { get; set; }  
	Angiver processens prioritet, hvor 1 er højeste prioritet og 2, 3, osv. er tilsvarende lavere prioriteter. Prioriteten anvendes til at placere processen korrekt i en prioritetskø.
public ProcessStateType ProcessState { get; set; } Angiver processens prioritet, hvor 1 er højeste prioritet og 2, 3, osv. er tilsvarende lavere prioriteter. Prioriteten anvendes til at placere processen korrekt i en prioritetskø. Enumeration-typen ProcessStateType skal defineres som:
	public enum ProcessStateType { New, Ready, Run, Exit, Wait };
public override string ToString()  
	Returnerer en tekstrepræsentation af PCB’en med formatet: `<navn>`(`<prioritet>`). F.eks. for en proces med navnet ’A’ og prioriteten 2, returnerer ToString() tekststrengen ”A(2)”.