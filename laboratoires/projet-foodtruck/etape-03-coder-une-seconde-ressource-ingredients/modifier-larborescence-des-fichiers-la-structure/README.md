# Modifier l'arborescence des fichiers (la structure)

## Intention

L'étape précédente nous a permis d'implémenter une première ressource et de la tester.

Cette nouvelle étape nous permettra de réaliser l'implémentation d'une deuxième ressource.

{% hint style="warning" %}
N'oubliez pas, nous sommes en train de créer une application "distribuée" !
{% endhint %}

## Objectif

Actuellement nous avons intégré la notion d'ingrédient comme une simple "liste" dans une pizza. Dans ce laboratoire, l'objectif est de pouvoir gérer les ingrédients comme une ressource.&#x20;

{% hint style="warning" %}
Le fonctionnement actuel de Pizzas ne doit pas être déstabilisé. Nous ferons dialoguer les deux ressources dans une prochaine étape. Ici il ne s'agit que de créer la ressource "Ingredients".
{% endhint %}

## Phase conceptuelle

* [ ] Identifier l'impact de l'ajout d'une nouvelle ressource sur notre projet
  * [ ] Certains fichiers sont communs à toutes les ressources et ne devront pas être modifiés
  * [ ] D'autres fichiers spécifiques à chaque ressources sont concernées par cette étape d'enrichissement fonctionnel.
* [ ] Pour chacunes des couches logiques, identifiez clairement les impacts:
  * [ ] Presentation Layer ?
  * [ ] Businesss Layer ?
  * [ ] Data Layer ?

#### Rappel

Voici la structure actuelle:

```
│   .env
│   .gitignore
│   dev.sqlite
│   package-lock.json
│   package.json
│   README.md
│
├───docs
│       class_diagram.puml
│
└───src
    │   app.js
    │   server.js
    │
    ├───config
    │       database.js
    │       swagger.js
    │
    ├───controllers
    │       pizzasController.js
    │
    ├───entities
    │       Pizza.js
    │
    └───routes
            pizzas.js
            router.js
```



