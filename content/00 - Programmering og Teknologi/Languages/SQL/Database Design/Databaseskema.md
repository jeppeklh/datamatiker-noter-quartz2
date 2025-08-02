tags: #Programmering #SQL

> [!tldr] Definition
> En samling af [[Relationsskema|relationsskemaerne]] i [[Repo/06 - Litteratur/Programmering/Database|databasen]].
> Bruges til at lave [[Databasemodel]]

---

## Example
![[Domænemodel Eksempel (Database design).png]]
Det relationelle databaseskema for eksemplet med tilstedeværelse i undervisningen er netop samlingen af dets [[Relationsskema|relationsskemaer]] (her er alle valgt):

SEMESTER (<u>SemesterId</u>, Number)  
SUBJECT (<u>SubjectId</u>, Title, <span class="red">*SemesterId*</span>)  
PARTICIPANT (<u>Email</u>, FirstName, LastName, ImagePath, <span class="red">*SemesterId*</span>)  
LESSON (<u>LessonId</u>, Date, <span class="red">*SubjectId*</span>)  
PARTICIPANT_LESSON (<span class="red"><u>*Email*</u></span>, <span class="red"><u>*LessonId*</u></span>)  
TEACHER (<span class="red"><u>*Email*</u></span>, <span class="red">*SubjectId*</span>)  
STUDENT (<span class="red"><u>*Email*</u></span>, Badge)

---

## Huskeregler??
Lav altid en ID [[PRIMARY KEY|Primary key]] ([[Surrogatnøgle]]) fremfor en [[Composite key|sammensat nøgle]] hvis det kan lade sige gøre.
[[Composite key|Sammensat nøgle]] bliver næsten kun brugt i en mange til mange relation hvor der oprettes et nyt [[Table|table]].

Man Refaktorer [[Design Class Diagram|DCD]] efter Relationelt databaseskema.

---

## Related Topics
- Link
- 

---

## Resources
- Link
- 