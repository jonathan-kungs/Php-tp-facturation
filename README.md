# Php-tp-facturation 
SYSTÈME DE FACTURATION AVEC LECTEUR CODES-BARRES
  Travaux Pratiques PHP — L2 FASI 2025-2026
  Université Protestante au Congo
====================================================

PRÉREQUIS
---------
- PHP 8.0 ou supérieur
- Un serveur web local : XAMPP, WAMP, MAMP ou Laravel Herd
- Un navigateur moderne (Chrome, Edge, Firefox)
- Connexion internet pour charger QuaggaJS (lecteur codes-barres)

INSTALLATION RAPIDE AVEC XAMPP (Windows)
-----------------------------------------
1. Installer XAMPP depuis https://www.apachefriends.org/
2. Copier le dossier "facturation/" dans :
      C:\xampp\htdocs\facturation\
3. Démarrer Apache dans le panneau XAMPP
4. Ouvrir dans le navigateur :
      http://localhost/facturation/

INSTALLATION AVEC WAMP (Windows)
----------------------------------
1. Installer WampServer depuis https://www.wampserver.com/
2. Copier "facturation/" dans :
      C:\wamp64\www\facturation\
3. Démarrer WampServer
4. Ouvrir : http://localhost/facturation/

INSTALLATION MACOS (avec MAMP)
--------------------------------
1. Installer MAMP depuis https://www.mamp.info/
2. Copier "facturation/" dans :
      /Applications/MAMP/htdocs/facturation/
3. Démarrer MAMP
4. Ouvrir : http://localhost:8888/facturation/

INSTALLATION LINUX (Apache)
-----------------------------
1. sudo apt install php apache2
2. Copier "facturation/" dans /var/www/html/facturation/
3. sudo chmod -R 755 /var/www/html/facturation/
4. sudo chmod -R 775 /var/www/html/facturation/data/
5. sudo service apache2 start
6. Ouvrir : http://localhost/facturation/

LANCEMENT VIA VS CODE + PHP SERVER EXTENSION
---------------------------------------------
1. Installer l'extension "PHP Server" dans VS Code
2. Ouvrir le dossier "facturation/" dans VS Code
3. Clic droit sur index.php > "PHP Server: Serve project"
4. L'application s'ouvre dans votre navigateur

PERMISSIONS DES FICHIERS (important !)
----------------------------------------
Le dossier "data/" doit être accessible en écriture par PHP.
Sur Linux/macOS :
    chmod -R 775 facturation/data/
Sur Windows (XAMPP/WAMP) : les permissions sont automatiques.

CONNEXION PAR DÉFAUT
---------------------
Identifiant : admin
Mot de passe : password

⚠ CHANGEZ ce mot de passe dès la première connexion !
(Modules > Admin > Modifier le compte)

STRUCTURE DU PROJET
--------------------
facturation/
├── index.php                     ← Page d'accueil / tableau de bord
├── config/
│   └── config.php                ← Configuration globale (TVA, chemins...)
├── auth/
│   ├── login.php                 ← Page de connexion
│   ├── logout.php                ← Déconnexion
│   └── session.php               ← Gestion des sessions PHP
├── modules/
│   ├── produits/
│   │   ├── enregistrer.php       ← Enregistrement/modification produit
│   │   ├── lire.php              ← API JSON : recherche par code-barres
│   │   └── liste.php             ← Liste de tous les produits
│   ├── facturation/
│   │   ├── nouvelle-facture.php  ← Interface de caisse (scan + panier)
│   │   ├── calcul.php            ← Validation et sauvegarde de la facture
│   │   └── afficher-facture.php  ← Affichage et impression d'une facture
│   └── admin/
│       ├── gestion-comptes.php   ← Liste des utilisateurs
│       ├── ajouter-compte.php    ← Création d'un compte
│       └── supprimer-compte.php  ← Suppression/désactivation de compte
├── data/                         ← Fichiers de persistance JSON
│   ├── produits.json
│   ├── factures.json
│   └── utilisateurs.json
├── includes/
│   ├── header.php                ← En-tête HTML et barre de navigation
│   ├── footer.php                ← Pied de page
│   ├── fonctions-auth.php        ← Fonctions d'authentification et RBAC
│   ├── fonctions-produits.php    ← Fonctions CRUD produits
│   └── fonctions-factures.php    ← Fonctions CRUD factures et calculs
├── assets/
│   ├── css/style.css             ← Feuille de style principale
│   └── js/scanner.js             ← Intégration QuaggaJS (caméra)
└── rapports/
    ├── rapport-journalier.php    ← Rapport du jour
    └── rapport-mensuel.php       ← Rapport mensuel

RÔLES ET PERMISSIONS
---------------------
  Caissier        : Créer des factures, scanner des produits
  Manager         : + Enregistrer/modifier des produits, voir les rapports
  Super Admin     : + Gérer les comptes utilisateurs

UTILISATION DU SCANNER DE CODES-BARRES
----------------------------------------
1. Aller sur "Nouvelle Facture" ou "Enregistrer un produit"
2. Cliquer sur "Activer la caméra"
3. Autoriser l'accès à la caméra dans votre navigateur
4. Pointer vers le code-barres du produit
5. La valeur est automatiquement détectée et remplie

Note : Le scanner utilise QuaggaJS (chargé depuis Internet).
       En cas de problème, utilisez la "Saisie manuelle".

CODES-BARRES COMPATIBLES
--------------------------
EAN-13, EAN-8, Code 128, Code 39, UPC-A, UPC-E

DÉPENDANCES EXTERNES (chargées depuis CDN)
-------------------------------------------
- QuaggaJS 0.12.1 : https://cdn.jsdelivr.net/npm/quagga@0.12.1/

TAUX DE TVA
-----------
Configuré dans config/config.php :
    define('TVA_TAUX', 0.18);  // 18%

Pour modifier : changer la valeur et recharger la page.

PROBLÈMES FRÉQUENTS
--------------------
❌ "La caméra ne fonctionne pas"
   → Utiliser http://localhost (pas une IP type 192.168...)
   → Autoriser la caméra dans les paramètres du navigateur
   → Essayer Chrome ou Edge (meilleure compatibilité)

❌ "Impossible d'écrire dans data/"
   → Vérifier les permissions du dossier data/ (chmod 775 sur Linux)

❌ "Page blanche ou erreur PHP"
   → Vérifier que PHP 8+ est installé
   → Activer les erreurs : error_reporting(E_ALL) dans config.php

====================================================
  Bonne chance pour votre travail pratique !
  FREEDOM — UPC 2025-2026
====================================================
