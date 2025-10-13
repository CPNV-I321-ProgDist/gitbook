# Un exemple d'API avec Express

## Intention

Le framework Express facilite de nombreux aspects du développement, mais comme tout framework, déstabilise un peu le développeur par le nombre de fichier et répertoire à utiliser.

Cette page a pour objectif de démontrer le contenu de chaque fichier et ainsi avoir une meilleure compréhension du framework.

Ce contenu est un complément à la page précédente présentant [les différentes couches d'une API](../../../les-differentes-architectures/).

## La structure du projet

{% code fullWidth="true" %}
```
.env                 // Fichier pour stocker les variables d'environnement (ex : mots de passe, port)
.gitignore           // Liste des fichiers/dossiers à ne pas envoyer sur Git (ex : node_modules, .env)
app.js               // Fichier principal de l'application Express (définit app, middlewares, routes)
package-lock.json    // Fichier généré automatiquement qui verrouille les versions exactes des dépendances
package.json         // Fichier de configuration du projet Node.js (nom, version, dépendances, scripts)
server.js            // Fichier qui lance le serveur et écoute sur un port

config/              // Dossier de configuration
    database.js      // Configuration de la connexion à la base de données

controllers/         // Dossier des "contrôleurs" (logique métier)
    productController.js // Contient les fonctions pour gérer les produits (CRUD)

entities/            // Dossier des entités / modèles
    Product.js       // Définition du modèle Product (structure des données pour la DB)

routes/              // Dossier des routes (gestion des endpoints)
    router.js        // Fichier principal qui rassemble toutes les routes
    products.js      // Routes spécifiques aux produits (GET, POST, PUT, DELETE)
```
{% endcode %}

### Le fichier .env

Permet d'externaliser les variables qui doivent pouvoir être modifiées au lancement de l'API, sans avoir besoin de modifier le code.

```bash
PORT=3000             // port d'écoute sur serveur
DB_FILE=./dev.sqlite  // emplacement de la base de données
NODE_ENV=development  // spécifie l environnement de déploiement
```

### Le fichier package

Liste toutes les dépendances et les versions à installer (via le gestionnaire de package npm) avant de pouvoir exécuter le projet.

```json
{
  "name": "products-api",
  "version": "1.0.0",
  "description": "RESTful Products API with sqlite3, express-validator, and swagger-ui",
  "main": "./src/server.js",
  "scripts": {
    "start": "node src/server.js",
    "dev": "nodemon src/server.js",
    "test": "jest --coverage"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "dotenv": "^16.6.1",                  //permet l'exploitation de variables d'environnement
    "express": "^4.21.2",                 //framework express
    "express-validator": "^6.15.0",       //middelware express pour valider les données des requêtes
    "morgan": "^1.10.1",                  //middelware node.js pour faciliter la production de logs.
    "sqlite3": "^5.1.7",                  //nécessaire pour travailler avec sqlite
    "swagger-jsdoc": "^6.2.8",            //pour la génération de documentation swagger
    "swagger-ui-express": "^4.6.3"        //pour la génération de documentation swagger
  },
  "devDependencies": {                     //dépendances spécifique pour le dev
    "jest": "^29.5.0",                     //framework de test
    "nodemon": "^3.1.10"                   //utilitaire permettant des redémarrages automatiques
                                           // du serveur lorsque des fichiers ont été changés.
  }
}
```

### Le .gitignore

Offre un mécanisme d'exclusion des fichiers et répertoires que nous ne désirons pas intégrer dans notre code source. Pour un projet avec node, le répertoire "node\_modules" en est un bon exemple. Inutile d'intégrer des dépendances que npm sera tout à fait capable d'aller chercher, grâce au fichier "package.json" décrivant chacunes des ressources.

{% embed url="https://github.com/github/gitignore/blob/main/Global/JetBrains.gitignore" %}

```gitignore
# Custom for the project   //exemple d'exclusions spécifiques au projet
node_modules/
dev.sqlite
.env
coverage/
```

### Le fichier server.js

Express exploite un fichier "server.js" pour configurer rapidement un serveur offrant l'exposition d'un port d'écoute. On y voit la configuration du port d'écoute ainsi que l'initialisation de l'écoute.

{% code fullWidth="true" %}
```javascript
require("dotenv").config();                       // Charge les variables d'environnement depuis le fichier .env

const app = require("./app");                     // Importe l'application Express définie dans app.js

const PORT = process.env.PORT || 3000;           // Définit le port : prend la valeur du .env sinon utilise 3000

app.listen(PORT, () => {                          // Démarre le serveur sur le port choisi
    console.log(`API running on http://localhost:${PORT}`);  // Affiche dans la console l'URL pour accéder à l'API
      if (process.env.NODE_ENV !== 'production') {
        console.log(`Swagger UI: http://localhost:${port}/docs`);   //Mise à disposition du Swagger
    }  
});
```
{% endcode %}

### Le fichier app.js

Express exploite un fichier "app.js", appelé par le "server.js" et qui déploiera l'application.

On y positionnera les différentes dépendances telles qu'express, tout comme l'initialisation de la base de données.

Il déclare également le point d'entrée de l'API pour que les requêtes puissent être redirigées vers le routage par ressource.

{% code fullWidth="true" %}
```javascript
const express = require("express");                     // Importe Express pour créer le serveur
const morgan = require('morgan');                       // Importe la libraire de log
const errorHandler = require("./middleware/errorHandler"); // Importe le middleware pour gérer les erreurs
const initDatabase = require("./config/db");           // Importe la fonction pour initialiser la base de données

const app = express();                                  // Créer l'application Express

// Middleware
app.use(morgan('dev'));                                //Active les logs en mode "dev"
app.use(express.json());                               // Permet de lire le corps des requêtes en JSON

// Initialize DB globally
const db = initDatabase();                             // Initialise la base de données
app.use((req, res, next) => {                         
    req.db = db;                                       // Attache la DB à chaque requête pour y accéder dans les routes
    next();                                            // Passe à la suite du traitement
});

// Routes
const userRoutes = require("./routes/users");         // Importe les routes liées aux utilisateurs
app.use("/api/users", userRoutes);                    // Préfixe ces routes avec /api/users

// Root endpoint
app.get("/", (req, res) => {                          
    res.json({ message: "Welcome to the API" });      // Point d'entrée principal qui renvoie un message simple
});

// error handler (fallback)
app.use((err, req, res, next) => {                    //Gestion de l'erreur 500 (pourrait-être déplacée dans "middelware"
    console.error(err);
    if (!res.headersSent) {
        res.status(err.status || 500).json({ error: err.message || 'Internal Server Error' });
    } else next(err);
});               

module.exports = app;                                 // Exporte l'application pour pouvoir l'utiliser dans server.js

```
{% endcode %}

