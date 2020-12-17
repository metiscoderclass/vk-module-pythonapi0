# De Wikipedia API

## Wikipedia

We beginnen met de Wikipedia API. Dit is een leuke API, want Wikipedia heeft een interessante, grote database aan informatie waar we dankbaar gebruik van kunnen maken.

## Modules

* Als je wilt werken met turtle, dan moet je turtle importeren.
* Als je wilt werken met random, dan moet je random importeren.

Als je tegen een API wilt praten, dan heb je een module nodig die je moet importeren aan het begin van je code: `requests`

De module requests hebben we nodig om de Web-API aan te roepen. En de data te verkrijgen.

Om hem te importeren, doen we dit:

```python
import requests
```

\(Als je Python op je lokale machine draait, dan moet je deze library eerst installeren. Doe dat door `pip3 install requests` in te typen in je terminal\). In repl.it hoeft dit niet, want het gebeurt automatisch.

## URL

We moeten dus de data via de API gaan ophalen.

Laten we beginnen met een voorbeeld waarbij je als gebruiker invoert wat je wilt zoeken. Op basis daarvan wordt een url samengesteld.

```python
# Vraag de gebruiker om een zoekterm
search = input("Geef een zoekterm: ")
# We plakken deze zoekterm aan de API-url
url = "https://en.wikipedia.org/w/api.php?action=opensearch&limit=1&format=json&search=" + search
```

We vragen dus eerst om een zoekwoord. Vervolgens plakken we dat aan een URL. Maar laten we dit URL wat nader bekijken:

De basis van het bovenstaande URL is: [https://en.wikipedia.org/w/api.php](https://en.wikipedia.org/w/api.php) Deze basis noemen we een _endpoint_. Een endpoint is de plek waar je API calls kunt doen. Het is een communicatiekanaal. Via dit kanaal vraag je iets op \(request\) en via dit kanaal krijg je antwoord \(response\). Vervolgens kun je met parameters allerlei waarden en instellingen meegegeven. Die parameters staan achter het vraagteken en elke parameter wordt onderscheiden door een &. Hierboven heb je dus 4 parameters:

* action = opensearch: we doen een vrije zoekopdracht
* limit = 1: we geven aan dat we maximaal 1 resultaat willen
* format = JSON: het formaat van het antwoord willen we json
* search = : ten slotte willen we dat hij zoekt op jouw zoekterm

Deze hele URL \([https://en.wikipedia.org/w/api.php?action=opensearch&limit=1&format=json&search=iets](https://en.wikipedia.org/w/api.php?action=opensearch&limit=1&format=json&search=iets)\) noem je dus ook een query: Je vraagt de API of hij antwoord wil geven op jouw vraag.

## Request Data

We kunnen nu de URL gebruiken om de data van de API op te vragen. Dit doen we met:

```python
response = requests.get(url)
```

## Reading JSON

JSON is het formaat dat gebruikt wordt om gegevens heen-en-weer te versturen. JSON staat voor _JavaScript Object Notation_. Zoals de naam ook al doet vermoeden is dit formaat vooral gebaseerd op JavaScript objecten. Maar ook in andere programmeertalen kunnen we gewoon werken met JSON. Zoals in het plaatje hieronder ook te zien is geeft de server het resultaat van je zoekopdracht terug in het JSON formaat.

![JSON als communicatietaal client server](.gitbook/assets/client%20server%20%283%29.png)

In Python worden deze JSON structuren omgezet naar lijsten en dictionaries.

```python
# The we can load the json received from the response
data = response.json()
# Print the data to view it
print(data)
```

Dit was je eerste kennismaking met een API. Maak nu opdracht 1 in repl.it. Zie:

