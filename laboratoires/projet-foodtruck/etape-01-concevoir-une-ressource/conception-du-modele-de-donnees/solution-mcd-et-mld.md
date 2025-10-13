# Solution - MCD et MLD

## Introduction

A cette étape du projet, nous cherchons à modéliser les pizzas présentes sur la carte des mets proposée par le Foodtruck.

## Modèle conceptuel de données

<figure><img src="../../../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

### Explications complémentaires

| Valeur              | Explications                                                                                                                                                                 |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| \_\_xxx\_\_\_       | <ul><li>identifiant naturel</li></ul>                                                                                                                                        |
| _italique_          | <ul><li>attribut optionnel</li></ul>                                                                                                                                         |
| `Ingredient "0..*"` | <ul><li>une pizza peut avoir aucun ou plusieurs ingrédients (en sachant que la pizza de base est une marguerita ayant de la sauce tomate et de la mozzarrella).</li></ul>    |
| `Ingredient "0..*"` | <p></p><ul><li>chaque ingrédient peut est présent sur une ou plusieurs pizzas.</li></ul><ul><li>Les identifiants naturels sont mentionnés comme suit "____name___"</li></ul> |

## Modèle logique de données

<figure><img src="../../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

### Explications complémentaires

* L'association N à N est bien devenue une relation N à N via une table intermédiaire.
* Les contraintes d'unicité sont cohérentes avec le MCD.
* Les types sont plus techniques, sans être en lien direct avec Node.js.
* Les associations sont bien devenues des tables.

