12/07/2023

<h1 align="center">Gérer les Tâches Web en Python avec urllib.parse et urllib.request</h1>

Si vous êtes fatigué de gérer des dépendances supplémentaires comme "requests" pour effectuer des tâches web simples en Python, ou si vous recherchez une solution légère et efficace, alors cet article est fait pour vous ! Les modules `urllib.parse` et `urllib.request` de la bibliothèque standard Python vous offrent de nombreuses fonctionnalités similaires à celles de "requests", sans nécessiter d'installation supplémentaire.

**Effectuer une Requête GET avec urllib.request**

Pas besoin d'installer quoi que ce soit de plus, `urllib.request` est tout ce dont vous avez besoin pour effectuer une requête GET simple :

```python
import urllib.request

response = urllib.request.urlopen('https://www.example.com')
print(response.read())
```

**Passer des Paramètres dans une Requête GET**

Avec `urllib.parse`, vous pouvez facilement construire des URLs avec des paramètres de requête :

```python
import urllib.parse
import urllib.request

params = urllib.parse.urlencode({'param1': 'value1', 'param2': 'value2'})
url = 'https://www.example.com?' + params
response = urllib.request.urlopen(url)
print(response.read())
```

**Effectuer une Requête POST avec urllib.request**

Si vous avez besoin de faire une requête POST, `urllib.request` peut aussi vous aider :

```python
import urllib.parse
import urllib.request

data = urllib.parse.urlencode({'param1': 'value1', 'param2': 'value2'}).encode()
url = 'https://www.example.com'
req = urllib.request.Request(url, data=data)  # Requête POST
response = urllib.request.urlopen(req)
print(response.read())
```

**En Conclusion**

Si vous trouvez que gérer des dépendances supplémentaires pour les tâches web en Python est une contrainte, essayez `urllib.parse` et `urllib.request`. Ces modules de la bibliothèque standard offrent une grande partie des fonctionnalités de "requests", sans nécessiter d'installation supplémentaire.

Pourquoi ne pas essayer dès maintenant ? Remplacez vos appels à "requests" par des appels à `urllib.request` et découvrez à quel point il est facile de simplifier vos dépendances en Python.