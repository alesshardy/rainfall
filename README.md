# rainfall

Write-ups et solutions du projet **rainfall** (42), un wargame d'exploitation binaire sur x86 Linux. Chaque niveau est un binaire SUID vulnérable : l'objectif est de l'exploiter pour lire le mot de passe du niveau suivant et progresser en escalade de privilèges, de `level0` jusqu'au dernier niveau, en passant par 4 niveaux bonus.

Le sujet original du projet se trouve dans [rainfall.pdf](rainfall.pdf).

## Structure

Chaque dossier `levelX/` et `bonusX/` contient :

- `source` — le code source (C/C++) du binaire vulnérable
- `flag` — le mot de passe récupéré pour ce niveau
- `walkthrough` — l'explication (en français) de la vulnérabilité et de son exploitation

## Niveaux

| Niveau | Vulnérabilité |
|---|---|
| level0 | Reverse d'un binaire SUID, comparaison d'argument à désassembler |
| level1 | Buffer overflow via `gets()`, écrasement de l'adresse de retour |
| level2 | Buffer overflow via `gets()` avec contournement d'une vérification d'adresse |
| level3 | Format string (`printf(buffer)`) pour écraser une variable globale |
| level4 | Format string via pointeur de fonction, écriture d'une valeur précise en mémoire |
| level5 | Buffer overflow, redirection de l'adresse de retour vers une fonction shell |
| level6 | Buffer overflow écrasant un pointeur de fonction sur le tas |
| level7 | Overflow d'un buffer global corrompant des pointeurs de structures sur le tas |
| level8 | Corruption de tas (heap overflow / use-after-free) |
| level9 | Détournement de vtable C++ via overflow d'un attribut |
| bonus0 | Overflow en chaîne entre plusieurs buffers de la pile |
| bonus1 | Contrôle de la taille d'un `memcpy` via un argument utilisateur |
| bonus2 | `strcpy`/`strcat` dépendant d'une variable d'environnement (`LANG`) |
| bonus3 | Off-by-one sur un index de tableau contrôlé par l'utilisateur |

## Avertissement

Les `flag` sont spécifiques aux instances de VM utilisées pendant la résolution du projet et n'ont aucune valeur en dehors de cet environnement. Ce dépôt est fourni à titre pédagogique (apprentissage de l'exploitation binaire).
