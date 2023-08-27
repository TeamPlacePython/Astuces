19/08/2023

<h1 align="center">Afficher un Élément Aléatoire avec le Filtre "random" dans les Templates Django</h1>

Lorsque vous développez une application Django, vous avez parfois besoin d'afficher un élément de manière aléatoire parmi un ensemble. Par exemple, imaginez que vous ayez un site de recettes de cuisine et que vous souhaitiez proposer chaque jour une recette aléatoire en page d'accueil.

Django offre un filtre template très pratique pour cela : `random`. Ce filtre permet de sélectionner un élément au hasard dans une liste.

Supposons que vous ayez un modèle `Recette` et que vous vouliez afficher une recette aléatoire.

Dans votre vue :

```python
from django.shortcuts import render
from .models import Recette

def recette_du_jour(request):
    recettes = Recette.objects.all()
    return render(request, 'recette_du_jour.html', {'recettes': recettes})
```
Dans votre template recette_du_jour.html :

```django
{% if recettes %}
    <h2>Recette du jour</h2>
    <p>{{ recettes|random }}</p>
{% else %}
    <p>Désolé, aucune recette disponible pour le moment.</p>
{% endif %}
```

Avec ce code, chaque fois que vous actualisez la page, une recette différente sera (potentiellement) affichée.

Si vous n'avez jamais essayé les filtres de template Django, c'est le moment ! Ils simplifient beaucoup de tâches courantes. Intégrez le filtre random dans votre projet et voyez par vous-même la magie de Django en action. Et rappelez-vous : chaque petit outil que vous apprenez vous rapproche de devenir un maître de Django. Courage !