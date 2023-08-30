10/08/2023

<h1 align="center">Trouver les Éléments les Plus Courants dans une Séquence avec collections.Counter.most_common()</h1>

Lorsque vous avez une séquence (comme une liste) et que vous voulez rapidement identifier les éléments les plus fréquents ainsi que leur fréquence d'occurrence, la bibliothèque `collections` de Python offre une solution puissante : `Counter`. Utilisez la méthode `most_common(n)` de `Counter` pour obtenir les `n` éléments les plus courants avec leur nombre d'occurrences.

```python
from collections import Counter

ma_liste = [1, 2, 3, 2, 2, 3, 4, 5, 3, 1]
compteur = Counter(ma_liste)

# Obtenir les 3 éléments les plus courants :
top_trois = compteur.most_common(3)
print(top_trois)  # Résultat : [(2, 3), (3, 3), (1, 2)]
```

Cette technique est un moyen rapide et efficace d'analyser la fréquence des éléments dans une séquence. L'utilisation de `collections.Counter` est un excellent exemple de la facilité avec laquelle Python permet de résoudre des problèmes courants de programmation.