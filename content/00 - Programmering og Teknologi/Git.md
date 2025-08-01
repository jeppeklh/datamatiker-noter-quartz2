tags: #Programmering #Tools #Git
## Git init
---
Laver et tomt git repo eller reinsancier et eksisterende

## Git pull
---
Henter fra og integrerer det med en lokal branch

## Git add
---
Tilføjer filer til index

## Git commit
---
Laver en ny commit der tager indholdet I index (filer) og den givne log besked  beskriver ændringerne

## Git push
---
Skubber ændringerne ud til github repoet på den givne branch

## Git status
---
Viser tree statussen (Kan se hvilker filer der added til index og hvilke filer der venter på at blive pushet ud.

## Git clone
---
Kloner et repo ind I en ny mappe.

## Git checkout
---
Skifter branch 


## Git Konventioner
---
En Github organization per projekt.  
Kan have flere repositories. Hver medlem kan have deres eget testrepo eller lege med deres eget
Fælles repo er KUN til fælles.

Lav ny branch for hvert push. 
Push på den nye branch og lav en pull request
De andre medlemmer godkender mergen (Man pusher aldrig selv sine egne ændringer til main).
Efter merge - slet branch.
Slet branchen lokalt (Det medlem der lavede en pull request.)
Husk at pulle fra main branchen.

Navnekonventioner til commitbeskeder:https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13
