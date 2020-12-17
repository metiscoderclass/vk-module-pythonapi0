# Python en JSON
Nu je weet wat JSON is en hoe het werkt, wordt het tijd om te kijken hoe je met de programmeertaal Python JSON objecten kunt gebruiken. Zoals je vanuit de afkorting al hebt kunt afleiden is JSON eigenlijk gebaseerd op JavaScript. Maar toch kunnen we het in elke programmeertaal gebruiken. Zo ook in Python.

Allereerst moeten we de library json importeren:

```python
import json
```

Als we nu een string hebben met daarin json, dan moeten we dat omzetten naar een echt json object. En dat is Python dan gewoon een dictionary. Dit omzetten doen we met de functie ```json.loads()```. Voorbeeld:

```python
import json

json_string = '''
{  
  "first_name"  : "Henk",
  "last_name"   : "Shark",
  "online"      : true,
  "age"         : 20
}
'''

object_person = json.loads(json_string)
```

De variabele object_person is nu een dictionary. Hij bevat 4 keys, te weten:
* first_name
* last_name
* online
* age

Met de module Python-3 heb je geleerd hoe je dictionaries kan gebruiken. We printen de voornaam en achternaam uit:

<iframe height="500px" width="100%" src="https://repl.it/@hakkas/JSON-voorbeeld?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>

Laten we nu een iets complexer JSON string nemen. Eentje met een ander object als value.

Schematisch ziet dat er zo uit:
<img src="https://docs.google.com/drawings/d/e/2PACX-1vTP2wfgPzvzD798-G8AFsnpHi-K7qVQhv62Gy4ocyzzJHylOFe7vJYrH7DfpSH_FtKybp0TmPm-TSlV/pub?w=679&amp;h=382">

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
Willen we nu de straatnaam printen, dan doen we dat zo:

```Python
print("Straatnaam: " + object_person["address"]["street"])
```

Je hebt dus een dictionary _in_ een dictionary.

En nu een JSON object met een array erin. Arrays worden omgezet naar Python lijsten. Kijk goed naar het onderstaande voorbeeld:

<iframe height="400px" width="100%" src="https://repl.it/@hakkas/JSON-voorbeeld-3?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>
