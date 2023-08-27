20/08/2023

<h1 align="center">Afficher une Portion de Données avec le Filtre "slice" dans les Templates Django</h1>

Lorsque vous travaillez avec des données dans Django, il est courant de vouloir afficher seulement une portion d'une chaîne de caractères ou d'une liste. Par exemple, vous pourriez vouloir montrer seulement les 10 premiers caractères d'une description ou les 5 premiers articles d'une liste.

Django vous offre un filtre très utile pour cela, appelé `slice`. Il fonctionne un peu comme le découpage de listes en Python.

Imaginez que vous avez un blog et que vous voulez afficher seulement les 50 premiers caractères du contenu de chaque article sur la page d'accueil pour donner un aperçu.

```django
{{ article.content|slice:":50" }}...
```

Ou, disons que vous avez une liste d'utilisateurs et que vous voulez n'afficher que les 5 premiers :

```django
{% for user in users|slice:":5" %}
  {{ user.name }}
{% endfor %}
```
Le filtre slice est simple mais très puissant. La prochaine fois que vous avez besoin d'afficher une portion de vos données, n'oubliez pas d'utiliser ce filtre. Faites des essais dans vos templates Django et voyez par vous-même combien il est pratique !