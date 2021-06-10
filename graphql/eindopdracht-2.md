# De BadgeCraft API

In deze eindopdracht ga je iets leuks doen! Je gaat namelijk je badges uit BadgeCraft halen. BadgeCraft biedt namelijk een GraphQL API die je zo kunt gebruiken. Er zijn wel een aantal bijzonderheden.

Kort samengevat komt het op het volgende neer:

1. Voor de BadgeCraft API moet je je **authenticeren** met je gebruikersnaam en wachtwoord die je voor BadgeCraft hebt aangemaakt. 
2. Je krijgt dan een token en dat token moet je meegeven aan de daarop volgende API calls.

{% hint style="warning" %}
**Belangrijk!**

De _**Endpoint**_ voor BadgeCraft is: [https://www.badgecraft.eu/api/graphql](https://www.badgecraft.eu/api/graphql)  
De _**Playground**_ van de BadgeCraft API is: [https://www.badgecraft.eu/api/graphiql](https://www.badgecraft.eu/api/graphiql)
{% endhint %}

**Stap 1**

Stuur eerst de volgende **mutation** query naar BadgeCraft:

```python
query = gql(
    """
  mutation {{
    passwordAuthorize(email:"{0}", password:"{1}") {{
      success,
      token
    }}
  }}
""".format(os.environ['un'], os.environ['pw'])

result = client.execute(query)
```

Zoals je ziet geef ik mijn username en wachtwoord via geheime environment variabelen mee. Dat moet jij ook doen!  
Merk ook op dat ik `string.format` gebruik. Omdat ik dat doe moet ik de **letterlijke** accolades verdubbelen.

**Stap 2**

Als je goed naar de vorige query kijkt, dan krijg je dus twee dingen terug: `success` en `token`.  Met `success` kun je kijken of je query is gelukt en het `token` heb je nodig voor de volgende API calls.

```python
if result["passwordAuthorize"]["success"] == True:
  print("Het is gelukt!")
  # en nu het token bewaren, want die hebben we nodig!
  token = result["passwordAuthorize"]["token"]
```

We maken nu een nieuw `transport` object aan, maar deze keer met headers waarin we het `token` meegeven:

```python
transport = AIOHTTPTransport(
    url='https://www.badgecraft.eu/api/graphql',
    headers={'Auth-Token': token}
)
```

Vervolgens doen we weer hetzelfde: We maken een `client` aan, voeren de query uit en laten het resultaat zien:

```python
client = Client(transport=transport, fetch_schema_from_transport=True)

query = gql("""
query {
  me {
    id
  }
}
""")

# Execute the query on the transport
result = client.execute(query)
print(result)
```

Als het goed is krijg je je BadgeCraft-id te zien.



