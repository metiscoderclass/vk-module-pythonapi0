# De Weather API

## Het verschil

Tijdens de vorige les hebben we een API gebruikt waar je _geen_ ApiKey voor nodig had. Nu gaan we met een API werken waar je dat _wel_ nodig gaat hebben.

## OpenWeatherMap

De API die we nu gaan gebruiken is de OpenWeatherMap \(OWM\). Het is gratis te gebruiken voor als je de huidige informatie over het weer wil hebben.

Allereerst moeten we naar de website van OWM gaan. Je kunt bovenaan de pagina op de Sign Up knop drukken om een account aan te maken. Zodra je dat hebt gedaan ga je naar de tab API keys. Daar zie je een lange key met cijfers en letters: het is een supergroot hexadecimaal getal! Dat is de ApiKey die je nodig hebt!

Laten we nu deze key veilig opslaan.

## ApiKey, geheim? Waarom?

Waarom moeten ApiKey's eigenlijk geheim blijven? Omdat deze keys zijn gekoppeld aan jouw account. Als er dus misbruik wordt gemaakt van deze keys dan loop je kans dat jouw account wordt geblokkeerd. En dat willen we natuurlijk niet hebben!

Hiervoor gebruiken we een bestand met de naam `.env`. Daar zetten we dan de ApiKey in en vanuit de code lezen we deze key uit dit bestand.

Dus:

* Maak een bestand in je project en noem hem .env
* Zet vervolgens in dat bestand de regel: `APIKEY=(jouw api key)`

  Uiteraard moet je `(jouw api key)` vervangen door de key die je van OpenWeatherMap hebt gekregen.

* Sla het bestand op.

Hoe halen we de key op in onze code? Hiervoor gebruiken we de os module.

```python
import os
# haal de apikey uit het .env bestand
apikey = os.environ["APIKEY"]
# we printen de key om te checken om het is gelukt
print(apikey)
```

Nu kunnen we aan de slag gaan!

## Let's Do This!

Laten we allereerst de benodigde modulen importeren:

```python
import urllib.request
import json
import os
import time
```

Nu halen we de ApiKey uit de `.env` file en plakken het vast aan de url \(endpoint\).

```python
apikey = os.environ["APIKEY"]

url = "https://api.openweathermap.org/data/2.5/weather?"
# Voeg de api key toe aan de URL (endpoint)
url += "APPID=" + apikey
# nu voegen we wat extra opties toe
url += "&units=metric&&q=Amsterdam"
```

En nu kunnen we via de samengestelde url de data gaan opvragen.

```python
# haal de data op met een request
req = urllib.request.Request(url)
resp = urllib.request.urlopen(req).read().decode()

# lees de JSON data in de variabele data
data = json.loads(resp)
print(data)
```

Als het goed is zul je nu data uitgeprint krijgen. Het lijkt een beetje op het onderstaande:

```javascript
{'coord': {'lon': 4.89, 'lat': 52.37}, 'weather': [{'id': 800, 'main': 'Clear', 'description': 'clear sky', 'icon': '01n'}], 'base': 'stations', 'main': {'temp': 9.36, 'feels_like': 4.39, 'temp_min': 8.89, 'temp_max': 10, 'pressure': 1011, 'humidity': 87}, 'visibility': 10000, 'wind': {'speed': 6.2, 'deg': 150}, 'clouds': {'all': 0}, 'dt': 1608152920, 'sys': {'type': 1, 'id': 1524, 'country': 'NL', 'sunrise': 1608104718, 'sunset': 1608132436}, 'timezone': 3600, 'id': 2759794, 'name': 'Amsterdam', 'cod': 200}
```

Dit is het welbekende JSON-formaat. In paragraaf 2.1 zullen we je uitleggen hoe het werkt en waar het goed voor is.

Voor de volledigheid, hier nog de hele code in de onderstaande repl. Vergeet niet je eigen `ApiKey` in het `.env` bestand te zetten als je de code wilt testen:

{% embed url="https://repl.it/@hakkas/OpenWeatherVoorbeeld?lite=true" %}







