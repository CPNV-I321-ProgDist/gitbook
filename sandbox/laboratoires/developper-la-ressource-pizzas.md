# Développer la ressource "Pizzas"

## Intention

Afin de vous permettre de découvrir le code récupéré dans l'étape précédante, vous devez modifier la solution existante afin d'obtenir une API gérant des pizzas, et non des produits.

En parcourant l'architecture, idéalement en partant du "server.js" puis en déroulant la logique d'appel (route, controller, entities) sans omettre les documents tels que le README ainsi que le contenu présent dans "docs", remplacer les références à "producuts" par "pizzas".

## Objectif

* [ ] Ouvrez une nouvelle branche du nom de "feature/pizzas" comme suit:

```
git flow feature start pizzas
```

* [ ] Parcourez le code est modifié les références nécessaires
* [ ] Adaptez l'entité Produit afin d'obtenir un modèle compatible avec les Pizzas (voir Etape01)

{% hint style="warning" %}
Questionnez-vous également sur les attributs, le sens métier et adapter le code en fonction.
{% endhint %}

### Voici le résultat à obtenir

```bash
curl localhost:3000/api/pizzas | jq
```

{% code fullWidth="true" %}
```json
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   630  100   630    0     0  16411      0 --:--:-- --:--:-- --:--:-- 16578
[
  {
    "id": 3,
    "name": "4 Saisons",
    "ingredients": "Jambon, champignons frais, poivrons, artichauts, mozzarella",
    "imageUrl": "",
    "price": 17,
    "created_at": "2025-09-09 08:26:21",
    "updated_at": "2025-09-09 08:26:21"
  },
  {
    "id": 2,
    "name": "Margherita",
    "ingredients": "Mozzarella",
    "imageUrl": "",
    "price": 12,
    "created_at": "2025-09-09 08:26:21",
    "updated_at": "2025-09-09 08:26:21"
  },
  {
    "id": 1,
    "name": "Pizza du moment",
    "ingredients": "Sauce de tomates jaunes, bresaola, copeaux de parmesan, rucola, tomates cerises, mozzarella fior di latte.",
    "imageUrl": "https://picsum.photos/200?1",
    "price": 20,
    "created_at": "2025-09-09 08:26:21",
    "updated_at": "2025-09-09 08:26:21"
  }
]
```
{% endcode %}
