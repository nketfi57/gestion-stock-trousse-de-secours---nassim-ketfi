# 🏥 Gestion Trousse de Soins

Système de gestion en temps réel pour le suivi d'une trousse de premiers secours. Permet à plusieurs utilisateurs de voir et prendre du matériel médical de manière synchronisée via Firebase.

## ✨ Fonctionnalités

- 📦 **Gestion de stock en temps réel** - Synchronisation instantanée entre tous les utilisateurs
- 📍 **Suivi par lieu** - Enregistrement du lieu de prise du matériel (infirmerie, bureau, terrain...)
- 🔐 **Panel administrateur** - Accès protégé par mot de passe pour gérer les stocks
- 📊 **Historique complet** - Logs détaillés avec lieu, article, quantité et horodatage
- 🛒 **Système de panier** - Sélection multiple d'articles avant validation
- 📱 **Design responsive** - Fonctionne sur mobile, tablette et desktop
- 🎨 **Interface moderne** - Design clean et professionnel

## 🚀 Démo en ligne

👉 [Voir la démo](https://votre-username.github.io/gestion-trousse-soins)

## 📋 Prérequis

- Un compte [Firebase](https://firebase.google.com/)
- Un navigateur web moderne

## 🛠️ Installation

### 1. Cloner le repository

```bash
git clone https://github.com/votre-username/gestion-trousse-soins.git
cd gestion-trousse-soins
```

### 2. Configurer Firebase

1. Créez un projet sur [Firebase Console](https://console.firebase.google.com/)
2. Activez **Firestore Database** en mode test
3. Dans les paramètres du projet, récupérez vos clés de configuration
4. Ouvrez `index.html` et remplacez la configuration Firebase (ligne ~365) :

```javascript
const firebaseConfig = {
    apiKey: "VOTRE_API_KEY",
    authDomain: "VOTRE_PROJECT.firebaseapp.com",
    projectId: "VOTRE_PROJECT_ID",
    storageBucket: "VOTRE_PROJECT.appspot.com",
    messagingSenderId: "VOTRE_ID",
    appId: "VOTRE_APP_ID"
};
```

### 3. Configurer les règles Firestore

Dans Firebase Console → Firestore Database → Règles :

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /stock/{document} {
      allow read, write: if true;
    }
    match /logs/{document} {
      allow read, write: if true;
    }
  }
}
```

### 4. Lancer l'application

Ouvrez simplement `index.html` dans votre navigateur, ou déployez sur GitHub Pages.

## 📦 Contenu de la trousse

L'application est pré-configurée avec 27 articles :

- Sprays désinfectants (chlorhexidine, alcool)
- Compresses stériles
- Bandes et pansements
- Gel hydroalcoolique
- Gants vinyle
- Matériel de premiers secours (ciseaux, pince, couverture de survie)
- Serviettes médicales (arnica, anti-brûlure, anti-moustique)
- Sérum physiologique
- Masque d'insufflation
- Et plus...

## 🔐 Accès Administrateur

**Mot de passe par défaut** : `Congobrazzaville28@`

⚠️ **Important** : Changez le mot de passe dans le code (ligne ~367) avant de déployer en production :

```javascript
const ADMIN_PASSWORD = 'VotreMotDePasse';
```

## 📱 Utilisation

### Pour les utilisateurs

1. Entrez le lieu de prise sur la page d'accueil (ex: Infirmerie, Bureau A, Terrain de sport...)
2. Cliquez sur "Se connecter"
3. Sélectionnez les articles et quantités souhaitées
4. Cliquez sur "Prendre" pour ajouter au panier
5. Validez votre sélection avec "Valider la prise"

### Pour l'administrateur

1. Cliquez sur "Accès Administrateur"
2. Entrez le mot de passe
3. Gérez les stocks et consultez l'historique complet (lieu, article, quantité, date/heure)

## 🌐 Déploiement sur GitHub Pages

1. Créez un repository sur GitHub
2. Poussez votre code :

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/votre-username/gestion-trousse-soins.git
git push -u origin main
```

3. Dans les paramètres du repository → Pages
4. Sélectionnez la branche `main` et le dossier `/root`
5. Votre site sera disponible à `https://votre-username.github.io/gestion-trousse-soins`

## 🎨 Personnalisation

### Couleurs

Modifiez les variables CSS (ligne ~12 de `index.html`) :

```css
:root {
    --primary: #2563eb;
    --success: #10b981;
    --warning: #f59e0b;
    --danger: #ef4444;
}
```

### Articles de la trousse

Éditez l'objet `initialStock` (ligne ~370) pour ajouter, modifier ou supprimer des articles.

## 📄 Structure du projet

```
gestion-trousse-soins/
├── index.html          # Application complète (HTML + CSS + JS)
├── README.md           # Documentation
├── LICENSE             # Licence MIT
└── .gitignore          # Fichiers à ignorer
```

## 🔒 Sécurité

⚠️ **Attention** : Les règles Firestore actuelles permettent un accès en lecture/écriture total. Pour un environnement de production, renforcez la sécurité :

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /stock/{document} {
      allow read: if true;
      allow write: if request.auth != null;
    }
    match /logs/{document} {
      allow read: if request.auth != null;
      allow write: if request.auth != null;
    }
  }
}
```

## 🤝 Contribution

Les contributions sont les bienvenues ! N'hésitez pas à ouvrir une issue ou une pull request.

## 📝 Licence

Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

## 🙏 Remerciements

- [Firebase](https://firebase.google.com/) pour la base de données temps réel
- [Font Awesome](https://fontawesome.com/) pour les icônes (via emojis Unicode)

## 📞 Support

Pour toute question ou problème :
- Ouvrez une [issue](https://github.com/votre-username/gestion-trousse-soins/issues)
- Contactez-moi directement

---

Fait avec ❤️ pour faciliter la gestion des trousses de premiers secours