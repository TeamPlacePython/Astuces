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