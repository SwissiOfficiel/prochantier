# Installer l'application — guide pas à pas

Durée : environ 45 minutes. Tout est gratuit. Il te faut un compte Google (Gmail).

## Étape 1 — Créer la base de données Firebase
1. Va sur https://console.firebase.google.com et connecte-toi avec ton compte Google.
2. Clique « Créer un projet », donne un nom (ex. le nom de ton entreprise), refuse Google Analytics, puis « Créer ».
3. Menu de gauche « Build » > **Authentication** > « Commencer » > onglet « Sign-in method » > active **E-mail/Mot de passe**.
4. Onglet « Users » > « Ajouter un utilisateur » : crée un compte (e-mail + mot de passe) pour chaque personne qui utilisera l'app, toi compris.
5. « Build » > **Firestore Database** > « Créer une base de données » > choisis la région **eur3 (Europe)** > mode **production** > « Activer ».
6. Dans Firestore, onglet **Règles** : efface tout, colle le contenu du fichier `regles-firestore.txt`, puis clique « Publier ».
7. Roue dentée ⚙️ (en haut à gauche) > « Paramètres du projet » > en bas « Vos applications » > icône **</>** (Web) > donne un nom > « Enregistrer l'application ». Firebase affiche un bloc `firebaseConfig = { apiKey: ..., authDomain: ..., ... }`. **Garde cette page ouverte.**

## Étape 2 — Mettre ta configuration dans l'app
1. Ouvre le fichier `config.js` (avec le Bloc-notes).
2. Remplace chaque `COLLE_ICI_...` par la valeur correspondante affichée par Firebase (garde les guillemets). Enregistre.

## Étape 3 — Mettre l'app en ligne (GitHub Pages)
1. Crée un compte gratuit sur https://github.com.
2. « New repository » : nom simple sans espace (ex. `app`), laisse **Public**, « Create repository ».
3. « uploading an existing file » : glisse **tout le contenu** du dossier de l'app (fichiers ET dossiers `bons`, `calculatrice`, `carnet`, `chantiers`, `machine`, `rapport`, `ressources`). Clique « Commit changes ».
4. Onglet **Settings** > **Pages** > « Branch : main » + dossier « / (root) » > « Save ».
5. Après 1 à 2 minutes, l'adresse apparaît : `https://tonpseudo.github.io/app/`.
6. Retourne dans Firebase > Authentication > **Settings** > « Domaines autorisés » > « Ajouter un domaine » : ajoute `tonpseudo.github.io`.

## Étape 4 — Installer sur les téléphones
- **Android** : ouvre l'adresse dans Chrome > menu ⋮ > **« Installer l'application »**. (Ou installe l'APK, voir plus bas.)
- **iPhone** : ouvre l'adresse dans **Safari** > bouton Partager > **« Sur l'écran d'accueil »**.
Connecte-toi avec l'e-mail et le mot de passe créés à l'étape 1.

## Étape 5 (facultatif) — Fichier APK pour Android
1. Va sur https://www.pwabuilder.com, colle l'adresse de ton app, « Start ».
2. « Package for stores » > **Android** > « Generate ». Télécharge le fichier `.zip`, il contient l'`.apk`.
3. Envoie l'APK aux employés. Sur leur téléphone : ouvrir le fichier, autoriser « sources inconnues » une seule fois, installer.

## Mises à jour
Quand une nouvelle version de l'app est livrée : GitHub > ton dépôt > « Add file » > « Upload files » > glisse les fichiers modifiés > « Commit changes ». **Ne remplace jamais `config.js`** (garde le tien). Ensuite, ferme et rouvre l'app. Si l'ancienne version reste : paramètres Chrome > Paramètres du site > ton app > « Effacer les données ».

## En cas de problème
- Écran bleu qui ne se charge pas : vérifie `config.js` (valeurs bien collées, guillemets) et le domaine autorisé (étape 3.6).
- « Erreur de connexion » : le compte n'existe pas dans Authentication > Users.
- Rien ne se synchronise : les règles Firestore n'ont pas été publiées (étape 1.6).
