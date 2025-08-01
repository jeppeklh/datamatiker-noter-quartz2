I Vores projekt valgte vi at anvende en MVVM-struktur. Dette har vi gjort på baggrund af de fordele, som MVVM tilbyder i en WPF-baseret applikation.
ViewModel-laget før det gør det nemt at data- og commandbinde brugergrænsefladens elemeter (Views) direkte til properties og kommandoer i ViewModels. Dette reducerer behovet for code-behind i Views og resulterer i en mere fleksibel og vedligeholdelsesvenlig kodebase.
Vi bruger altså færre event-handlings i code-behind, hvilket også gør koden mere overskuelig. 
MVVM skaber en opdeling mellem UI (View) og forretningslogik (ViewModel). Dette gør det nemmere at teste forrentningslogikken, fordi det kan testes uafhængigt af UI. 

Hvorfor ikke MVC?
Valget af MVVM frem for MVC blev truffet med fokus på at levere et fleksibel, testbar og vedligeholdelsesvenligt program. I MVC er controller-laget ofte tættere knittet til View-laget, hvilket kan gøre testning og udskiftning af lag mere kompliceret.
I en WPF-kontekst er MVVM mere naturligt intergreret med frameworkets funktioner, som bindings. 

ItemsSource="{Binding FilteredEmployeeMVMCollection}" sørger for, at DataGrid dynamisk opdateres med data fra ViewModel’en

Kommandoerne (OpenCreateWindowCommand, OpenUpdateWindowCommand, OpenDeleteWindowCommand) er bundet til knapper, hvilket giver mulighed for at udføre handlinger som oprettelse, opdatering og sletning af medarbejderdata direkte fra brugergrænsefladen

Her er et udsnit fra commanden AddColumnCommand i klassen SkillSetVVM. Vi bruger kommentarer strategisk gennem hele projektet for at forbedre kodelæsbarheden og sikre kvalitet. Ved kun at forklare "hvad" der sker fremfor "hvordan," holder vi kommentarerne korte og målrettede, hvilket gør koden lettere at vedligeholde og forstå for andre udviklere.


Dette interface viser, hvordan vi har brugt absktrakte datayper i vores projekt. Ved at definere et generisk repoisotry-mønster, skaber vi en fleksibel og genanvendelig abstraktion, der kan arbejde med enhver Model-klasse, som opfylder kravene. For eksempel kan T repæsentere en medarbejder, en ferieanmodning, eller en kompetence. 

