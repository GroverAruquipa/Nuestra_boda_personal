# Notre mariage · Grover & Laura

Site privé pour préparer le mariage à distance : tâches, invités, fournisseurs, idées et questions, déroulement du jour J, deux horloges (une par ville), compte à rebours et bouton de câlins.

Le site est en français par défaut ; le bouton FR · ES · EN change la langue.

## Publication (GitHub Pages)

Dans le dépôt : **Settings → Pages → Build and deployment → Source : Deploy from a branch**, branche `main`, dossier `/ (root)`, puis **Save**. Le site est à `https://groveraruquipa.github.io/Nuestra_boda_personal/`.

Sans la synchronisation ci-dessous, chacun voit seulement ce qu'il enregistre dans son propre navigateur.

## Voir les mêmes données à deux (Firebase, gratuit)

1. Créer un projet sur <https://console.firebase.google.com>.
2. **Authentication → Sign-in method → Google → Enable**, et ajouter `groveraruquipa.github.io` dans **Authorized domains**.
3. **Firestore Database → Create database** (mode production, région `northamerica-northeast1`, Montréal).
4. Dans **Rules**, coller `firestore.rules` avec vos deux adresses Gmail, puis publier.
5. **Project settings → Your apps → Web (`</>`)**, copier l'objet `firebaseConfig`.
6. Dans `index.html`, remplacer `const FIREBASE_CONFIG = null;` par cet objet, puis pousser le changement.

La clé `apiKey` n'est pas secrète : ce sont les règles de l'étape 4 qui protègent les données. Si vous modifiez au même moment, la dernière modification enregistrée l'emporte.

## Utilisation

- **Je suis …** : chacun choisit qui il est sur son téléphone.
- **Réglages** : noms, villes, fuseaux horaires, date (le jour est facultatif) et lieu.
- **Effacer les exemples** : retire les invités, fournisseurs, idées et horaires d'exemple.
- Touchez une photo pour l'agrandir.
