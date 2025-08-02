
## Blazor Server 
Fungerer ved at køre alle komponenter direkte på serveren. Enhver brugerinteraktion sendes via en SignalR-forbindelse til serveren, hvor komponenten behandles. Serveren sender efterfølgende kun de minimale UI-opdateringer tilbage til browseren. Dette betyder, at hele applikationens logik og processeringskraft ligger på serveren, hvilket kan være fordelagtigt i situationer med komplekse beregninger eller begrænset klientudstyr.  

---

## Blazor WebAssembly 
Anvender en anderledes tilgang. Her kompileres hele .NET-runtimen til WebAssembly, hvilket betyder, at applikationen kan køre direkte i brugerens browser.

---

## Resourcer
- [Blazor Projekttyper Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_39/scormcontent/index.html#/lessons/cvMTsNz1mzTPtnlUTGfD6ZiMjJfDDtlH)