# PacketTracer - Système de Suivi de Distribution Pharmaceutique

Une solution complète de suivi de colis développée pour SOREMED (Société de Répartition de Médicaments), composée d'applications de bureau et mobiles avec un système backend centralisé.

## Présentation du Projet

Ce projet répond aux inefficacités du système actuel de gestion des produits pharmaceutiques et parapharmaceutiques de SOREMED en fournissant :
- **Application de Bureau** : Interface conviviale pour les entrepreneurs et administrateurs
- **Application Mobile** : Interface intuitive pour les chauffeurs-livreurs
- **Backend Centralisé** : Gestion des données et synchronisation

## Architecture

La solution suit une architecture à trois niveaux :

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Application   │    │     Backend     │    │   Application   │
│   de Bureau     │◄──►│  (Spring Boot)  │◄──►│     Mobile      │
│    (JavaFX)     │    │                 │    │   (Android)     │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                                 │                    │
                                 ▼                    ▼
                        ┌─────────────────┐    ┌─────────────────┐
                        │     MySQL       │sync│     SQLite      │
                        │   Database      │◄──►│    Database     │
                        └─────────────────┘    └─────────────────┘
```

## Structure du Projet

```
├── DesktopApp/              # Application de Bureau JavaFX
│   ├── src/main/java/
│   │   └── com/example/packet_tracer/
│   │       ├── admin/       # Contrôleurs administrateur
│   │       ├── expediteur/  # Contrôleurs expéditeur
│   │       └── models/      # Modèles de données
│   └── src/main/resources/  # Fichiers FXML et ressources
│
├── PacketTracer/            # Application Mobile Android
│   └── app/src/main/java/
│       └── com/example/packettracer/
│           ├── model/       # Modèles de données
│           └── utils/       # Utilitaires et adaptateurs
│
└── packetTracerBase/        # Backend Spring Boot
    └── src/main/java/
        └── com/example/packettracerbase/
            ├── controller/  # Contrôleurs API REST
            ├── dto/         # Objets de Transfert de Données
            ├── model/       # Modèles d'entités
            ├── repository/  # Couche d'accès aux données
            └── service/     # Logique métier
```

## Technologies Utilisées

### Backend
- **Framework** : Spring Boot
- **Base de données** : MySQL
- **ORM** : Hibernate
- **API** : Services RESTful
- **Sécurité** : Spring Security
- **Outil de build** : Maven

### Application de Bureau
- **Framework** : JavaFX
- **Langage** : Java
- **Outil de build** : Maven

### Application Mobile
- **Plateforme** : Android
- **Langage** : Java/Kotlin
- **Outil de build** : Gradle
- **Client HTTP** : Retrofit + OkHttp
- **Base de données** : Room (SQLite)
- **Analyse JSON** : Gson
- **Lecture de codes-barres** : ZXing

## Fonctionnalités Principales

### Pour les Administrateurs et Entrepreneurs
- Authentification sécurisée avec accès basé sur les rôles
- Gestion des produits et de l'inventaire
- Suivi de colis en temps réel
- Système de reporting complet
- Gestion des chauffeurs et clients
- Optimisation des itinéraires de livraison

### Pour les Chauffeurs-Livreurs
- Interface optimisée pour mobile
- Lecture de codes-barres/QR
- Navigation GPS et optimisation d'itinéraires
- Mises à jour du statut de livraison en temps réel
- Fonctionnalité hors ligne avec synchronisation des données
- Confirmations de livraison numériques

### Fonctionnalités Système
- Gestion centralisée des données
- Synchronisation en temps réel entre les applications
- Contrôle d'accès basé sur les rôles
- Pistes d'audit complètes

## Assurance Qualité et Tests

### Analyse de la Qualité du Code avec SonarQube
- **Métriques de la base de code** : 2 161 lignes de code Java réparties sur 59 classes et 216 fonctions
- **Couverture de code** : Amélioration de 0% à 56,6% grâce à l'implémentation de 195 tests unitaires
- **Réduction de la complexité** : Réduction réussie de la complexité cyclomatique de 36 à 16 dans les fichiers de service critiques
- **Résolution des problèmes** : Traitement de 82 problèmes de maintenabilité et 8 problèmes de fiabilité

### Tests Fonctionnels Automatisés avec Appium
- **Tests mobiles** : Tests boîte noire complets de l'application Android
- **Couverture des tests** : Fonctionnalité de connexion, navigation du tableau de bord et lecture de codes-barres
- **Compatibilité des appareils** : Testé sur Android 12.0 avec processeur HUAWEI Kirin 710F
- **Framework d'automatisation** : Intégration Spring Boot avec Selenium WebDriver

### Tests de Performance avec Apache JMeter
- **Résultats des tests de charge** :
  - **500 utilisateurs** : Taux de réussite de 100%, temps de réponse moyen de 28,65ms, score APDEX de 1,000
  - **2000 utilisateurs** : Taux de réussite de 97,95%, temps de réponse moyen de 2308,84ms, 353,17 transactions/seconde
- **Tests de stress** : Identification des goulots d'étranglement de performance sous charge élevée d'utilisateurs simultanés
- **Analyse réseau** : Surveillance des taux de transfert de données (170,61 KB/sec reçus, 189,18 KB/sec envoyés)

### Intégration DevOps
- **Intégration continue** : Pipeline Jenkins avec analyse SonarQube automatisée
- **Conteneurisation Docker** : Configuration complète de l'environnement de développement
- **Tests automatisés** : Intégration de JaCoCo pour le reporting de couverture de code

## Démarrage Rapide

### Prérequis
- Java 11 ou supérieur
- MySQL 8.0+
- Android Studio (pour l'application mobile)
- Maven 3.6+

### Configuration du Backend
1. Cloner le dépôt
2. Naviguer vers `packetTracerBase/`
3. Configurer la connexion à la base de données dans `application.properties`
4. Exécuter l'application :
   ```bash
   mvn spring-boot:run
   ```

### Configuration de l'Application de Bureau
1. Naviguer vers `DesktopApp/`
2. Construire et exécuter :
   ```bash
   mvn javafx:run
   ```

### Configuration de l'Application Mobile
1. Ouvrir `PacketTracer/` dans Android Studio
2. Synchroniser le projet avec les fichiers Gradle
3. Exécuter sur appareil ou émulateur

## Outils de Développement

- **EDI** : IntelliJ IDEA, Android Studio
- **Analyse de qualité** : SonarQube avec déploiement Docker
- **Outils de test** : Apache JMeter, Appium, JUnit
- **Tests API** : Postman
- **Gestion de base de données** : XAMPP/phpMyAdmin
- **Contrôle de version** : Git
- **CI/CD** : Jenkins avec pipelines automatisés
- **Couverture de code** : JaCoCo
- **Modélisation UML** : Astah UML Community

## Points de Terminaison API

Le backend fournit des API RESTful complètes pour :
- `/api/admins` - Gestion des administrateurs
- `/api/bordoreaux` - Gestion des bordereaux de livraison
- `/api/clients` - Gestion des clients
- `/api/drivers` - Gestion des chauffeurs
- `/api/packets` - Gestion des colis
- `/api/secteurs` - Gestion des secteurs
- `/api/transferts` - Gestion des transferts

## Métriques de Performance

- **Haute disponibilité** : Taux de réussite de 97,95% sous 2000 utilisateurs simultanés
- **Temps de réponse** : Moyenne de 28,65ms pour les opérations standard
- **Qualité du code** : Couverture de test de 56,6% avec amélioration continue
- **Sécurité** : Zéro vulnérabilité critique détectée
- **Évolutivité** : Support de plus de 353 transactions par seconde
