# Bureau des Agents — kit de démarrage

*[English version → README.md](README.md)*

Un modèle de dossier partagé pour faire travailler deux agents IA (ou plus) ensemble — typiquement un dans votre clavardage et un sur votre machine (ex. Claude Code). Ils ne peuvent pas se parler directement, alors ils partagent un dossier : **le Bureau**. Chaque tâche est un fichier ; le clavardage n'est que la sonnette ; le fichier fait foi. Rien ne sort sans votre GO.

Générique par design : aucune donnée privée, aucun vrai nom — juste le modèle.

## Démarrage rapide

```bash
git clone https://github.com/VisionCI/agent-office-starter.git
cp -r agent-office-starter/fr "Bureau des Agents"
```

Puis collez [`fr/AMORCE.md`](fr/AMORCE.md) dans chaque agent, une fois.

## Les 6 règles

1. **Un sujet = un endroit.** Un sujet vit dans exactement un fichier. Jamais deux copies.
2. **Le clavardage est la sonnette.** Un message fait 1 à 3 lignes : c'est quoi, où est le fichier. Jamais le contenu lui-même.
3. **Le fichier fait foi.** Si le clavardage et le fichier se contredisent, le fichier gagne.
4. **Un responsable par livrable.** Un agent construit ; l'autre relit. Jamais deux constructeurs.
5. **Rien d'externe sans GO.** Aucun envoi, publication, paiement ou suppression sans votre feu vert explicite pour cette action précise.
6. **Citez chaque fait.** Chaque affirmation porte son fichier source et sa date. Sans source, c'est une supposition.

## Contenu

```
fr/
  00_LISEZ-MOI.md        <- les règles, en entier
  ETAT.md                <- ce qui est en cours, maintenant
  REGISTRE.md            <- journal des décisions (ajout seulement)
  AMORCE.md              <- à coller une fois dans chaque agent
  regles/
    roles.md             <- les 4 rôles
    constructeur.md      <- règles permanentes par agent (vous seul les modifiez)
    operateur.md
  messages/
    GABARIT.md           <- gabarits de messages
    general/             <- les notes « sonnette »
  projets/<projet>/      <- un dossier par projet
  archive/               <- messages traités, anciens états
```

## Les 4 rôles

| Rôle | Travail | Vit généralement dans |
|---|---|---|
| Stratège | Décide quoi faire, dans quel ordre. Possède le plan. | Agent de clavardage |
| Constructeur | Fabrique — code, pages, fichiers. | Agent machine |
| Veilleur | Vérifie les sources selon un horaire, rapporte seulement le nouveau. Silence sinon. | Agent de clavardage (planifié) |
| Éditeur | Vérifie avant que quoi que ce soit sorte. Lit la vraie chose, jamais le résumé. | Agent de clavardage |

## La boucle quotidienne

Matin : le Veilleur rapporte le nouveau. Journée : le Stratège choisit, le Constructeur construit, l'Éditeur vérifie. Soir : un court débrief — livré, bloqué, en attente de votre GO.

## Commencez ce soir

1. Copiez le dossier.
2. Collez l'amorce dans chaque agent.
3. Choisissez UNE veille — la plus petite utile.
4. Ne publiez rien avant que la règle de l'Éditeur ait attrapé une erreur. Elle en attrapera une.

---

Par [Vision CI](https://visionci.ca) — Québec. Vidéos : [@visionaivideo](https://www.instagram.com/visionaivideo/).
Licence [CC BY 4.0](LICENSE) : réutilisez et adaptez librement, en gardant le crédit.
