# Solution

## Diagramme de classes

<figure><img src="../../../../.gitbook/assets/diagram-16493888247746822365.png" alt=""><figcaption></figcaption></figure>

## Modèle logique de données

<figure><img src="../../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

## Séquence de création d'une pizza

<figure><img src="../../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Comment créer une pizza

```json
{
  "name": "Margherita",
  "price": 8.5,
  "ingredientIds": [1, 2, 3]
}
```

Comment récupérer une pizza

```json
{
  "id": 1,
  "name": "Margherita",
  "price": 8.5,
  "ingredients": [
    { "id": 1, "name": "tomato" },
    { "id": 2, "name": "mozzarella" },
    { "id": 3, "name": "basil" }
  ]
}
```

Lien avec la base de données

<figure><img src="../../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
