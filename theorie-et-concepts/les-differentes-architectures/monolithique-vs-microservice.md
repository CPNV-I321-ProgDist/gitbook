# Monolithique vs MicroService

Source : [AWS](https://aws.amazon.com/compare/the-difference-between-monolithic-and-microservices-architecture/)

## Quelle est la différence entre une architecture monolithique et une architecture de microservices ?

Une architecture monolithique est un modèle de développement logiciel traditionnel qui utilise une base de code unique pour exécuter plusieurs fonctions métier. Tous les composants logiciels d'un système monolithique sont interdépendants en raison des mécanismes d'échange de données au sein du système.&#x20;

La modification d'une architecture monolithique est contraignante et prend du temps, car de petites modifications ont un impact sur des pans entiers de la base de code. À l'inverse, les microservices sont une approche architecturale qui consiste à décomposer le logiciel en petits composants ou services indépendants.&#x20;

Chaque service joue un rôle unique et communique avec les autres services au moyen d'une interface bien définie. Comme ils s'exécutent indépendamment, vous pouvez mettre à jour, modifier, déployer ou mettre à l'échelle chaque service selon vos besoins.

### Principales différences : monolithique versus microservices <a href="#ams-what-isc2-pattern-data" id="ams-what-isc2-pattern-data"></a>

Les applications monolithiques se composent généralement d'une interface utilisateur côté client, d'une base de données et d'une application côté serveur. Les développeurs construisent tous ces modules sur une base de code unique.

D'autre part, dans une architecture distribuée, chaque microservice fonctionne pour exécuter une fonctionnalité ou une logique métier unique. Au lieu d'échanger des données au sein de la même base de code, les microservices communiquent via une API.

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>



