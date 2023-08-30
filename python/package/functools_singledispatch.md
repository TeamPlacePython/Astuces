09/08/2023

<h1 align="center">Utilisation de `singledispatch` pour le Dispatch Simple de Fonctions en Fonction du Type</h1>

Lorsque vous devez exécuter différents morceaux de code en fonction du type d'objet que vous manipulez, plutôt que de recourir à une série de vérifications `isinstance`, la fonction `singledispatch` du module `functools` est votre alliée.

Prenons l'exemple où vous souhaitez formater différents types de données pour affichage :

```python
from functools import singledispatch

@singledispatch
def format_data(arg):
    """Format pour les types non spécifiés"""
    return str(arg)

@format_data.register(str)
def _(arg):
    return f"Chaine : {arg}"

@format_data.register(int)
def _(arg):
    return f"Entier : {arg}"

@format_data.register(list)
def _(arg):
    return f"Liste de {len(arg)} éléments : {arg}"
```

Utilisation :

```python
print(format_data(5))         # "Entier : 5"
print(format_data("Bonjour")) # "Chaine : Bonjour"
print(format_data([1, 2, 3])) # "Liste de 3 éléments : [1, 2, 3]"
```

Avec `singledispatch`, votre code est plus lisible et facilement extensible, comparé à une série de vérifications `isinstance`. Cette astuce améliore la maintenabilité et la lisibilité de votre code, tout en vous permettant d'ajouter de nouvelles implémentations pour d'autres types à tout moment.