# Etape 00 - Squelette de notre API

## Intention

Ce laboratoire a pour intention de vous permettre de configurer votre projet (la base de votre code) ainsi que d'affiner la configuration de votre environnement de développement.

## Bibliographies

Afin de construire notre projet, il est assez naturel de s'inspirer de nos confrères qui ont l'expérience sur le framework Express.

Express offre un générateur de projet : [Express Generator](https://expressjs.com/en/starter/generator.html)

Jetbrains, l'éditeur de notre IDE émet également une procédure pour ouvrir un projet : [Jetbrains](https://www.jetbrains.com/help/webstorm/developing-node-js-applications.html)

## Objectifs

Vous devez réussir à valider les critères de qualité suivants tout comme des critères fonctionnels.

***

### Critères qualitatifs

#### Structure du projet

Considérez les différentes couches dont nous allons avoir besoin pour notre API (routes, controllers, middleware, tests...).&#x20;

Il s'agit de créer une structure de fichier qui s'adaptera bien à notre logique d'API.

{% embed url="https://medium.com/@hammad.shahid120/organizing-and-managing-rest-api-in-node-js-fdb74b828487" %}

#### Externalisation des variables

<mark style="color:orange;">Données sensibles</mark>

Tout au plus on va livrer un fichier d'exemple que chaque développeur va devoir ensuite compléter en fonction de son propre environnement.

<mark style="color:orange;">Données non-sensibles</mark>

Eviter à l'intégrateur (la personne responsable de déployer notre application) de dépendre de notre travail. Pensez au port d'écoute de notre api, aux règles de sécurités ([cors](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CORS)), aux différentes valeurs que l'intégrateur doit pouvoir modifier librement sans avoir besoin de "re-compiler" le projet.

<mark style="color:orange;">Différencier les environnements</mark>

Les variables globales seront spécifiques à chaque environnements (test, intégration, production).

{% embed url="https://medium.com/the-node-js-collection/making-your-node-js-work-everywhere-with-environment-variables-2da8cdf6e786" %}

#### Configurer votre VCS dès la création du squelette

Configurer votre VCS pour alléger au maximum le poids de votre livrable. Seules les sources que vous produisez doivent être intégrées à votre dépôt.

Exemple d'exclusion:

* [ ] les dépendances telles que les modules nodes.
* [ ] les données confidentielles présentes par exemple, dans un fichier .env.
* [ ] la branche _main_ répond à tous les critères émis dans ce document.
* [ ] la branche _develop_ est basés sur la branche _main_.

{% embed url="https://intellij-support.jetbrains.com/hc/en-us/community/posts/115000154070-How-to-gitignore-idea-files" %}

***

### Critères fonctionnels

#### Notre API écoute !

Prouver que votre application écoute bien sur un port spécifique (part défaut le 3000).

```bash
curl localhost:3000
```

```
{"message":"Welcome to the API"}
```

#### Exposer une ressource

Récupérer une ressource via une route correctement nommée.

```bash
curl localhost:3000/api/users | jq
```

```json
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    25  100    25    0     0   1404      0 --:--:-- --:--:-- --:--:--  1470
[
  {
    "id": 1,
    "name": "Alice"                                                                                                                                                                                        
  }
]
```

{% embed url="https://restfulapi.net/resource-naming/" %}

#### Code d'erreur

Valider que le bon code d'erreur est retourné lorsque l'on appelle une ressource inexistante.

```bash
curl -i localhost:3000/users
```

```json
HTTP/1.1 404 Not Found
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Security-Policy: default-src 'none'
X-Content-Type-Options: nosniff
Content-Type: text/html; charset=utf-8
Content-Length: 144
Date: Fri, 29 Aug 2025 07:07:10 GMT
Connection: keep-alive
Keep-Alive: timeout=5

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<title>Error</title>
</head>
<body>
<pre>Cannot GET /users</pre>
</body>
</html>
```

{% embed url="https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/404" %}
