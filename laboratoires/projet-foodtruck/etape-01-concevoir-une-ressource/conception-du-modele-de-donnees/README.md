# Conception du modèle de données

## Critères à respecter pour la modélisation

Utilisez bien les normes "Meurise" pour dessiner cette première version du modèle de données.

Rappel MCD:

* [ ] Les entités sont au pluriel.
* [ ] Les entités affichent des attributs uniques (identifiant naturel) qui permettront ensuite les contraintes d'unicité.
* [ ] Les types de données sont simples et non techniques (Text vs String).
* [ ] Un verbe ainsi que des cardinalités (min et max) explicitent les associations entre les entités.
* [ ] Les associations "N à N" n'exploitent pas -encore- de tables intermédiaires.\
  \
  Rappel MLD:
* [ ] Doit être cohérent avec le MCD.
* [ ] Les entités deviennent des tables, également au pluriel.
* [ ] Les associations deviennent des relations.
  * [ ] C'est à cette étape&#x20;
    * [ ] qu'une association N à N requiert une table intermédiaire.
    * [ ] qu'une association 1 à N induit une clé étrangère sur l'une des tables.&#x20;
* [ ] Les types de données se précisent. Attention, cela reste des types génériques et non spécifiques à un langage particulier.

{% hint style="warning" %}
MCD ET MLD DOIVENT ÈTRE COHERENTS. N'OUBLIEZ PAS DE FAIRE DES ALLERS-RETOURS ENTRE LES DEUX POUR GARANTIR CE CRITERE.
{% endhint %}
