# TaskFlow Kanban Project

TaskFlow est une application web de gestion de projet de type Kanban, inspirée de Jira. Elle est construite en JavaScript vanilla, utilise Tailwind CSS pour le style, et s'appuie entièrement sur Firebase pour le backend (Authentification, base de données Firestore et Stockage).

Ce projet permet aux utilisateurs de créer des comptes, de gérer des projets (protégés par des codes d'accès) et de suivre les tâches à travers les colonnes "To Do", "In Progress", et "Done" avec des mises à jour en temps réel.

# Fonctionnalités Clés

Authentification et Gestion de Profil

* Authentification complète : Inscription et connexion par e-mail et mot de passe via Firebase Authentication.

* Réinitialisation du mot de passe : Fonctionnalité d'envoi d'e-mail pour réinitialiser le mot de passe.

* Gestion de profil : Les utilisateurs peuvent mettre à jour leur nom d'utilisateur et télécharger une photo de profil personnalisée (gérée par Firebase Storage).

## Gestion de Projet

* Tableau de bord : Visualisez tous les projets auxquels vous avez accès sur un tableau de bord d'accueil.

* Création de projets : Créez de nouveaux projets avec un nom, une description et un code d'accès unique (secret).

* Accès aux projets : Rejoignez un projet existant en utilisant son code d'accès.

## Tableau Kanban et Tâches

* Tableau par projet : Chaque projet possède son propre tableau Kanban (To Do, In Progress, Done).

* Mises à jour en temps réel : Utilise les "snapshots" Firestore pour que tous les changements (nouvelles tâches, changements de statut) soient reflétés instantanément pour tous les utilisateurs.

* Gestion CRUD des tâches : Créez, lisez, modifiez et supprimez des tâches.

* Assignation : Assignez des tâches à d'autres utilisateurs membres du projet.

* Glisser-déposer (Drag-and-Drop) : Déplacez facilement les tâches entre les colonnes pour changer leur statut.

## Filtrage et Tri

* Filtrage : Filtrez les tâches par nom ou par créateur.

* Tri : Triez les tâches par date de création (plus récent ou plus ancien).

## Technologies Utilisées

* Frontend : HTML, JavaScript (Vanilla ES6+), Tailwind CSS

* Backend (BaaS) : Firebase

* Authentication : Pour la gestion des utilisateurs.

* Firestore : Base de données NoSQL en temps réel pour les projets, utilisateurs et tâches.

* Storage : Pour l'hébergement des photos de profil des utilisateurs.

## 📂 Structure du Projet

    TaskFlow-Kanban/
    ├── .gitignore         # Fichiers ignorés par Git
    ├── README.md          # Ce fichier
    ├── index.html         # La structure (squelette) HTML de l'application
    └── src/
        ├── css/
        │   └── styles.css   # Fichier de styles (personnalisés ou compilés de Tailwind)
        └── js/
            ├── config.js    # (Probablement la configuration Firebase)
            └── main.js      # Toute la logique JavaScript (UI, état, logique Firebase)


## Démarrage

Ce projet est une application web statique qui se connecte directement à Firebase. Il n'y a pas de code côté serveur à exécuter, mais il doit être servi via un serveur local.

Note importante : L'ouverture du fichier index.html directement dans le navigateur (ex: file:///...) échouera probablement en raison des politiques de sécurité (CORS) des navigateurs, en particulier pour les opérations de Firebase Storage (comme l'upload de photos).

Prérequis

Node.js (requis pour utiliser npx serve)

Un compte Firebase pour configurer le backend.

Étapes d'installation et de configuration

Cloner le dépôt :

    git clone [URL_DU_REPO]
    cd TaskFlow-Kanban


## Configurer Firebase :

1- Créez un nouveau projet sur la console Firebase.

2- Activez l'Authentication (fournisseur E-mail/Mot de passe).

3- Activez Firestore Database.

4- Activez Storage. (Assurez-vous que vos règles de sécurité autorisent la lecture/écriture pour les utilisateurs authentifiés).

Dans les paramètres de votre projet, trouvez votre objet de configuration firebaseConfig.

Ajouter la configuration Firebase :

1- Ouvrez le fichier src/js/main.js (ou src/js/config.js s'il est dédié à cela).

2- Trouvez la variable firebaseConfig (elle est probablement vide ou un placeholder) et collez-y votre propre configuration :

##  Remplacez par votre propre configuration

        const firebaseConfig = {
        apiKey: "VOTRE_API_KEY",
        authDomain: "VOTRE_AUTH_DOMAIN",
        projectId: "VOTRE_PROJECT_ID",
        storageBucket: "VOTRE_STORAGE_BUCKET",
        messagingSenderId: "VOTRE_MESSAGING_SENDER_ID",
        appId: "VOTRE_APP_ID"
        };

##  Initialiser Firebase (la méthode d'initialisation peut varier)
# 
    firebase.initializeApp(firebaseConfig);
#

## Exécuter le projet

Choisissez une des options suivantes pour démarrer un serveur local :

* Option 1 : (Recommandée) Utiliser npx serve
Ouvrez un terminal dans le dossier racine du projet et exécutez :
#
    npx serve
#

Ouvrez l'adresse affichée (généralement http://localhost:3000) dans votre navigateur.

* Option 2 : Utiliser l'extension Live Server (VS Code)
Si vous utilisez Visual Studio Code, vous pouvez installer l'extension Live Server et cliquer sur "Go Live" en bas à droite de votre éditeur.
