# Introduction - Vers les architectures distribuées

### **Introduction – Vers les architectures distribuées**

Pendant longtemps, les applications étaient <mark style="color:orange;">**monolithiques**</mark> : tout le code, la logique métier, et les données vivaient dans un seul bloc déployé sur un seul serveur. Cette approche fonctionnait bien dans un contexte où :

* la <mark style="color:$warning;">charge</mark> utilisateur était limitée,
* le <mark style="color:$warning;">matériel</mark> était coûteux et peu évolutif,
* la connectivité <mark style="color:$warning;">réseau</mark> était lente ou instable,
* la <mark style="color:$warning;">virtualisation et le cloud</mark> n’existaient pas.

Mais avec l’augmentation du volume de données, la nécessité de servir des milliers (voire des millions) d’utilisateurs simultanément, et la mondialisation des services, ce modèle a montré ses limites : impossibilité de monter en charge efficacement, difficulté de maintenance et dépendances fortes entre composants. **C’est là qu’est née l’architecture distribuée** : diviser une application en plusieurs composants coopérants, répartis sur plusieurs machines, pour gagner en performance, en disponibilité et en résilience.

### Différence entre un système centralisé et un système distribué

Dans un système centralisé, toutes les données et ressources informatiques sont conservées et contrôlées dans un seul endroit central, tel qu'un serveur. Les applications et les utilisateurs se connectent à ce hub afin d'accéder aux données et de les traiter. Bien que cette configuration soit facile à entretenir et sécurisée, elle peut devenir un goulot d'étranglement si trop d'utilisateurs y accèdent simultanément ou si le serveur central tombe en panne.

Un système distribué, en revanche, répartit les données et les ressources sur plusieurs serveurs ou emplacements, souvent répartis sur différents sites physiques. Cette configuration offre une meilleure évolutivité et une plus grande fiabilité, car le système peut continuer à fonctionner même en cas de défaillance d'un composant. Cependant, en raison de leurs nombreux points d'interaction, les systèmes distribués peuvent être plus difficiles à sécuriser et à administrer.

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

### **Première génération – CORBA et les pionniers du distribué**

Dans les années 1990, la première vague d’architectures distribuées s’est appuyée sur des standards comme **CORBA** (Common Object Request Broker Architecture).\
Ces technologies visaient à permettre la communication entre programmes, même écrits dans des langages différents et exécutés sur des systèmes hétérogènes. Cependant, elles étaient :

* complexes à mettre en œuvre,
* fortement couplées,
* sensibles aux différences d’implémentation réseau,
* peu adaptées aux environnements Internet émergents.

### **Deuxième génération – Le cloud comme catalyseur**

Avec l’essor massif du **cloud computing** dans les années 2010, l’architecture distribuée a changé d’échelle. Les contraintes matérielles (achat de serveurs, gestion de datacenters) ont quasiment disparu grâce aux modèles **IaaS**, **PaaS** et **FaaS**, permettant :

* d’allouer des ressources à la demande,
* de déployer mondialement en quelques minutes,
* de concevoir des applications **cloud-native**, pensées pour être élastiques, tolérantes aux pannes et facilement évolutives.

### **Tiers logique et tiers physique**

Pour bien comprendre une architecture distribuée moderne, il est essentiel de distinguer :

* **Le tiers logique** – l’organisation et la structure du code : découpage en microservices, API, logique métier, modèles de données.
* **Le tiers physique** – l’infrastructure qui héberge et fait communiquer ces composants : serveurs, conteneurs, réseau, équilibreurs de charge, zones géographiques de déploiement.

Cette séparation aide à concevoir des systèmes où la logique applicative est indépendante des contraintes d’hébergement, ce qui est clé dans un monde où les environnements évoluent rapidement.

### Les composants clés d'un système distribué

Les systèmes distribués sont des réseaux d'ordinateurs indépendants qui collaborent pour atteindre un objectif commun. Ces systèmes améliorent la fiabilité, l'évolutivité et l'efficacité en répartissant les tâches entre différents nœuds. Les composants clés sont les suivants:

Nœuds : ordinateurs ou appareils individuels qui participent au système.\
Réseau : support par lequel les nœuds communiquent.\
Middleware : logiciel qui facilite la communication et la gestion des données entre les nœuds.



Sources:

* [https://www.geeksforgeeks.org/computer-networks/what-is-a-distributed-system/](https://www.geeksforgeeks.org/computer-networks/what-is-a-distributed-system/)
