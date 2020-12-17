# OpenWeatherMap JSON

De OpenWeather data gaf ons de volgende JSON terug:

```text
{'coord': {'lon': 4.89, 'lat': 52.37}, 'weather': [{'id': 800, 'main': 'Clear', 'description': 'clear sky', 'icon': '01n'}], 'base': 'stations', 'main': {'temp': 9.36, 'feels_like': 4.39, 'temp_min': 8.89, 'temp_max': 10, 'pressure': 1011, 'humidity': 87}, 'visibility': 10000, 'wind': {'speed': 6.2, 'deg': 150}, 'clouds': {'all': 0}, 'dt': 1608152920, 'sys': {'type': 1, 'id': 1524, 'country': 'NL', 'sunrise': 1608104718, 'sunset': 1608132436}, 'timezone': 3600, 'id': 2759794, 'name': 'Amsterdam', 'cod': 200}
```

Zo'n lange string op één regel is natuurlijk niet handig. Je zou met een JSON viewer op het internet het formaat wat leesbaarder kunnen maken. Voor een handige JSON viewer, zie [http://jsonviewer.stack.hu/](http://jsonviewer.stack.hu/)

**Gebruik:** Plak de JSON string erin en druk op format. Ik krijg dan het volgende te zien:

```javascript
{
  'coord': {
    'lon': 4.89,
    'lat': 52.37
  },
  'weather': [
    {
      'id': 800,
      'main': 'Clear',
      'description': 'clear sky',
      'icon': '01n'
    }
  ],
  'base': 'stations',
  'main': {
    'temp': 9.36,
    'feels_like': 4.39,
    'temp_min': 8.89,
    'temp_max': 10,
    'pressure': 1011,
    'humidity': 87
  },
  'visibility': 10000,
  'wind': {
    'speed': 6.2,
    'deg': 150
  },
  'clouds': {
    'all': 0
  },
  'dt': 1608152920,
  'sys': {
    'type': 1,
    'id': 1524,
    'country': 'NL',
    'sunrise': 1608104718,
    'sunset': 1608132436
  },
  'timezone': 3600,
  'id': 2759794,
  'name': 'Amsterdam',
  'cod': 200
}
```

Willen we nu de windsnelheid printen, dan doen we dat zo:

```python
print(data["wind"]["speed"])
```

## Terug naar ons voorbeeld:

Uiteindelijk gaan we nu een script schrijven waarmee we de volgende gegevens gaan opvragen:

* huidige temperatuur
* de minimum temperatuur
* de maximum temperatuur
* en de luchtvochtigheid

```python
while True:
  req = urllib.request.Request(url)
  resp = urllib.request.urlopen(req).read().decode()

  data = json.loads(resp)

  temp = data["main"]["temp"]
  tempmin = data["main"]["temp_min"]
  tempmax = data["main"]["temp_max"]
  humidity = data["main"]["humidity"]
  name = data["name"]

  # print de data uit
  print("Het is momenteel " + temp + " graden in " + name)
  print("Minimum temperatuur is: " + tempmin)
  print("Maximum temperatuur is: " + tempmax)
  print("Luchtvochtigheid is: " +  humidity + ".")

  # wacht maar een minuut voordat je weer
  # een request doet
  time.sleep(60)
```

We hebben nu een leuk weerstationnetje gemaakt. Maak nu de volgende opdrachten.

## Opdrachten

komt nog

