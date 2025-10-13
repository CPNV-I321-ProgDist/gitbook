# Développer la ressource "Ingredients"

## Intention

En appliquant le même processus utilisé pour l'implémentation de la ressource "Pizzas", ajouter la ressource "Ingredients" à votre projet.

En parcourant l'architecture, idéalement en partant du "server.js" puis en déroulant la logique d'appel (route, controller, entities) sans omettre les documents tels que le README ainsi que le contenu présent dans "docs", ajouter la nouvelle ressource.

## Objectif

* [ ] Ouvrez une nouvelle branche du nom de "feature/ingredients" comme suit:

```
git flow feature start ingredients
```

* [ ] Couche par couche, ajouter le code nécessaire pour la nouvelle ressource.

{% hint style="warning" %}
Pour l'instant, vous ne devez pas lier la logique "Pizzas" avec celle d'"Ingredients". Nous le ferons dans la prochaine étape.
{% endhint %}

### Voici le résultat à obtenir

<figure><img src="../../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

```bash
curl localhost:3000/api/ingredients | jq
```

{% code fullWidth="true" %}
```json
   % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   995  100   995    0     0  73431      0 --:--:-- --:--:-- --:--:-- 76538
[
  {
    "id": 5,
    "name": "Lardons",
    "price": 2,
    "created_at": "2025-09-15 20:31:56",
    "updated_at": "2025-09-15 20:31:56"                                                                                                                                                                    
  },
  {
    "id": 4,
    "name": "Jambon",
    "price": 2,
    "created_at": "2025-09-15 20:31:50",
    "updated_at": "2025-09-15 20:31:50"                                                                                                                                                                    
  },
  {
    "id": 3,
    "name": "Oignons",
    "price": 1,
    "created_at": "2025-09-15 20:31:32",
    "updated_at": "2025-09-15 20:31:32"                                                                                                                                                                    
  },
  {
    "id": 2,
    "name": "Champignons",
    "price": 1,
    "created_at": "2025-09-15 20:31:17",
    "updated_at": "2025-09-15 20:31:17"                                                                                                                                                                    
  }
]

```
{% endcode %}
