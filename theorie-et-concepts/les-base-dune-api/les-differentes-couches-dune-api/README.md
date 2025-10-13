# Les différentes couches d'une API

Source : [Understanding the Three Layer of Software Interaction (APIs)](https://www.syncloop.com/blogs/software-interactions-api.html)

## Introduction

Pour mieux aborder la programmation par couche, voici un document présentant les différentes couches logiques que nous allons réaliser lors de notre projet d'API.

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption><p>Schéma vulgarisant les différents couches</p></figcaption></figure>

{% hint style="warning" %}
Pour un projet d'API (sans interface graphique), la vue correspondant au dialogue possible avec l'API, notamment les retours en  JSON qui sont produits.
{% endhint %}

### Couche de présentation (Présentation layer)

La couche de présentation, également appelée « point de terminaison API », est la couche avec laquelle les développeurs interagissent le plus fréquemment. Cette couche fournit une interface conviviale permettant aux développeurs d'accéder aux fonctionnalités et aux données du service sous-jacent. Elle est chargée de traiter les requêtes entrantes et de renvoyer des réponses dans un format facilement compréhensible par les développeurs.

La couche de présentation peut prendre différentes formes, en fonction des exigences de l'API. Il peut s'agir d'une API REST qui utilise des requêtes HTTP pour échanger des données ou d'une API SOAP qui utilise des messages XML pour communiquer. Quelle que soit l'implémentation spécifique, la couche de présentation est la partie publique de l'API et constitue le premier point de contact pour les développeurs.

{% hint style="warning" %}
Pour notre projet, nous opterons pour une approche Restfull (API qui suit les préconisations REST)
{% endhint %}

### Couche métier (Business layer)

La couche logique métier, également appelée « middleware API », est la couche qui contient la logique centrale de l'API. Elle est chargée de traiter les requêtes reçues de la couche présentation et de générer des réponses en fonction des actions demandées.

La couche logique métier est celle où réside la fonctionnalité principale de l'API. Elle peut effectuer la validation des données, l'authentification et l'autorisation, les requêtes de base de données ou d'autres opérations complexes. Cette couche est généralement développée par le fournisseur de services et n'est pas directement accessible aux développeurs.

{% hint style="warning" %}
Pour notre projet, nous réaliserons toutes les couches, y compris la couche métier.
{% endhint %}

### Couche de données (Data layer)

La couche de stockage des données, également appelée « base de données API », est la couche où sont stockées toutes les données utilisées par l'API. Cette couche est chargée de gérer le stockage, la récupération et la modification des données. Elle peut utiliser diverses technologies de base de données telles que SQL, NoSQL ou des bases de données orientées objet.

La couche de stockage des données est le composant le plus critique de l'API, car elle contient les données sur lesquelles s'appuie l'API. Si la couche de stockage des données tombe en panne, l'ensemble de l'API peut échouer. Il est donc essentiel de s'assurer que la couche de stockage des données est correctement conçue et mise en œuvre.

## Conclusion

En conclusion, les API se composent de trois couches : la couche de présentation, la couche de logique métier et la couche de stockage des données. Chaque couche joue un rôle crucial dans la fonctionnalité et les performances de l'API. Il est essentiel pour les développeurs qui souhaitent créer des API robustes, fiables et évolutives de comprendre les trois couches d'une API.
