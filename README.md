# Réseau Social en C

## Description

Application console de réseau social développée en C, permettant de gérer des utilisateurs, leurs relations (amis et abonnements) et leurs publications. Le système utilise une structure d'arbre binaire de recherche (BST) pour organiser les utilisateurs et offre des fonctionnalités complètes de gestion de réseau social.

## Auteurs

- **Ritej Louati**
- **Emna Khmiri**

## Fonctionnalités

### Gestion des Utilisateurs
- ✅ Création d'utilisateurs avec ID unique et nom
- ✅ Suppression d'utilisateurs
- ✅ Recherche d'utilisateurs par ID
- ✅ Affichage de tous les utilisateurs (ordre croissant par ID)

### Gestion des Relations
- 👥 **Amis** : Relations bidirectionnelles (si A est ami avec B, alors B est ami avec A)
  - Ajouter un ami
  - Supprimer un ami
- 📢 **Abonnements** : Relations unidirectionnelles (suivre un utilisateur)
  - Suivre un utilisateur
  - Arrêter de suivre un utilisateur

### Publications
- 📝 Publier des messages avec horodatage automatique
- 📰 Afficher la timeline d'un utilisateur (publications des amis, triées par date)

### Statistiques
- 📊 Nombre total d'utilisateurs
- 🏆 Utilisateur le plus actif (nombre de publications)
- ⭐ Utilisateur le plus suivi (nombre d'abonnés)
- 🤝 Utilisateur le plus sociable (nombre d'amis)

### Persistance des Données
- 💾 Sauvegarde automatique des utilisateurs, relations et publications
- 📂 Chargement automatique au démarrage
- **Fichiers générés** :
  - `utilisateurs.bin` : Données des utilisateurs (format binaire)
  - `relations.txt` : Relations amis et abonnements (format texte)
  - `publications.txt` : Messages publiés (format texte)

## Structure de Données

### Types Principaux

```c
typedef struct User {
    int id;
    char name[30];
    Relation *amis;              // Liste d'amis
    Relation *abonnements;       // Liste d'abonnements
    Publication *publications;   // Liste de publications
    struct User *left;           // Sous-arbre gauche (BST)
    struct User *right;          // Sous-arbre droit (BST)
} User;
```

### Organisation
- **Arbre Binaire de Recherche (BST)** : Les utilisateurs sont organisés par ID pour une recherche efficace en O(log n) dans le cas moyen
- **Listes chaînées** : Relations et publications stockées en listes dynamiques

## Compilation et Exécution

### Prérequis
- Compilateur C (GCC recommandé)
- Système d'exploitation Windows (utilise `windows.h`)

### Compilation
```bash
gcc interface.c -o reseau_social.exe
```

### Exécution
```bash
./reseau_social.exe
```

## Menu Principal

```
=====================================
   Bienvenue dans le reseau social   
=====================================

1. Créer utilisateur
2. Supprimer utilisateur
3. Rechercher utilisateur
4. Gérer les relations
5. Publier un message
6. Afficher les utilisateurs
7. Afficher les statistiques
8. Afficher la timeline
9. Enregistrer & Quitter
```

## Utilisation

### Créer un Utilisateur
1. Choisir l'option 1
2. Entrer un ID unique (nombre entier)
3. Entrer le nom de l'utilisateur

### Ajouter un Ami
1. Choisir l'option 4
2. Sélectionner l'option 1 (Ajouter ami)
3. Entrer votre ID
4. Entrer l'ID de l'ami à ajouter

### Publier un Message
1. Choisir l'option 5
2. Entrer votre ID
3. Entrer le message
4. La date et l'heure sont automatiquement enregistrées

### Afficher la Timeline
1. Choisir l'option 8
2. Entrer votre ID
3. Voir les publications de vos amis triées par date (plus récentes en premier)

## Format des Fichiers

### relations.txt
```
ID: 1
Amis: 2 3
Abonnements: 4 5

ID: 2
Amis: 1
Abonnements:
```

### publications.txt
```
1;2024-12-09 14:30:00;Bonjour tout le monde!
2;2024-12-09 15:45:00;Ma première publication
```

## Fonctionnalités Techniques

- **Encodage UTF-8** : Support des caractères français
- **Gestion mémoire** : Allocation dynamique avec libération appropriée
- **Validation des entrées** : Vérification des données utilisateur
- **Interface console** : Écran clair entre chaque action
- **Tri des publications** : Algorithme de tri à bulles pour la timeline

## Limites

- Taille maximale du nom : 30 caractères
- Taille maximale d'un message : 200 caractères
- Taille maximale de la date : 20 caractères
- Plateforme : Windows uniquement (utilise `windows.h` et `cls`)

## Améliorations Possibles

- 🔧 Support multiplateforme (Linux, macOS)
- 🔍 Recherche par nom d'utilisateur
- 🔐 Système d'authentification
- 💬 Commentaires sur les publications
- ❤️ Système de "J'aime"
- 🔔 Notifications
- 🎨 Interface graphique

## Notes Techniques

- L'arbre BST peut devenir déséquilibré selon l'ordre d'insertion des utilisateurs
- Les relations sont vérifiées pour éviter les doublons
- Un utilisateur ne peut pas être ami avec lui-même
- La suppression d'un utilisateur supprime également toutes ses relations et publications

## License

Projet académique - Libre d'utilisation à des fins éducatives.