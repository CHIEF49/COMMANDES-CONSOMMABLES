# Commande consommables

Application web d'une seule page pour gérer la liste de commande des consommables de l'atelier, partagée avec toute l'équipe.

## Fonctionnement

- **Catalogue** : toutes les pièces connues (nom, référence, appareil).
- **À commander** : les pièces de la prochaine commande, avec quantité et mention « Urgent ». « Retirer de la commande » renvoie une pièce au catalogue.
- **Vider la liste à commander** : remet en une fois toutes les pièces à commander dans le catalogue (avec confirmation).
- Les pièces sont regroupées par fabricant (ELITECH, SKYLA, BIONOTE, TOSOH, EDIF, NIHON KOHDEN, URIT, Autres) puis par appareil.
- **PDF liste** : exporte la liste affichée, avec logo, regroupée par fabricant, urgents en rouge.

## Fichiers

- `index.html` : toute l'application (HTML, CSS, JavaScript et logo intégrés).
- `firebase-config.js` : la configuration Firebase du projet (à remplir).
- `firebase.json`, `.firebaserc`, `firestore.rules` : hébergement Firebase et règles de la base.
- `outils/import-catalogue.html` et `outils/catalogue.json` : import du catalogue (155 pièces) dans Firestore.
- `.github/workflows/firebase.yml` : mise en ligne automatique sur Firebase à chaque modification.

## Mise en place sur Firebase (une seule fois)

1. **Créer le projet** sur https://console.firebase.google.com (ou reprendre un projet existant).
2. **Créer la base** : menu *Firestore Database* → *Créer une base de données* → mode production, région `europe-west`.
3. **Ajouter une application Web** : ⚙️ *Paramètres du projet* → *Vos applications* → icône `</>`. Copier l'objet `firebaseConfig` dans `firebase-config.js` (à la place de `null`).
4. **Indiquer l'identifiant du projet** dans `.firebaserc` (à la place de `VOTRE-ID-PROJET`).
5. **Donner la clé à GitHub** : ⚙️ *Paramètres du projet* → *Comptes de service* → *Générer une nouvelle clé privée*. Dans GitHub : *Settings* → *Secrets and variables* → *Actions* → *New repository secret*, nom `FIREBASE_SERVICE_ACCOUNT`, valeur = tout le contenu du fichier JSON téléchargé.
6. Envoyer les modifications sur `main` : l'application et les règles sont mises en ligne automatiquement (onglet *Actions* de GitHub).
7. **Importer le catalogue** : ouvrir `https://VOTRE-ID-PROJET.web.app/outils/import-catalogue.html` et cliquer sur *Importer le catalogue*.

## Sécurité

Les règles (`firestore.rules`) laissent toute personne qui a l'adresse lire et modifier la liste, sans connexion, mais seulement dans la collection `commandes` et avec des fiches de forme valide. Pour réserver l'accès à l'équipe, il faudra ajouter une connexion (par exemple avec un compte Google).

## Remarque

L'application fonctionne aussi comme artefact claude.ai : elle utilise alors la base de claude.ai au lieu de Firebase.
