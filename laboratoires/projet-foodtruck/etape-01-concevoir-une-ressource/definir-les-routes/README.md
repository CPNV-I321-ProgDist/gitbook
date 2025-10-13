# Définir les routes

## Introduction

Afin de pouvoir gérer, manipuler, modifier notre ressources "pizzas", nous devons disposer de différentes routes.

## Objectif

Mettez en évidence les routes dont nous avons besoin pour permettre à notre pizzaïolo de maintenir à jour sa carte des mets.

### Les fonctionnalités clés

Voici les fonctionnalité à prévoir:

* Lister les pizzas actuellement proposées (solution ci-dessous).
* Afficher une seule pizza.
* Ajouter une nouvelle pizza.
* Mettre à jour une pizza (son prix, ses ingrédients).
* Supprimer une pizza de la carte.

Pour l'instant, nous ne traiterons pas le cas "Définir une pizza comment étant la pizza du moment."

## Les éléments clés à définir pour une route

En étudiant cette capture d'écran, vous pouvez identifier les éléments clés à définir pour ensuite développer une route adaptée à notre besoin.

{% hint style="warning" %}
Faites le lien avec le besoin métier ci-dessous
{% endhint %}

## Exemple de définition de route - Lister les pizzas

Afin de lister les pizzas actuellement proposées, nous avons besoin de réaliser sur la ressource "Pizzas" un get, sans distinction.

### Définir une route

Observez cette implémentation et identifiez les éléments à définir.

<figure><img src="../../../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Exemple de documentation produit par Swagger (nous le mettrons en place prochainement)</p></figcaption></figure>

### Structure de l'appel

<table><thead><tr><th>Critères</th><th>Valeur</th></tr></thead><tbody><tr><td>Verbe HTTP</td><td>GET</td></tr><tr><td>Chemin</td><td><pre><code>/pizzas
</code></pre></td></tr><tr><td>Paramètres</td><td>Aucun</td></tr></tbody></table>

### Structure de la réponse "Successfull"

<table><thead><tr><th>Critères</th><th>Valeur</th></tr></thead><tbody><tr><td>Code</td><td>200</td></tr><tr><td>Description</td><td>List of pizzas</td></tr><tr><td>Media type</td><td>JSON</td></tr><tr><td>Exemple value : Schema</td><td><pre class="language-json"><code class="lang-json">[
  {
    "id": 1,
    "title": "Margherita",
    "image": null,
    "ingredients": [
      "Tomato",
      "Mozzarella",
      "Basil"
    ],
    "price": 8.5
  }
]
</code></pre></td></tr></tbody></table>
