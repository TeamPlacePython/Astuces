25/09/2023
<h1 align="center">Utiliser une Base de Données Existante avec Django</h1>

Nous le savons tous : lorsqu'on commence un nouveau projet Django, ce n'est pas toujours sur une nouvelle base de données. Parfois, nous avons déjà une base de données remplie de précieuses informations. Comment faire pour que Django travaille avec cette base, sans la reconstruire de zéro ?

## 1. Utiliser la commande inspectdb :

Django offre un outil formidable pour ce cas précis : la commande `inspectdb`. Cet outil génère automatiquement des modèles Django à partir de la structure d'une base de données existante.

Pour commencer, assurez-vous d'avoir correctement configuré la connexion à votre base de données dans le fichier `settings.py` de votre projet Django.

## 2. Générer les modèles :

Une fois la connexion établie, ouvrez votre terminal et tapez la commande suivante :

```python
python manage.py inspectdb
```


Cette commande affichera les modèles générés à l'écran. Pour les sauvegarder directement dans un fichier, par exemple `models.py`, utilisez :

```python
python manage.py inspectdb > nom_de_votre_application/models.py
```

## 3. Ajuster les modèles (si nécessaire) :

L'outil `inspectdb` est intelligent, mais il n'est pas parfait. Il se peut qu'il ne détecte pas toutes les relations ou les spécificités de votre base de données. Prenez donc un moment pour parcourir les modèles générés, ajuster les noms, ajouter des métadonnées ou des relations manquantes.

## 4. Laissez Django gérer la suite :

Maintenant que vous avez vos modèles, vous pouvez utiliser toutes les fonctionnalités ORM de Django pour interagir avec votre base de données, comme les requêtes, les migrations et bien plus encore.

Par défaut, `inspectdb` crée des modèles qui ne sont pas gérés par Django. C’est-à-dire que la présence de `managed = False` dans la classe `Meta` des modèles indique à Django de ne pas superviser la création de la table correspondante, ni sa modification ultérieure ou sa destruction. Voici un exemple fictif de modèle qui aurait pu être généré par la commande `inspectdb` :

```python
class Product(models.Model):
    id = models.IntegerField(primary_key=True)
    name = models.CharField(max_length=70)
    description = models.TextField()

    class Meta:
        managed = False
        db_table = "products"
```

Si vous voulez autoriser Django les tables suite aux modifications futures de ce module, vous pouvez modifier l’option managed mise pour lui donner la valeur True (ou carrément l’enlever, car True est sa valeur par défaut).

N'attendez pas pour intégrer vos bases de données existantes dans vos projets Django. L'outil inspectdb est là pour vous faciliter la tâche. Lancez-vous, et découvrez la puissance combinée de Django et de vos données existantes !