# JSON
Het formaat van de data die je terug hebt gekregen van de OpenWeather API heet _JSON_. De afkorting staat voor _JavaScript Object Notation_. Maar waar is dit goed voor?

Als je de gegevens van een programma beschikbaar wilt stellen voor andere programma's, dan moet je een formaat bedenken dat beide programma's ondersteunen en begrijpen.

Voorbeeld: Stel dat ik een programma heb geschreven met een database waarin ik alle voetbalwedstrijden en uitslagen bijhoudt die ooit zijn gespeeld. En stel dat anderen geïnteresseerd zouden zijn in deze gegevens. Dan kan ik middels een API deze gegevens beschikbaar stellen. Maar in welk formaat moet ik die gegevens opsturen?

Vroeger bedachten softwarebedrijven wel eens een eigen formaat. Leuk en aardig, maar als ieder bedrijf zijn eigen formaat bedenkt, dan is dat niet handig.
Men gebruikte ook wel eens het CSV-formaat. CSV staat voor Comma Seperated Value. Een voorbeeld van zo'n bestand:

```CSV
Year,Make,Model
1997,Ford,E350
2000,Mercury,Cougar
```

Zoals de naam zegt: de waarden worden onderscheiden door komma's. Heel handig voor gegevens die je mooi in een tabel kan weergeven. Maar hoe zet je complexere gegevens hierin? Als je bijvoorbeeld hiërarchie wilt aanbrengen in de gegevens. Of je wilt je gegevens beter beschrijven. In dat geval kun je kiezen voor iets nieuwers, iets beters, iets wat veel flexibeler te gebruiken is: _JSON_.

Verreweg de meeste Web API's werken met JSON. Roep je een API methode aan, dan krijg je JSON terug. Zoals ook de OpenWeatherAPI dat doet.

## Beknopte uitleg syntax JSON
Je hebt vier soorten constructies in JSON:
* Je kunt name/value pairs opslaan
* De gegevens worden onderscheiden middels komma's
* Met accolades {} beschrijf je objecten
* Met [] beschrijf je arrays

### Name/Value pairs
We beginnen met het eenvoudigste: Hier een voorbeeld van een name/value pair:
```json
"first_name":"Henk"
```
**LET OP:**
* keys zijn altijd strings (dus met aanhalingstekens)
* de value kan een string zijn

### Key/Value paren in een objecten
Hier maken we een object met daarin meerdere key/value pairs:
```json
{
  "first_name"  : "Henk",
  "last_name"   : "Shark",
  "online"      : true,
  "age"         : 20
}
```
**LET OP:**
* de value kan een string zijn, een (komma)getal of een boolean

### Objecten als values
Je kunt ook andere objecten als value gebruiken:
```json
{
  "first_name"  : "Henk",
  "last_name"   : "Shark",
  "online"      : true,
  "age"         : 20,
  "address"     : {
    "street"        : "Mauritskade",
    "number"        : 58
  }
}
```
Zo breng je hierarchie en nesting aan. Het object address is onderdeel van een ander object. Zo kun je ook objecten in objecten in objecten enzovoorts maken.

### Arrays
Met blokhaken [] maak je arrays/lijsten. Hier een voorbeeld:

```json
[
  {
    "first_name"  : "Henk",
    "last_name"   : "Shark",
    "online"      : true,
    "age"         : 20,
    "address"     : {
      "street"        : "Mauritskade",
      "number"        : 58
    }
  },
  {
    "first_name"  : "Kai",
    "last_name"   : "Kruse",
    "online"      : false,
    "age"         : 14,
    "address"     : {
      "street"        : "Mauritskade",
      "number"        : 54
    }
  },
  {
    "first_name"  : "Jop",
    "last_name"   : "Bergh",
    "online"      : true,
    "age"         : 15,
    "address"     : {
      "street"        : "Mauritskade",
      "number"        : 22
    }
  }
]
```
Nu hebben we dus een lijst van 3 personen.

En je kunt ook arrays als _value_ instellen:
```JSON
{
  "first_names" : ["Henk","Willem", "Sjaak"],
  "last_name"   : "Shark",
  "online"      : true,
  "age"         : 20,
  "address"     : {
    "street"        : "Mauritskade",
    "number"        : 58
  }
}
```
Deze persoon heeft dus drie voornamen.

## JSON kort samengevat:
* JSON staat voor JavaScript Object Notation
* JSON is een lightweight data uitwisselingsformaat
* JSON is zelfbeschrijvend (self-describing) en makkelijk te begrijpen
* JSON is taal en platformonafhankelijk

## Opdrachten
hier komen nog opdrachten
