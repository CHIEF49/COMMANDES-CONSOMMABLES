# Commande consommables

Application web d'une seule page pour gérer la liste de commande des consommables de l'atelier, partagée avec toute l'équipe.

## Fonctionnement

- **Catalogue** : toutes les pièces connues (nom, référence, appareil).
- **À commander** : les pièces de la prochaine commande, avec quantité et mention « Urgent ». « Retirer de la commande » renvoie une pièce au catalogue.
- **Vider la liste à commander** : remet en une fois toutes les pièces à commander dans le catalogue (avec confirmation).
- Les pièces sont regroupées par fabricant (ELITECH, SKYLA, BIONOTE, TOSOH, EDIF, NIHON KOHDEN, URIT, Autres) puis par appareil.
- **PDF liste** : exporte la liste affichée, avec logo, regroupée par fabricant, urgents en rouge.

## Fichier

- `index.html` : toute l'application (HTML, CSS, JavaScript et logo intégrés).

## Remarque

La liste partagée et le téléchargement du PDF reposent sur les fonctions des artefacts claude.ai (base de données partagée et téléchargements). Ouverte en dehors de claude.ai, la page s'affiche mais indique que le registre partagé n'est pas disponible.
