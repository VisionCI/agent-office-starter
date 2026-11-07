# Gabarits de messages

Nom de fichier : `messages/general/AAAA-MM-JJ_<de>-a-<a>_<sujet>.md`
Sonnette dans le clavardage (1 à 3 lignes) : `Nouvelle note pour <a> : messages/general/<fichier>.md — <pourquoi en une ligne>.`

---

## 1. Demande

```
DE : <agent>   À : <agent>   DATE : AAAA-MM-JJ   STATUT : OUVERT
SUJET : <court>

Quoi : <la demande, 1 à 3 lignes>
Pourquoi : <l'objectif>
Terminé quand : <critères d'acceptation>
Fichiers : <chemins>
Échéance : <date ou « aucune »>
```

## 2. Livraison (pour relecture)

```
DE : <constructeur>   À : <éditeur>   DATE : AAAA-MM-JJ   STATUT : OUVERT
SUJET : <livrable> prêt pour relecture

Livrable : <chemin ou URL>
Ce qui a changé : <puces>
Comment vérifier : <étapes — ouvrir la vraie chose>
Limites connues : <ou « aucune »>
```

## 3. Verdict de relecture

```
DE : <éditeur>   À : <constructeur>   DATE : AAAA-MM-JJ   STATUT : OUVERT
SUJET : Relecture — <livrable> — OK | À CORRIGER

Vérifié sur : <la vraie page / le vrai fichier, avec date>
Constats : <numérotés, chacun avec sa source>
Verdict : OK (prêt pour le GO humain) | À CORRIGER (liste ci-dessus)
```

## 4. Demande de GO (à l'humain)

```
À : humain   DATE : AAAA-MM-JJ
Action : <exactement ce qui va se passer — envoi / publication / paiement / suppression>
Cible : <où>
Vérifié par : <éditeur> le AAAA-MM-JJ (messages/general/<fichier de relecture>)
Répondez GO pour cette action précise.
```

## 5. Rapport de veille

```
DE : <veilleur>   DATE : AAAA-MM-JJ
Source : <nom/URL>
Nouveau depuis le dernier rapport : <puces, chacune avec lien + date> — ou « rien de nouveau » (alors ne rien envoyer)
```

Une fois traité : mettre `STATUT : TERMINÉ` et déplacer le fichier dans `archive/`.
