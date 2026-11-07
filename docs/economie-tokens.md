# Économie de tokens — tenir le Bureau à l'abri du « context creep »

*[English version → token-economy.md](token-economy.md)*

Chaque fichier qu'un agent lit coûte des tokens, et chaque token de vieux contexte dilue la tâche en cours. Un Bureau qui grossit sans limite devient plus lent, plus cher et moins précis. Ces règles le gardent léger. Chacune est écrite pour être **vérifiable**.

## A. Ce qu'un agent lit

| # | Règle | Test |
|---|---|---|
| A1 | **Lire le minimum au début de session :** `ETAT.md` + `regles/<agent>.md` + **seulement les 2 messages les plus récents** du projet. Jamais tout l'historique. | L'amorce liste exactement ces fichiers. Un agent qui dit avoir « lu tous les messages » a échoué. |
| A2 | **N'ouvrir un fichier plus ancien que par son nom**, quand un message ou `ETAT.md` y renvoie. Pas de navigation. | Chaque ancien fichier ouvert est cité par son chemin dans un message récent ou dans `ETAT.md`. |
| A3 | **Un sujet = un fichier.** On le met à jour ; on ne le duplique jamais. | Chercher le nom du sujet donne un seul fichier de travail (plus son archive). |
| A4 | **Des journaux, pas des captures d'écran.** Préférer la sortie texte (journal, résultat de commande, texte de la page) aux images. Capture seulement quand la mise en page *est* la question. | Les relectures citent une ligne de journal ou un extrait de texte, pas une image, sauf vérification visuelle. |

## B. Ce qu'un agent écrit

| # | Règle | Test |
|---|---|---|
| B1 | **Le clavardage est la sonnette :** 1 à 3 lignes + le chemin du fichier. Jamais de contenu collé dans le clavardage. | Aucun message de plus de 3 lignes ; chacun contient un chemin. |
| B2 | **`ETAT.md` est plafonné** (ex. 150 lignes). Au-delà : compacter — résumer le terminé en une ligne chacun, déplacer le détail dans `archive/ETAT-AAAA-MM-JJ.md`. | `wc -l ETAT.md` ≤ 150. |
| B3 | **Archivage automatique des messages de plus de 30 jours** (de `messages/` vers `archive/`). | Aucun fichier de `messages/` n'a plus de 30 jours. Voir le script ci-dessous. |
| B4 | **Notes de passation courtes** (≤ 15 lignes : fait / pas fait / prochaine étape / fichiers) plutôt que prolonger une session. | La note de passation existe et fait ≤ 15 lignes. |

## C. Comment se déroulent les sessions

| # | Règle | Test |
|---|---|---|
| C1 | **Session fraîche par chantier.** Un livrable = une nouvelle session qui repart de A1. On ne traîne pas une longue conversation d'une tâche à l'autre. | Un nouveau livrable ne commence jamais dans une session qui en a déjà terminé un autre. |
| C2 | **Fermer une session qui s'allonge** (ex. elle a déjà été résumée/compactée une fois, ou relit des fichiers déjà lus) : écrire une passation (B4), fermer, repartir à neuf. | Les sessions compactées deux fois sont rares ; chacune a sa note de passation. |
| C3 | **Des scripts réutilisables, pas du travail refait par l'IA.** Si un agent fait deux fois la même tâche mécanique (renommer, vérifier des liens, archiver, formater), il écrit un script une fois et l'exécute ensuite. | Les tâches récurrentes renvoient à un fichier dans `scripts/` (ou votre dossier d'outils). |

## D. Quel modèle fait quoi

| # | Règle | Test |
|---|---|---|
| D1 | **Router selon la taille de la tâche :** petit modèle rapide pour le tri, le classement, les veilles, les vérifications oui/non ; gros modèle pour la rédaction, l'architecture, les relectures difficiles. | Chaque tâche planifiée indique son modèle ; les veilles ne tournent jamais sur le plus gros modèle. |
| D2 | **Mode éco :** l'agent de clavardage exécute les étapes de routine ; l'agent code arbitre seulement (relit, décide, gère les exceptions). On ne dépense pas l'agent coûteux sur du mécanique. | Le journal de l'agent code est surtout des relectures et décisions, pas des modifications de routine. |

## E. Budgets et freins

| # | Règle | Test |
|---|---|---|
| E1 | **Chaque boucle a un budget :** nombre max d'itérations, durée max et/ou coût max, écrit dans la tâche. | Aucune tâche planifiée ni boucle de reprise sans limite écrite. |
| E2 | **Freins :** s'arrêter et rapporter quand le budget est atteint, quand la même erreur revient deux fois, ou quand rien n'a changé depuis la dernière exécution. Le silence vaut mieux qu'un rapport répété. | Les journaux de boucle montrent une raison d'arrêt ; aucune tâche n'a dépassé sa limite. |

## Exemple : script d'archivage à 30 jours

PowerShell :
```powershell
$bureau = "<CHEMIN DU BUREAU>"
$limite = (Get-Date).AddDays(-30)
Get-ChildItem "$bureau\messages" -Recurse -File -Filter *.md |
  Where-Object { $_.LastWriteTime -lt $limite } |
  ForEach-Object { Move-Item $_.FullName "$bureau\archive\" }
```

Bash :
```bash
BUREAU="<CHEMIN DU BUREAU>"
find "$BUREAU/messages" -name '*.md' -mtime +30 -exec mv {} "$BUREAU/archive/" \;
```

À lancer selon un horaire (hebdomadaire suffit), ou à demander à l'agent constructeur en début de semaine.

## À ajouter à l'amorce

```
Économie de tokens : lis seulement ETAT.md, regles/<ton-agent>.md et les 2 messages les plus récents. N'ouvre un fichier plus ancien que si un message le nomme. Messages de 1 à 3 lignes avec un chemin. Si ETAT.md dépasse 150 lignes, compacte-le. Préfère les journaux aux captures d'écran. Si tu refais une tâche mécanique, écris un script. Chaque boucle a un budget ; arrête-toi quand il est atteint ou que rien n'a changé.
```
