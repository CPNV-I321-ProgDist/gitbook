# Etape 05 - Deux micro-services indépendants

## Intention

Afin de pouvoir exécuter nos APIs sur des noeuds différents, nous devons modifier la structure du projet actuel.

Les étapes de réalisation sont présentées dans la vidéo ci-dessous. Vous disposez également du code.

Elle sont les suivantes:

* [ ] Séparation des ressources pour disposer d'une base de données ainis qu'un serveur dédiés.
* [ ] Suppression de toutes les références qui ne sont pas essentielles à la ressource (on retire toutes la logique ingrédients de la ressource pizza).
* [ ] Ajout d'une table "product\_compositions" pour faire le lien entre ingrédients et pizzas.
* [ ] Intégration d'un service "pizza" pour gérer la composition des pizzas et communication avec le micro-services "ingredients".

### Le code

{% embed url="https://github.com/I321-ProgDist/express-api-starter/tree/develop" %}

