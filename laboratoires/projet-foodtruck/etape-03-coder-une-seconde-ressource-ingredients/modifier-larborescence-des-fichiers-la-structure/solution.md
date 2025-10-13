# Solution

```
C:.
│   app.js
│   server.js
|   package.json
|   package-lock.json
│
├───config
│       database.js
│       swagger.js
│
├───ingredients
│       Ingredient.js
│       ingredientsController.js
│       ingredientsRouter.js
│
├───pizzas
│       Pizzas.js
│       pizzasController.js
│       pizzasRouter.js
│
└───routes
        router.js
```

## Points à traiter (issues)

### Comment gérer la base de données ?

Actuellement la base de données est spécifique pour une entité (pizzas). Le script de création de base de données est initialisé lors du lancement de l'application, via le contrôleur de pizza.

Réflexion : et si on utilisait un micro-service aussi pour la base de données ?

### Comment gérer les dépendances spécifiques à chaque micro-services ?

Actuellement seul un "package.json" est présent à la racine du projet.

Réflexion : et si on avait un package commun pour les dépendances communes, mais également un package.json pour chacune des ressources ?

### Comment gérer le code ?

Actuellement nous n'avons qu'un seul dépôt pour 2 ressources.&#x20;

Réflexion: Et si nous avions 2 dépôts différents, autrement dit 1 dépôt = 1 ressource ?

### Comment gérer plusieurs ressources codées en différentes langages ?

Actuellement tout est codé sur la même "stack".

Réflexion : Et si nous avions un service en python et un second en java script ?



