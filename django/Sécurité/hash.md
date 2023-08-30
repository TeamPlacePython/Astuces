08/08/2023

<h1 align="center">Ajout de Hash à vos Fichiers Statiques avec Django-Compressor</h1>

**Le Problème :**

Lors du développement d'un site web, les fichiers statiques (comme les fichiers CSS et JavaScript) sont souvent modifiés. Cependant, les navigateurs mettent en cache ces fichiers pour accélérer le chargement des pages. Cela peut poser problème : les utilisateurs pourraient voir l'ancienne version des fichiers à cause du cache du navigateur.

**La Solution : django-compressor**

`django-compressor` est un outil puissant qui permet de compresser les fichiers statiques et d'ajouter un hash unique à leur nom. Lorsque le contenu d'un fichier change, le hash change également, forçant ainsi les navigateurs à télécharger la nouvelle version du fichier.

**Comment Faire :**

1. **Installation :** Commencez par installer `django-compressor` avec pipenv ou votre outil préféré :

   ```bash
   pipenv install django-compressor
   ```

2. **Configuration :** Ajoutez `'compressor'` à votre liste `INSTALLED_APPS` dans `settings.py` :

   ```python
   INSTALLED_APPS = [
       ...
       'compressor',
       ...
   ]
   ```

3. **Utilisation dans les Templates :** Encadrez vos fichiers statiques avec les balises `{% compress 'type' %}` et `{% endcompress %}`. Par exemple, pour du CSS :

   ```html
   {% load compress %}
   {% compress css %}
   <link rel="stylesheet" href="{% static 'css/mon_fichier.css' %}">
   {% endcompress %}
   ```

4. **Configuration de la Compression :** Toujours dans `settings.py`, ajoutez :

   ```python
   COMPRESS_ENABLED = True
   ```

C'est tout ! Maintenant, chaque fois que vous modifierez votre fichier CSS (ou JavaScript), `django-compressor` générera un nouveau hash pour le fichier, assurant que vos utilisateurs voient toujours la dernière version.

**En Conclusion :**

La mise en cache est excellente pour les performances, mais peut causer des problèmes lors des mises à jour. Avec `django-compressor`, vous avez une solution élégante pour garantir que vos utilisateurs bénéficient toujours des dernières améliorations. Intégrez `django-compressor` dès aujourd'hui et offrez à vos utilisateurs la meilleure expérience possible !