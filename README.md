# YONETWORK - Système de Gestion de Factures

## Description du Projet

YONETWORK Facturation est une application web complète de gestion de factures développée pour YONETWORK S.A.R.L. Cette application permet de créer, gérer, visualiser et télécharger des factures professionnelles, avec un système d'authentification sécurisé basé sur JWT.

## Fonctionnalités Principales

- *Authentification sécurisée* : Système de connexion avec JWT
- *Tableau de bord interactif* : Vue d'ensemble des statistiques et activités
- *Gestion des factures* :
  - Création et édition de factures
  - Prévisualisation en temps réel
  - Téléchargement au format PDF
  - Numérotation automatique basée sur la date (YYYY-MM-XXX)
- *Gestion des clients* : Stockage et récupération des informations clients
- *Interface responsive* : Adaptée à tous les appareils

## Prérequis

- Node.js (v16 ou supérieur)
- NPM ou Yarn

## Installation

1. Cloner le dépôt bash
   git clone <url-du-repo>
   cd GESTION FACTURE
   

2. Installer les dépendances bash
   npm install
   

3. Configurer l'URL de l'API dans src/services/api.ts
   javascript const API_URL = 'https://api.yonetwork.ma'; // À modifier selon votre environnement
   

4. Lancer l'application en mode développement
   bash npm run dev
   

## Structure du Projet


/DASHBORD
├── public/            # Fichiers statiques
├── src/
│   ├── components/    # Composants React
│   │   ├── Auth/      # Composants d'authentification
│   │   └── Dashboard/ # Composants du tableau de bord et factures
│   ├── services/      # Services d'API et utilitaires
│   ├── store/         # Configuration Redux et slices
│   │   └── slices/    # Slices Redux (auth, invoices, etc.)
│   ├── utils/         # Fonctions utilitaires
│   ├── App.tsx        # Composant principal et routes
│   └── main.tsx       # Point d'entrée
└── package.json       # Dépendances et scripts


## Authentification

L'application utilise JWT (JSON Web Token) pour l'authentification :

1. L'utilisateur se connecte avec ses identifiants
2. Le serveur vérifie les identifiants et renvoie un token JWT
3. Le token est stocké dans le localStorage et inclus dans toutes les requêtes API
4. Les routes protégées vérifient la présence et la validité du token

### Configuration de l'API

Le service API est configuré pour gérer automatiquement :
- L'ajout du token dans les en-têtes d'autorisation
- La redirection vers la page de connexion en cas de token expiré (erreur 401)
- La persistance de la session utilisateur

## Facturation

### Format des Factures

Chaque facture contient :
- Informations client (nom, adresse)
- Liste des produits/services avec quantités et prix
- Calcul automatique des sous-totaux, TVA et montant total
- Pied de page personnalisé avec informations de l'entreprise

### Numérotation des Factures

Le système génère automatiquement des numéros de facture au format :

YYYY-MM-XXX

où :
- YYYY : année en cours
- MM : mois en cours
- XXX : numéro séquentiel commençant à 300

### Génération de PDF

L'application utilise une génération HTML-to-PDF personnalisée pour créer des factures professionnelles avec :
- En-tête de l'entreprise
- Corps détaillé des articles
- Résumé des totaux et conditions
- Pied de page contenant les informations légales de l'entreprise
- Pagination automatique pour les factures de plus de 10 articles

## Personnalisation

### Informations de l'Entreprise

Les informations de l'entreprise (pied de page, etc.) peuvent être modifiées dans :
- src/utils/pdfGenerator.ts pour les PDF
- src/components/Dashboard/ViewInvoice.tsx pour l'affichage

### Styles et Apparence

L'interface utilise Tailwind CSS pour le styling, facilitant la personnalisation des couleurs, polices et styles dans les fichiers respectifs.

## Développement et Extension

### Ajouter de Nouvelles Fonctionnalités

1. Créer les composants nécessaires dans /src/components/
2. Ajouter les routes dans App.tsx si nécessaire
3. Créer ou mettre à jour les slices Redux dans /src/store/slices/

### API et Services

Pour ajouter de nouveaux services API :
1. Ouvrir src/services/api.ts
2. Ajouter un nouveau service avec les méthodes nécessaires

## Déploiement

1. Construire l'application pour la production
   bash
   npm run build
   

2. Les fichiers générés se trouvent dans le dossier dist/

3. Déployer ces fichiers sur un serveur web statique

## Contribution

Pour contribuer au projet :
1. Forker le dépôt
2. Créer une branche (git checkout -b feature/nouvelle-fonctionnalite)
3. Committer vos changements (git commit -m 'Ajout de nouvelle fonctionnalité')
4. Pusher vers la branche (git push origin feature/nouvelle-fonctionnalite)
5. Ouvrir une Pull Request

## Licence

Propriété de YONETWORK S.A.R.L. - Tous droits réservés.

## Contact

Pour toute question ou assistance technique :
- Email : contact@YONETWORK.ma
- Téléphone : 0661566822
