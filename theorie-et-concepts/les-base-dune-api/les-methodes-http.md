# Les méthodes HTTP

Source : [https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods)

### Introduction

Dans le cadre du développement d’API REST, les **méthodes HTTP** jouent un rôle essentiel. Elles permettent de décrire **l’intention d’une requête** en utilisant un verbe standardisé (comme GET ou POST) appliqué à une ressource identifiée par une URL (la _route_).

<mark style="color:orange;">Un principe fondamental de REST est que</mark> <mark style="color:orange;"></mark><mark style="color:orange;">**l’action n’est pas incluse dans le chemin de l’URL**</mark>. Autrement dit, au lieu d’avoir une route comme `/createUser`, on utilisera simplement `/users`, et c’est le verbe HTTP (POST, GET, etc.) qui exprimera l’opération attendue.

\
Exemple :

* `POST /users` → crée un nouvel utilisateur
* `GET /users` → récupère la liste des utilisateurs

Ainsi, l’URL représente une **ressource**, et le verbe HTTP exprime **l’opération** sur cette ressource.

## Les principales méthodes HTTP

### GET

* **Objectif** : Récupérer une ressource ou une collection de ressources.
* **Exemples** :
  * `GET /users` → liste tous les utilisateurs
  * `GET /users/42` → récupère l’utilisateur avec l’ID 42
* **Remarque** : cette méthode ne doit pas modifier l’état du serveur (idempotente et sans effet de bord).

### POST

* **Objectif** : Créer une nouvelle ressource.
* **Exemples** :
  * `POST /users` avec un corps JSON → crée un nouvel utilisateur
* **Remarque** : la requête POST n’est pas idempotente, répéter la requête peut entraîner plusieurs créations.

### PUT

* **Objectif** : Remplacer complètement une ressource existante.
* **Exemples** :
  * `PUT /users/42` avec un corps JSON complet → remplace toutes les informations de l’utilisateur 42
* **Remarque** : méthode idempotente (répéter la requête produit le même résultat final).

### PATCH

* **Objectif** : Mettre à jour partiellement une ressource.
* **Exemples** :
  * `PATCH /users/42` avec un corps JSON ne contenant que `{ "email": "new@mail.com" }` → modifie uniquement l’email de l’utilisateur 42
* **Remarque** : utile pour éviter d’envoyer l’ensemble de la ressource quand une seule partie change.

## Les méthodes complémentaires

### DELETE

* **Objectif** : Supprimer une ressource.
* **Exemple** : `DELETE /users/42` → supprime l’utilisateur 42.
* **Caractéristique** : généralement idempotente (supprimer deux fois une ressource mène au même état final : ressource absente).

### HEAD

* **Objectif** : Récupérer uniquement les **en-têtes** de la réponse sans le corps.
* **Exemple** : `HEAD /users/42` → permet de vérifier si l’utilisateur existe sans télécharger son contenu.
* **Caractéristique** : souvent utilisée pour des vérifications rapides (existence, taille, type MIME).

### OPTIONS

* **Objectif** : Demander quelles méthodes HTTP sont disponibles pour une ressource.
* **Exemple** : `OPTIONS /users` → réponse avec `Allow: GET, POST, OPTIONS`.
* **Caractéristique** : largement utilisé dans le cadre du **CORS** (Cross-Origin Resource Sharing).

## Conclusion

Les méthodes HTTP définissent un langage standardisé entre client et serveur.

* Les **principales** (GET, POST, PUT, PATCH) couvrent la majorité des cas d’usage.
* Les **complémentaires** (DELETE, HEAD, OPTIONS) enrichissent les possibilités et renforcent la robustesse d’une API.

Une API REST bien conçue respecte ce principe :

{% hint style="warning" %}
**L’URL décrit une ressource, et c’est la méthode HTTP qui exprime l’opération**
{% endhint %}

## Tableau récapitulatif des méthodes HTTP

| Méthode     | Objectif principal                   | Exemple d’URL      | Corps attendu ?  | Idempotente ? | Remarques                                          |
| ----------- | ------------------------------------ | ------------------ | ---------------- | ------------- | -------------------------------------------------- |
| **GET**     | Lire une ressource ou une collection | `GET /users/42`    | Non              | ✅ Oui         | Sans effet de bord                                 |
| **POST**    | Créer une nouvelle ressource         | `POST /users`      | Oui (JSON, etc.) | ❌ Non         | Répéter l’appel crée plusieurs entrées             |
| **PUT**     | Remplacer une ressource existante    | `PUT /users/42`    | Oui (complet)    | ✅ Oui         | Met à jour toute la ressource                      |
| **PATCH**   | Modifier partiellement une ressource | `PATCH /users/42`  | Oui (partiel)    | ⚠️ Variable   | Mise à jour ciblée                                 |
| **DELETE**  | Supprimer une ressource              | `DELETE /users/42` | Non              | ✅ Oui         | Deux suppressions successives donnent le même état |
| **HEAD**    | Récupérer uniquement les en-têtes    | `HEAD /users/42`   | Non              | ✅ Oui         | Vérification rapide sans télécharger le corps      |
| **OPTIONS** | Connaître les méthodes disponibles   | `OPTIONS /users`   | Non              | ✅ Oui         | Utilisé notamment pour le CORS                     |
