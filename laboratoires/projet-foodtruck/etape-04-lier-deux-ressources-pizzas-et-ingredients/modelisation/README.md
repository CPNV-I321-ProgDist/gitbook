# Modélisation

## Intention

Dans les [etape02](../../etape-02-coder-une-ressource-pizzas/) et [etape03](../../etape-03-coder-une-seconde-ressource-ingredients/) nous avons développé 2 ressources indépendantes les unes des autres.

Il est venu temps de créer la relation entre elles.

Cette étape va nous permettre de modéliser correctement le fait qu'une pizza contient 1 ou plusieurs ingrédients, tout comme un ingrédient peut se retrouver sur une ou plusieurs pizzas.

## Objectif

Dans ce laboratoire, vous devez réaliser les tâches suivantes:

* [ ] Dessinez le diagramme de classes intégrant les deux ressources
* [ ] Dessinez le modèle logique de données intégrant les deux ressources&#x20;
* [ ] Dessinez la séquence de création d'une pizza.
  * [ ] Critères d'acceptance
    * [ ] Une exception sera levée si
      * [ ] La requête ne contient pas tous les paramètres ou qu'ils ne sont pas du bon type.
      * [ ] Les ingrédients de la nouvelle pizza doivent tous exister pour pouvoir créer la pizza.
      * [ ] Si on tente d'utiliser un nom de pizza existant.
  * [ ] Dialogue entre les ressources
    * [ ] Se fait via les contrôleurs respectifs. Le contrôleur "Pizzas" n'accédent pas en direct à l'entité "Ingredients".

{% hint style="warning" %}
Le tout avec Plant UML
{% endhint %}

