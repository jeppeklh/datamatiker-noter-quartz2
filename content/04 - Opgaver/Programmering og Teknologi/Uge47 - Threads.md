## Øvelse 1 - Terminologi
---
Del teamet op i to mindre grupper (evt. 2-3 personer i hver), og brug Ordet rundt til at reflektere over begreberne ”Singleton Pattern”, ”Lazy Loading”, ”Thread”, ”Process”, ”Thread-safe (da: trådsikker)”, ”Lock”, ”Deadlocks”, ”Mutual Exclusion”, ”Circular wait” og ”Hold-and-wait”.

Sørg for, at alle får mulighed for at tale.

**Singleton Pattern**: Et mønster, hvor kun én instans af en klasse er tilladt. Bruges til at styre adgang til delte ressourcer.

**Lazy Loading**: En teknik, hvor data først indlæses, når det er nødvendigt, for at spare ressourcer.

**Thread**: En tråd er en mindre udførelsesenhed inden for en proces.
> ([[threading.pdf#page=4&selection=10,63,11,34&color=yellow|p.4]])
> A thread is an independent execution path, able to run simultaneously with other threads.

**Process**: En proces er et program i eksekvering, der kan have flere tråde.

**Thread-safe**: Sikrer korrekt funktionalitet, selv når flere tråde kører samtidigt og deler ressourcer.

**Lock**: Bruges til at forhindre flere tråde i at tilgå en delt ressource samtidigt.

**Deadlocks**: Når to eller flere tråde venter på hinanden og aldrig kommer videre.

**Mutual Exclusion**: Garanterer, at kun én tråd kan tilgå en ressource ad gangen.

**Circular Wait**: En cyklus, hvor tråde holder ressourcer og venter på hinanden.

**Hold-and-Wait**: En tråd holder en ressource og venter på en anden ressource.

Tidsramme: 20 minutter

## Øvelse 2: Start af en Thread
---
Implementer 3 tråde, som hver skriver ”Hello world (metode/lambda/anonym)” på skærmen 4 gange ved at anvende henholdsvis en metode, et lambda-udtryk og en anonym metode som argument til Thread().

Fremgangsmåde:

Implementer en metode som anvendes som argument til Thread()
Definer et lambda udtryk som argument til Thread()
Definer en anonym metode som argument til Thread()

Output skulle gerne se ud som følgende:

![](https://filerepository.itslearning.com/d73c2d8b-9f18-460b-bc58-3e3ba3e92cc4?Token=WTwHANkMAAA9Wj9nAAAAACAArEqbeMyDvdCE4qS6yr-gx2R20DH2vfaNDhCqr_pY3BAAAA)
```csharp
using System;
using System.Threading;

class Program
{
    static void Main()
    {
        // 1. Metode
        Thread t1 = new Thread(HelloWorldMethod);
        t1.Start();

        // 2. Lambda
        Thread t2 = new Thread(() =>
        {
            for (int i = 0; i < 4; i++) Console.WriteLine("Hello world (lambda)");
        });
        t2.Start();

        // 3. Anonym metode
        Thread t3 = new Thread(delegate ()
        {
            for (int i = 0; i < 4; i++) Console.WriteLine("Hello world (anonymous)");
        });
        t3.Start();
    }

    static void HelloWorldMethod()
    {
        for (int i = 0; i < 4; i++) Console.WriteLine("Hello world (method)");
    }
}

```

## Øvelse 3: Benyt argument, når tråd startes
---
Ændr din implementering af trådene fra øvelse 2, så du kan overføre en tekststreng som et argument til trådens Start-metode. F.eks.: t1.Start("Hello world (metode)");

Fremgangsmåde:

Udvid din implementering af metoden, så den kan tage imod et objekt som argument og skrive den ud på skærmen
Udvid dit lambda-udtryk, så den også tager imod et objekt som argument og kan skrive den ud på skærmen
Udvid din anonyme metode, så den kan skrive en tekststreng ud på skærmen

Bemærk, at Start-metoden kun accepterer et argument af typen "object". Derudover er der ikke nogen forskel rent funktionelt, så du skal stadigvæk få det samme resultat printet ud til skærmen.

```csharp
System;
using System.Threading;

class Program
{
    static void Main()
    {
	    // Metode
		Thread t = new Thread(PrintHelloWorld);
		t.Start("Hello");

		// Lambda
		new Thread(s =>
		{
			for (int i = 0; i < 4; i++)
			{
				Console.WriteLine(s);
			}
		}).Start("123");

		// Delegate
		new Thread(delegate(object? s)
		{
			for (int i = 0; i < 4; i++)
			{
				Console.WriteLine(s);
			}
		}).Start("fjsdkl");
		Console.ReadLine();
	}

	// Metode
	static void PrintHelloWorld(object? s)
	{
		for (int i = 0; i < 4; i++)
		{
			Console.WriteLine(s);
		}
	}
}

```
## Øvelse 4: En betragtning, double-checked locking
---
Betragt nedenstående metode, der implementer double checked locking:

![](https://filerepository.itslearning.com/8c2b7e4d-df2e-4e43-918b-acb878e8ec89?Token=WTwHANkMAAA9Wj9nAAAAACAAaL8r0aF4lQU1T2XfSziX5dy-xWtxKUWjo_KWeCZCnDQAAA)

Besvar følgende spørgsmål i relation til kodeeksemplet:

Er det nødvendigt at kontrollere for null i både linje 10 og 14?
	med andre ord: kan en af linjerne undværes?
- Når tråde rammer låsen næsten samtidigt, kan mere end én tråd potentielt kontrollere `null` udenfor låsen og forsøge at oprette objektet.
- Låsemekanismen sikrer, at kun én tråd kan oprette objektet, men du er nødt til at kontrollere `null` igen indenfor låsen for at undgå, at den første tråd, der opretter objektet, bliver overskrevet af andre tråde, der kommer efter.

Kan der være grunde til at have begge linjer, som de er?
Ja, det sikrer, at instansen kun oprettes én gang, selv med flere tråde.

## Øvelse 5: Delt ressourceproblem
---
Analyser nedenstående program, og forudsig, hvad der sker under udførelsen af programmet (herunder output til skærm). Du må ikke prøve at køre programmet, førend du er færdig med din forudsigelse.

![](https://filerepository.itslearning.com/65cc397e-5263-4ff7-a9ea-aaa9bc9c7843?Token=WTwHANkMAAA9Wj9nAAAAACAAXKislEIgHGuVMGI9M2TGS0tIKM10hkevEtasf-EOnPMAAA)

Når du er klar, så udfør følgende:

Opret et nyt konsolprojekt
Indsæt nu koden ind i dit konsol-projekt i VS
Kør programmet

Gav det samme output, som du forudsagde?

## Øvelse 6: Delt ressourceproblem – Løsning
---
Du har nok bemærket, at programmet i øvelse 5 har et åbenlyst problem vedrørende den delte ressource (_sharedChar), hvilket resulterer i, at der kan opstå forekomster såsom ”Thread B : A” og ”Thread A : B”.

Løs problemet, så der kun printes ”Thread A : A” og ”Thread B : B” ud til skærmen.

**Note: Du må ikke ændre på den rækkefølge trådene starter i, i Run()-metoden – du skal bruge en lås.**

## Klargøring
---
Udfør følgende:

Hent kodedokumentet ’Threads.Kode.docx’ i Git materialefolderen. (tilgængelig via. ItsLearning)

Dokumentet indeholder nogle kodeudsnit, som du skal bruge i de følgende øvelser.

## Øvelse 7: Delt ressourceproblem
---
Find ’Kode udsnit 1’ i kodedokumentet.

Programmet simulerer kørsel af registreringer fra et antal vejrstationer (WEATHERSTATIONS). Hver vejrstation, repræsenteret af en tråd, har en sensor, som foretager et antal målinger (MEASURES) af en given værdi (VALUE). For at gøre kørslen deterministisk er værdien det samme hver gang (1.0). Værdierne summeres, så for hver kørsel burde summen være (WEATHERSTATIONS * MEASURES * VALUE). Hvis accum ikke har denne værdi for en kørsel udskrives forskellen.

Udfør følgende:

Opret et nyt konsolprojekt
Kopier kodeudsnittet (’Kode udsnit 1’) over til VS og kør det
	Forklar resultatet1
Løs problemet ved hjælp af låsning
	Du har løst problemet, når der blot står: ”Press a key …”

**Hint: Overvej nøje, hvor problemet opstår, og hvorfor.**

## Øvelse 8: Interlocked (frivillig)
---
Problemet i øvelse 7 var, at en anden tråd kunne ”bryde ind” og manipulere accum fra accum blev læst (og gemt i temp) til accum blev tildelt sin nye værdi. Denne delte ressource skulle trådsikres, for at undgå synkroniseringsproblemet, ved hjælp af en lås.

Nu skal du se lidt længere nede i kodedokumentet. Se på ‘kodeudsnit 2’. Programmet viser (forhåbentligt), at operationerne X++ og X-- heller ikke er trådsikre.

To tråde (adder og subtractor) manipulerer Number samme antal gange. Den samlede effekt burde altså være at Number er lig med nul efter kørslen. Forhåbentlig viser en kørsel af programmet, at dette ikke er tilfældet2. En ofte anvendt ”løsning” på denne problematik er at benytte en lås i definitionen af get og set:

public Int64 Number {get { lock (key) { return _number; } } set { lock (key) { _number = value; } } }

En hurtig test viser dog, at det heller ikke er trådsikkert.

Udfør følgende:

Forklar, hvorfor “løsningen” ikke er trådsikker
Løs problemet vha. klassen InterLocked. (se forberedelsen til i dag).

## Øvelse 9: Producer/Consumer (frivillig)
---
I denne øvelse skal du arbejde med tråde og producer/consumer-problematikken.

### Øvelse 9.1: Forberedelse
---
Opret en ny konsolapplikation i Visual Studio IDE
Brug koden fra ‘Kode udsnit 3’ i kodedokumentet til at implementere de nødvendige klasser:
	Program.cs
	Producer.cs
	Consumer.cs
	Buffer.cs
	Car.cs
Sørg for at indsætte de korrekte namespaces i din kode, så den kan kompileres (bygges ikke køres) uden fejl
Inspicer koden

### Øvelse 9.2 - Trådsikring af Put()- og Get()-metoderne i Buffer-klassen
---
I denne øvelse skal du gøre Put()- og Get-metoderne i Buffer-klassen trådsikre ved hjælp af Monitor-klassen. Buffer-klassen har allerede en bufferLock, som du kan bruge.

Krav til implementeringen:

Du skal aflåse den kritiske sektion, som er tilgangen til køen bufferData, ved hjælp af Monitor.Enter() og Monitor.Exit().
Du skal benytte Monitor.Wait, når køen er tom og Get() bliver kaldt fra en Consumer, og benytter Monitor.Pulse() for at vække en ventende tråd, når en ny Car er blvet tilføjet.
Du skal benytte Monitor.Wait(), når køen er fuld og Put() bliver kaldt fra en Producer, og benytte Monitor.Pulse() for at vække en ventende tråd, når Car er blevet fjernet.
Du må ikke bruge ”Lock”
Du skal benytte IsFull() og IsEmpty() metoderne.


![[Threading eksempel Thomas.png]]