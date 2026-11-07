# Bureau des Agents — à lire d'abord

Ce dossier est le bureau partagé de vos agents. Chaque agent lit ce fichier au début de chaque session.

## Les 6 règles

1. **Un sujet = un endroit.** Un sujet vit dans exactement un fichier. Jamais deux copies. On met à jour le fichier ; on ne le duplique pas.
2. **Le clavardage est la sonnette.** Un message fait 1 à 3 lignes : c'est quoi, où est le fichier. Jamais le contenu lui-même.
3. **Le fichier fait foi.** Si le clavardage et le fichier se contredisent, le fichier gagne. Si deux fichiers se contredisent, l'entrée datée la plus récente de `REGISTRE.md` tranche.
4. **Un responsable par livrable.** Un agent construit ; un autre relit. Jamais deux constructeurs sur le même fichier en même temps.
5. **Rien d'externe sans GO.** Aucun envoi, publication, paiement ou suppression sans le feu vert explicite de l'humain pour cette action précise. Un GO ne se transfère pas à une action semblable.
6. **Citez chaque fait.** Chaque affirmation porte sa source (chemin de fichier ou URL) et sa date. Sans source, c'est une supposition — dites-le.

## Où va quoi

| Quoi | Où |
|---|---|
| Ce qui est en cours, maintenant | `ETAT.md` |
| Ce qui a été décidé, quand, par qui | `REGISTRE.md` (ajout seulement) |
| Règles permanentes d'un agent | `regles/<agent>.md` (seul l'humain modifie) |
| Une note d'un agent à un autre | `messages/general/AAAA-MM-JJ_de-a_sujet.md` |
| Travail de projet | `projets/<projet>/` |
| Terminé / remplacé | `archive/` |

## Début de session (chaque agent)

1. Lire `ETAT.md` et son propre `regles/<agent>.md` (ce fichier à la première session).
2. Lire seulement les 2 notes les plus récentes de `messages/general/` ; n'ouvrir un fichier plus ancien que s'il est nommé. Voir `docs/economie-tokens.md` dans le kit.
3. Faire le travail. Mettre à jour le fichier dont vous êtes responsable. Laisser une note courte si quelqu'un d'autre doit agir.
4. Déplacer les messages traités dans `archive/`.
