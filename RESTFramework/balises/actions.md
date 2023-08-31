17/08/2023

<h1 align="center">Ajouter des Actions Personnalisées aux API avec Django Rest Framework (@action)</h1>

Vous avez déjà créé des API CRUD (Créer, Lire, Mettre à jour, Supprimer) avec Django Rest Framework (DRF), n'est-ce pas ? Mais comment ajouter des actions personnalisées qui ne rentrent pas dans ces opérations classiques ?

Heureusement, DRF nous offre une manière élégante de le faire grâce à la décoration `@action`.

Imaginons que vous ayez un viewset pour gérer des profils d'utilisateurs. Outre les opérations CRUD, vous voulez donner la possibilité d'activer un profil en un clic. Cette opération n'est ni une mise à jour classique ni une autre opération CRUD.

Voici comment faire :

```python
from rest_framework.decorators import action
from rest_framework.response import Response

class ProfilViewSet(viewsets.ModelViewSet):

    @action(detail=True, methods=['post'])
    def activer(self, request, pk=None):
        profil = self.get_object()
        profil.actif = True
        profil.save()
        return Response({'status': 'Profil activé'})
```

Dans cet exemple, la méthode activer est définie comme une action personnalisée sur le viewset. L'URL pour cette action serait quelque chose comme /profils/{id}/activer/.

## À retenir :

L'argument detail=True signifie que cette action s'applique à un objet spécifique et non à la liste entière.
methods=['post'] définit la méthode HTTP pour cette action.
N'ayez pas peur de sortir des sentiers battus des opérations CRUD classiques. Expérimentez avec @action pour rendre vos API plus expressives et puissantes. Vous avez le pouvoir de personnaliser vos endpoints selon les besoins de votre application, alors profitez-en !

__________

04/09/2023

<h1 align="center">TWITTER</h1>

**Question (Matin)**
"Vous avez déjà créé des API CRUD avec Django Rest Framework (DRF). Mais comment ajouter des actions personnalisées qui ne rentrent pas dans ces opérations classiques ? 🤔

**Indice (Midi)**
"Découvrez comment étendre les fonctionnalités de vos API DRF grâce à la décoration @action ! 🚀

**Astuce (Après-midi) - Chapitre 1/3**
"🔍 Actions Personnalisées avec @action in DRF 🔍"
"Si vous voulez ajouter des fonctionnalités personnalisées aux API DRF, @action est là pour vous ! Dans cet exemple, nous explorerons comment activer un profil d'utilisateur en un clic."

**Astuce (Soir) - Chapitre 2/3**
"📝 Détail=True et Méthodes HTTP 📝"
"L'argument detail=True signifie que l'action s'applique à un objet spécifique, pas à la liste entière. Avec methods=['post'], nous spécifions la méthode HTTP utilisée pour cette action. Une flexibilité puissante pour des fonctionnalités sur mesure !"

**Astuce (Nuit) - Chapitre 3/3**
"🛠️ Mise en Pratique 🛠️"
"Dans l'exemple, nous avons créé une action 'activer' pour les profils d'utilisateurs. Elle permet d'activer un profil en un clic. Expérimentez avec @action pour personnaliser vos endpoints et rendre vos API plus expressives et puissantes ! 💪🌟
