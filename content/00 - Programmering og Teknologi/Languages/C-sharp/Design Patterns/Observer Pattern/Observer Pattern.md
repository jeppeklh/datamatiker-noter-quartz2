tags: #C-sharp #Programmering #DesignPattern

> [!tldr] Definition
> Observer Pattern defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

---

## Two way of implementing Observer Pattern
- [[With abstract classes]]
- [[With interfaces]]

---

## Konsekvenser
Der er både fordele og ulemper ved at benytte sig af et mønster, derfor skal vi nu se på dem for Observer Pattern.

---

### Fordele
##### Low coupling / loose coupling
Subject kender ikke til den [[With abstract classes#ConreteObserver|ConcreteObserver]], men indeholder en kollektion af [[With abstract classes#Observer|Observer]] Kollektionen af [[With abstract classes#Observer|Observer]] bliver notificeret om ændringer uden at skulle vide noget om [[With abstract classes#Subject|Subject]]. [[With abstract classes#Subject|Subject]] og [[With abstract classes#Observer|Observer]] er derfor ikke tæt koblet.

---

##### Flexibility
Vi har den frihed, at vi kan tilføje og fjerne en [[With abstract classes#Observer|Observer]] på et vilkårligt tidspunkt, uden at vores  [[With abstract classes#Subject|Subject]] har behov for en specifik modtager.

---

### Ulemper
##### Performance
Hver eneste gang  [[With abstract classes#Subject|Subject]] ændrer tilstand, skal kollektionen af [[With abstract classes#Observer|Observer]] have en notifikation. Dette kan påvirke ydeevnen af applikationen, især hvis kollektionen af [[With abstract classes#Observer|Observer]] er meget stor, eller hvis der sker hyppige ændringer i  [[With abstract classes#Subject|Subject]].

---

##### Complexity
Man skal administrere tilføjelsen og fjernelsen af en [[With abstract classes#Observer|Observer]], hvilket kan lede til øget kompleksitet i koden.