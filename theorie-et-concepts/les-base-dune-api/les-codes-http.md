# Les codes HTTP

Source : [https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status)

## Introduction

Lorsqu’un client (navigateur, application, API) envoie une requête à un serveur via HTTP, celui-ci répond toujours avec un **code de statut** à trois chiffres.\
Ces codes permettent de connaître rapidement le **résultat de la requête** : succès, erreur côté client, erreur côté serveur, etc.

Chaque code appartient à une **famille** identifiée par son premier chiffre :

* **1xx** → Information
* **2xx** → Succès
* **3xx** → Redirection
* **4xx** → Erreur côté client
* **5xx** → Erreur côté serveur

## Les grandes familles de codes HTTP

### 1xx – Informations

* Indiquent que la requête est en cours de traitement.
* **Peu utilisés** dans les API courantes.
* Exemple :
  * `100 Continue` → le serveur a bien reçu la requête initiale, le client peut continuer.

### 2xx – Succès

* Indiquent que la requête a été correctement traitée.
* Codes fréquents :
  * `200 OK` → succès générique.
  * `201 Created` → ressource créée avec succès (souvent après un `POST`).
  * `204 No Content` → succès sans contenu renvoyé (utile après `DELETE`).

### 3xx – Redirection

* Indiquent que le client doit faire une nouvelle requête ailleurs.
* Exemples :
  * `301 Moved Permanently` → la ressource a changé d’adresse définitivement.
  * `302 Found` → redirection temporaire.
  * `304 Not Modified` → la ressource n’a pas changé depuis la dernière requête (optimisation du cache).



### 4xx – Erreurs côté client

* Indiquent que la requête est invalide.
* Exemples :
  * `400 Bad Request` → requête mal formée.
  * `401 Unauthorized` → authentification requise (ou échouée).
  * `403 Forbidden` → accès refusé, même avec authentification.
  * `404 Not Found` → ressource inexistante.
  * `409 Conflict` → conflit (ex. tentative de création d’une ressource déjà existante).

### 5xx – Erreurs côté serveur

* Indiquent que la requête était valide, mais que le serveur a échoué à la traiter.
* Exemples :
  * `500 Internal Server Error` → erreur générique du serveur.
  * `502 Bad Gateway` → le serveur intermédiaire (proxy, gateway) a reçu une réponse invalide.
  * `503 Service Unavailable` → serveur indisponible (surcharge ou maintenance).
  * `504 Gateway Timeout` → le serveur intermédiaire n’a pas reçu de réponse dans les temps.

## Tableau récapitulatif des code HTTP courants

| Famille | Code | Signification         | Usage typique                               |
| ------- | ---- | --------------------- | ------------------------------------------- |
| **1xx** | 100  | Continue              | Signal d’attente, rarement utilisé          |
| **2xx** | 200  | OK                    | Requête réussie                             |
|         | 201  | Created               | Création d’une ressource (POST)             |
|         | 204  | No Content            | Suppression réussie, pas de contenu renvoyé |
| **3xx** | 301  | Moved Permanently     | Redirection définitive                      |
|         | 302  | Found                 | Redirection temporaire                      |
|         | 304  | Not Modified          | Ressource inchangée (cache)                 |
| **4xx** | 400  | Bad Request           | Requête invalide                            |
|         | 401  | Unauthorized          | Authentification nécessaire                 |
|         | 403  | Forbidden             | Accès refusé                                |
|         | 404  | Not Found             | Ressource introuvable                       |
|         | 409  | Conflict              | Conflit de données                          |
| **5xx** | 500  | Internal Server Error | Erreur serveur générique                    |
|         | 502  | Bad Gateway           | Proxy/gateway a reçu une mauvaise réponse   |
|         | 503  | Service Unavailable   | Serveur indisponible                        |
|         | 504  | Gateway Timeout       | Délai dépassé côté serveur intermédiaire    |
