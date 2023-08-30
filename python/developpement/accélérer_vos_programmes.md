11/07/2023

<h1 align="center">Accélérer vos Programmes avec concurrent.futures</h1>

Si vous avez déjà souhaité que votre code Python puisse exécuter plusieurs tâches en même temps, ou si vous avez dû gérer plusieurs tâches pouvant être exécutées en parallèle, vous serez ravi de découvrir `concurrent.futures`. Ce module Python offre une interface de haut niveau pour gérer la programmation parallèle et concurrente, simplifiant ainsi l'exécution simultanée de fonctions.

**ThreadPoolExecutor vs ProcessPoolExecutor**

Dans `concurrent.futures`, vous avez deux types d'exécuteurs principaux : `ThreadPoolExecutor` et `ProcessPoolExecutor`. Le choix entre les deux dépend du type de tâches que vous effectuez :

- Si vos tâches sont limitées par les entrées/sorties (IO bound), comme le téléchargement de fichiers, l'envoi de requêtes HTTP, ou la lecture/écriture de fichiers, utilisez `ThreadPoolExecutor`. Les threads dans un même processus partagent la même mémoire, ce qui réduit les coûts de création et de destruction des threads.

- Si vos tâches sont limitées par le CPU (CPU bound), comme les calculs intensifs, utilisez `ProcessPoolExecutor`. Chaque processus fonctionne sur un cœur de CPU séparé, permettant ainsi une véritable parallélisation des calculs.

**Comment Utiliser concurrent.futures**

Voici un exemple de code qui utilise `concurrent.futures` pour télécharger plusieurs sites web en parallèle :

```python
from concurrent.futures import ThreadPoolExecutor

import requests

sites = ["https://www.google.com", "https://www.bing.com", "https://www.duckduckgo.com"]

def download_site(url):
    response = requests.get(url)
    # N'oubliez pas de gérer les erreurs ici
    return response.content

with ThreadPoolExecutor() as executor:
    content = executor.map(download_site, sites)

# Le contenu de chaque site est maintenant téléchargé en parallèle !
```

**En Résumé**

`concurrent.futures` est un outil puissant pour gérer la programmation concurrente et parallèle en Python. En comprenant la différence entre les tâches limitées par les entrées/sorties et celles limitées par le CPU, vous pouvez optimiser votre code pour une exécution plus rapide et plus efficace.

Alors, pourquoi ne pas essayer dès maintenant ? Prenez un code que vous avez récemment écrit, identifiez une tâche qui pourrait être parallélisée, et voyez comment `concurrent.futures` peut accélérer son exécution. Vous serez étonné de la différence que cela peut faire !