# Een GraphQL client in Python

Wil je in Python een GraphQL API gebruiken, dan is dat vrij eenvoudig.

Allereerst installeer je de library GQL \([https://github.com/graphql-python/gql](https://github.com/graphql-python/gql)\). Dat kun je doen met het volgende commando:

```text
pip install gql==3.0.0a2
```

{% hint style="info" %}
Als je repl.it gebruikt, dan worden libraries automatisch voor je geïnstalleerd. Echter wordt in dit geval de verkeerde versie geïnstalleerd. Met behulp van het bovenstaande commando kun je alsnog de juiste versie \(achteraf\) installeren.
{% endhint %}

## Stap 1

* Importeer de benodigde libraries
* Maak een transport object aan en stel daar de endpoint in naar de GraphQL API
* Maak vervolgens een client object aan.

```python
# we hebben drie objecten nodig: gql, Client en AIOHTTPTransport
from gql import gql, Client
from gql.transport.aiohttp import AIOHTTPTransport


# nu moeten we de GraphQL endpoint aangeven
transport = AIOHTTPTransport(url="https://www.badgecraft.eu/api/graphql")

# Create a GraphQL client using the defined transport
client = Client(transport=transport, fetch_schema_from_transport=True)
```

We maken vervolgens een GraphQL query waarmee we alle namen van de StarWars karakters gaan ophalen.

```python
# Pwe maken een graphql query
query = gql(
    """
    query {
    	allPeople{
        people {
          name
        }
      }
    }
""")
```

Nu vuren we de query af op de API en bewaren het resultaat in result. Met een loop doorlopen we de dictionary met personen. We printen de namen uit:

```python
# Execute the query on the transport
result = client.execute(query)
for person in result["allPeople"]["people"]:
  print(person["name"])
```

De gehele code nog even in een keer:

```python
from gql import gql, Client
from gql.transport.aiohttp import AIOHTTPTransport

# Select your transport with a defined url endpoint
transport = AIOHTTPTransport(url="https://swapi-graphql.netlify.app/.netlify/functions/index")

# Create a GraphQL client using the defined transport
client = Client(transport=transport, fetch_schema_from_transport=True)

# Provide a GraphQL query
query = gql(
    """
  query {
	  allPeople{
      people {
        name
      }
    }
  }
""")

# Execute the query on the transport
result = client.execute(query)
for person in result["allPeople"]["people"]:
  print(person["name"])
```

**Opdracht**

Maak een programma waarmee je de queries die je in de vorige paragraaf in de Playground hebt getest nu ook vanuit Python aanroept. Bedenk goed wat je op het scherm wilt printen. Maak er iets moois van!

