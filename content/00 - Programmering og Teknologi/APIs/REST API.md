### Hvad er REST?
---
> [!tldr] Definition
Et designkoncept og programmeringsparadigme bygget på HTTP. Det bruger eksisterende infrastruktur til at få adgang til resourcer via [[URI]]s og manipulere dem med HTTP metoder/operationer
Se [[REST API]]

## En Rest API HTTP request består af 
---
**Header**
Indeholder ting som API-key eller anden authentificerings

**Operation**
POST, GET, PUT, eller DELETE

**Endpoint**
`http://website.com/API/endpoint1`

**Body**
Data man ville sende i en request
i en PUT request kunne man ændre en is-smag til chokolade
```json
{"flavor" : "chokolade"}
```


## Grundlæggende principper i REST:
---
#### **Ressourceorienteret:**  
Ressourcer (fx produkter, brugere) repræsenteres som entydige URL'er. Navngivning skal primært baseres på navneord, ikke verber.

#### **HTTP-metoder**
Rest bruger HTTP metoder til at lave operationer på resourcer

| HTTP Verb | Function             |
| --------- | -------------------- |
| GET       | Read data            |
| POST      | Create new data      |
| PUT       | Update existing data |
| DELETE    | Delete existing data |
Nogle applikationer bruger også `POST` til at lave ny data, fordi `GET` og `POST` er tilgængelige overalt

#### **Stateless:**  
Hver forespørgsel fra klienten skal indeholde al nødvendig information, så serveren ikke behøver at huske tidligere interaktioner.

#### **Brug af standard statuskoder:**  
API'et returnerer statuskoder (fx 200 OK, 404 Not Found, 201 Created) for at indikere resultatet af en operation.

## Eksempel på RESTful URI-design
---

**Liste af produkter:**
```
GET https://api.hplussport.com/products
```

Returnerer en liste over produkter.

**Hent et specifikt produkt:**
```
GET https://api.hplussport.com/products/123
```

Returnerer produktet med ID 123.

**Opdater et produkt:**
```
PUT https://api.hplussport.com/products/123
```
Opdaterer data for produktet med ID 123.

**Slet et produkt:**
```
DELETE https://api.hplussport.com/products/123
```
Sletter produktet med ID 123.


## Contraints
---
RESTful APIs skal overholde 6 contraints
- Uniform interface
	En URI pr resource med et uniformt look.
- [[Client-Server Arkitektur]]
- Statelessnes
	HTTP (Hvor REST kommer fra) er stateless, så det skal REST APIs også være 
- Cacheability
- Layered system
- Code on demand (Optional)



## Sammenfatning
---
REST API-design handler om at skabe enkle, intuitive og konsistente grænseflader, hvor ressourcer er klart definerede og manipulation af disse sker via de velkendte HTTP-metoder.

## Resourcer
---
- [REST LinkedIn Learning](https://www.linkedin.com/learning/building-web-apis-with-asp-dot-net-core-in-dot-net/rest-basics?autoSkip=true&resume=false&u=57075649)