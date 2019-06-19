# Vim

## Summary
- [Normal mode](#normal-mode)
- [Insert mode](#insert-mode)
- [Visual select mode](#visual-select-mode)
- [Command line](#command-line)
- [Manage multiple files](#manage-multiple-files)
- [File directory](#file-directory)
- [Navigation](#navigation)
- [Mark](#mark)
- [Navigate in file](#navigate-in-file)
- [Register](#register)
- [Macros](#macros)
- [Search](#search)
- [Substitution](#substitution)
- [Flags](#flags)
- [Global command](#global-command)
- [Ctags](#ctags)
- [Search project wide](#search-project-wide)
- [Autocompletion](#autocompletion)
- [Spell check](#spell-check)
- [Fugitive](#fugitive)
- [Vim gitgutter](#vim-gitgutter)
- [Autre](#autre)

## Normal mode
`C` Supprime de la position de la ligne jusqu'à la fin et bascule en insertion

`S` Supprime toute la ligne et bascule en insertion

`f{char}` Cherche le caractère sur la ligne sur la droite

`F{char}` Cherche le caractère sur la ligne sur la gauche

`t{char}` Cherche le caractère sur la ligne sur la droite et se place un caractère avant

`T{char}` Cherche le caractère sur la ligne sur la gauche et se place un caractère avant

Note : `f`, `F`, `t`, `T`, servent de _motion_ également  
On peut faire une commande comme `dtX`
Qui supprimera tous les caractères jusqu'au caractères précédent le prochain `X`

`;` Répète la recherche sur la ligne sur la droite

`,` Répète la recherche sur la ligne sur la gauche

`<C-a> ou <C-x>` Sur la ligne incrémentera ou décrémentera le premier digitale rencontré

`zz` Centre la ligne courante verticalement 

## Insert mode
`<C-h>` Supprime le caractère précédent

`<C-w>` Supprime le mot précédent

`<C-u>` Supprime tout ce qui se trouve derrière le curseur

`<C-[>` Retour en mode normal

`<C-r>` 0 Coller en mode insertion

`<C-r>=1+2<CR>` Évalue avant d'insérer (3)

`<c-v>{code} ou <c-v>u{code}` Pour insérer un caractère par son code

## Visual select mode
`gv` Re-sélectionne la dernière sélection

`o` Alterne le curseur aux extrémités de la sélection

`O` Alterne le curseur aux autres extrémités (mode visuel bloc)

## Command line
`:register` Affiche la liste des presses papier

La copie et la suppression empile les caractères dedans  
Pour coller l'avant dernier faire `"1p`  
Pour copier dans presse papier d'une lettre "z", faire `"zyy`

Cette liste commence par le register "" puis "0 ensuite "1 etc

`:1,3p` Print les lignes 1 à 3
`:%p` Toutes les lignes
`:2+1,5-1p` On peut affiner une fourchette de lignes comme ceci

`[range] copy address` ou  
`[range] co address` ou  
`[range] t address` Copie la fourchette ou la ligne à telle ligne, sans passer par le presse papier  
Exemple `:-2,-1t` copie les lignes relatives -2 à -1 à la ligne courante "."

`:move` ou `:m` Identique que `copy` mais coupe.

`:normal` Exécute la commande en mode normal (par ex . ou A; ou une macro)  
`:normal G` Nous déplacera à la fin du document  
--> `:normal v/toto` Sélectionnera toto

`:execute "normal! >>"` Indentera la ligne

`@:` Répète la dernière commande (ligne de commande)

`:[a-z]<C-d>` Provoque la suggestion de commandes en mode commande,
comme tab à condition de définir les options wildmenu et wildmode

`:write` ou `:w` Sauvegarde

`<C-f>` Bascule de _command line_ à _command line window_

`:read!{cmd|ex ls}` Insère la sortie standard de la commande dans le buffer

`[range]!{filtre}` Applique le filtre à une fourchette de lignes.
Les filtres sont des commandes shell, comme sort ou autre.

`:g/pattern/d` Supprime toutes les lignes contenant le pattern.

`:v/pattern/d` Supprime toutes les lignes ne contenant pas le pattern.

## Manage multiple files
### Buffer
`:ls` Liste les buffers

`:bnext` Buffer suivant

`:bprev` Buffer précédent

`:bfirst` Premier buffer

`:blast` Dernier buffer

`:bdelete n1 n2` ou `:N, M bdelete` Supprime les buffers lister (mais ne supprime pas les fichiers)

`:args` Liste les arguments fournit pour ouvrir des fichiers

`:argdo [command]` Exécutera la commande sur toute la liste 

### Split
`:new` Ouvre un split vierge

`:vnew` Ouvre un vsplit vierge

`:sp (file)` Ouvre le fichier dans un nouveau split (horizontal)

`:vsp (file)` Ouvre le fichier dans un nouveau split (vertical)

`<C-w> <C-w>` peut s'écrire `<C-w> w` Passe active le _buffer_ suivant

`<C-w> =` Égalise les fenêtres

`<C-w> _` Maximise la taille de la fenêtre courante horizontalement

`<C-w> |` Maximise la taille de la fenêtre courante verticalement

`<C-w> t` Déplace la fenêtre split en un nouvel onglet 


## File directory

`:edit %` Édite le fichier courant

`:edit %:h` Ouvre le dossier du fichier courant

> Bien configurer son path (dépôt git courant)  
et utiser find de vim.

`:Explore` Viens d'un plugin intégré à Vim "netrw",  
qui permet de lire des fichiers à travers le réseau.

`<C-g>` Nom et statut du fichier

Astuce : Créer le dossier du fichier courant qui est dans une arborescence qui n'existe pas.
`:!mkdir -p %:h`

## Navigation
### Word
`w` Début du prochain mot

`w` Début du prochain mot en ignorant certains caractères

`b` Début du mot précédent

`b` Début du mot précédent en ignorant certains caractères

`e` Fin du mot

`E` Fin du mot en ignorant certains caractères

`gE` Fin du mot précédent

### Text object
Les commandes suivantes sont à précéder d'une action : `v|i|c|d…`
`i{delimiter}` Action à l'intérieur du délimiteur

`a{delimiter}` Délimiteurs incluts

`it` À l'intérieur du tag xml

`at` Le tag xml

`iw` Le mot

`aw` Le mot et l'espace

`iW` Le mot ne s'arrêtant qu'avec un espace

`aW` Le mot avec l'espace, ne finissant qu'avec un espace

`is` La phrase

`as` La phrase avec l'espace

`ip` Le paragraphe

`ap` Le paragraphe et un saut de ligne 

## Mark
`m{a-z}` Définit une marque sur la lettre choisie

`{a-z}` Positionne le curseur sur la marque définie à la marque

Les marks avec une lettre en majuscule sont dites globales,  
atteignable depuis un autre fichier.  

### Automatics marks
| Raccourcis | Contenu du buffer                         |
|------------|-------------------------------------------|
| \`\`       | Position avant le dernier saut de curseur |
| `.         | Position du dernier changement            |
| `^         | Position de la dernière insertion         |
| `[         | Début du dernier changement               |
| `]         | Fin du dernier changement                 |
| `<         | Début de la dernière selection            |
| `>         | Fin de la dernière selection              |

Voir le plugin matchit qui permet d'utiliser le symbole `%`,
pour faire correspondre le début et la fin d'un nœud xml.

## Navigate in file
`<C-o> <C-i>` Précédente, suivante position du curseur

`:jumps` Liste des positions du curseur

`( )` Phrase suivante, précédente

`{ }` Paragraphe suivant, précédent

`H` `M` `L` Respectivement met le curseur sur l'écran (sans scroller),
en haut,
au milieu,
en bas

`gf` "Go to file", atteint/ouvre le fichier dont l'adresse est sous le curseur.
Mais bien régler son path

On peut préciser à _vim_ une liste de suffixes,
que _vim_ ajoutera au fichier qu'il cherche sans le trouver avec la commande `gf`

`<C-i>` En mode insertion, indente comme tab

`:changes` Liste des changements

`g;` `g,` Positionne le curseur sur le changement précédent, suivant

`vim -u NONE -N` Lancer _vim_ sans plugin et sans configuration

## Register
`"ay` Copier dans le presse papier "a"

`"ap` Colle le presse papier "a"

`"Np` N étant la position dans l'historique des couper

`:reg` Historique

`:reg 1` Atteint l'historique à une certaine position

`_dd` Grâce au caractère `_`, suppression de la ligne sans mettre celle-ci dans le register


## Macros
`:reg {a-z}` Voir la description de la macro {a-z}

`@@` Exécute la dernière macro exécutée (en fait la dernière commande)

`q{A-Z}` Ajoutera à la fin de la macro assignée à la lettre en minuscule,  
l'enregistrement en cours

### Exemple de macro avec incrementation
* `:let i=1<CR>` Définir une variable à 1, avant le début de la macro
* `qa` Commencer une macro enregistrée à la lettre "a"
* `I<C-r>=i<CR>` Insertion avant le premier caractère de la ligne, de la variable évaluée
* `<Esc>` Sortir du mode d'insertion
* `:let i +=1<CR>` Incrémenter la variable
* `jse` positionner au prochain endroit où l'on voudra continuer cette insertion
* `q` Arrêter l'enregistrement de la macro

Il ne reste plus qu'à exécuter la macro autant de fois que nécessaire en faisant :  
`@a`

## Search
`/\c{pattern}` Force la casse insensible

`/\C{pattern}` Force la casse sensible

### Regex
Les accolades : échapper les ouvrantes  
Les crochets : ne pas à échapper (sauf littéral)  
Les parenthèses : tout échapper

`\v` "Very magic", regex plus traditionnelle,  
Voir `:h /character-classes`

`\V` "Verbatim", pour faire facilement du littéral

`<motif>` Délimite le mot plus facilement

`/mo\zsti\zef` Délimite la recherche, ici seul "ti" de "motif" sera en surbrillance

`escape({string}, {chars})` Échappe le caractère {chars} dans {string}

`//` Faire une recherche vide revient à chercher le dernier pattern.  
Fonctionne pour / ? substitute etc

`:noh` Enlève la surbrillance de la recherche une fois

`/l[^a]` Trouve "le", "li" … tous sauf "la"

Les parenthèses d'une recherche capture le résultat dans groupe,  
appelable par `\1` etc

`<C-r> "` Colle en insertion

## Substitution
Structure d'une commande de substitution : `[range]s[ubstitution]/{pattern}/{string}/[flags]`

| Caractères spéciaux | Définition                                               |
|---------------------|----------------------------------------------------------|
| \r                  | Insère un retour à la ligne                              |
| \t                  | Insère une tabulation                                    |
| \\                  | Insère un backslash                                      |
| \1                  | Insère le premier groupe capturé                         |
| \2                  | Insère le deuxième groupe capturé (jusqu'à 9)            |
| \0                  | Insère la capture entière                                |
| &                   | Insère la capture entière                                |
| ~                   | ??? Utilise la chaine capturée précédemment ? À vérifier |
| \={Vim script}      | Évalue le script et utilise le résultat pour le remplacer|

## Flags
`g` Global, toutes les occurrences

`n` Compte et ne substitue pas

`c` Demande confirmation, voir le tableau ci-dessous pour voir les options

|Flags | Définition                           |
|------|--------------------------------------|
|y     | oui                                  |
|n     | non                                  |
|q     | quitte la substitution               |
|l     | "last" remplace ce dernier et quitte |
|a     | "all" remplace tout sans confirmation|

On peut pendant cette phase interactive faire :
`<C-e>` ou `<C-y>` pour faire défiler la page

Dans certains cas il peut être plus simple et plus claire,  
de faire une recherche d'abord et d'examiner,  
et enfin de faire une substitution (en faisant une recherche vide pour utiliser la précédente recherche).

` <C-r> /` Colle la dernière recherche en mode insertion

`:%s//\=@0/g` en décomposé :

- `//` vide donc correspond à la dernière recherche
- `\=` évalue le script
- `@0` presse papier par référence
- `g` global

Si dans le presse papier on a copié (yank) un contenu multi-lignes,
_vim_ évaluera ce presse papier et remplacera par le contenu multi-lignes

`g&` Répète la dernière substitution, sur toutes les lignes

`&&` Répète la dernière substitution, avec les mêmes "flags"

> Voir la commande submatch qui permet de substituer à l'intérieur d'une substitution

`:let dico = {"a" : 1, "b" : 2}` Déclarer un tableau associatif (peut être pratique pour échanger 2 mots par exemple)

> Voir le plugin abolish

`|` sert à chainer plusieurs commande.

## Global command
`:[range]global[!]/{pattern}/{cmd}`

`!` pour inverser la recherche, `vglobal` peut servir dans ce sens aussi ?

`{cmd}` par défaut print

`:d` ou `:delete` est une commande global ?

## Ctags
`<C-]>` Saute à la définition du tag sous le curseur

`<C-t> t ou` `:pop` Reviens en arrière après avoir vu la définition du tag

`g<C-]>` Dans le cas de plusieurs résultats, présente une liste

`:tnext` `:tprev` `:tfirst` `:tlast` Respectivement : prochain, précédent, premier, dernier tag de la liste de résultats

`:tselect` Liste les tags trouvés

`:tjump` Liste les tags trouvés, mais si il n'y en a qu'un saute vers celui-ci

## Search project wide
`:grep` Met le résultat dans le _quick fix buffer_.  
Ouvrable avec la commande `:copen`.

Les résultats sont interactif et peuvent être parcouru par les commandes `:cnext` etc

Cette commande est configurable,  
on peut préciser à _vim_ quelle commande shell lancer (comme ack ou autre)

`:vimgrep[!]/{pattern}/[g][j]/file`  
`[j]` ne saute pas automatiquement sur le premier résultat  
`*` dans tout le dossier  
`**` récursif  
`%` dans le fichier en cours  
`##` dans tout les fichiers de la liste d'arguments

`:vim[grep]/<C-r>//*`

`<C-r>/` Pendant au milieu de la commande, reprendra la précédente recherche 

## Autocompletion
`<C-p>` et `<C-n>` suggestion précédente et suivante

Sommaire des commandes d'auto-complétion

| Commande      | Définition                      |
|---------------|---------------------------------|
| `<C-n>`       | Mots clés générique             |
| `<C-x><C-n>`  | Mots clés du buffer             |
| `<C-x><C-i>`  | Mots clés des fichiers inclus   |
| `<C-x><C-]>`  | Mots clés des tags              |
| `<C-x><C-k>`  | Recherche dans le dictionnaire  |
| `<C-x>s`      | Recherche dans les langues      |
| `<C-x><C-l>`  | Complétion de la phrase entière |
| `<C-x><C-f>`  | Nom de fichier                  |
| `<C-x><C-o>`  | Omni-complétion                 |

Commandes de la fenêtre de complétion

| Commande                  | Effet                                             |
|---------------------------|---------------------------------------------------|
| `<C-n>` ou flèche du bas  | Suggestion suivante                               |
| `<C-p>` ou flèche du haut | Suggestion précédente                             |
| `<C-y>`                   | Accepte la suggestion suivante                    |
| `<C-e>`                   | Sort du menu et reviens au mot tapé originalement |

## Spell check
`z=` Suggestion de correction

`1z=` Accepter la 1ère suggestion

`zg` Ajouter au dictionnaire le mot sous le curseur

`zw` Enlève du dictionnaire

`zug` Annule l'action d'ajout ou de suppression au dictionnaire

## Fugitive
:Gstatus

### Dans Gstatus
`r` Rafraichit Gstatus

`-` Ajoute ou retire de l'index le fichier sous le curseur

`o` Ouvrir le fichier sous le curseur, dans un split

`O` Ouvrir le fichier sous le curseur, dans un nouvel onglet

`p` Fait un add -p sur le fichier sous le curseur

Pointer vers le fichier désiré (par exemple avec `ctl+n` ou `ctrl+p`) et faire `shift+D`  
Voir le _diff [--staged]_ pour le fichier 

### Commit
`cc` Commit

`ca` Commit --amend

### Glog
`:Glog --` Place le log dans le buffer quickfix, mais il reste une validation avant de voir celui-ci.

`:Glog -- %` Même chose que précédemment mais concernant le fichier courant.

### Gdiff
`:on` pour revenir d'un `:Gdiff`  

### Gedit
En cas de manipulation hasardeuse,  
si on veut récupérer le fichier se trouvant dans le working directory,  
plutot qu'une version dans l'index de git, faire:
:Gedit

:Gedit HEAD:% Voir le fichier courant à une certaine révision  
Pratique dans un buffer vertical 

## Vim gitgutter
`<leader>hp` Prévisualisation du bloc

`<leader>hs` Ajoute le bloc dans l'index

`<leader>hr` Restaure le bloc

## Autre
`:!python -m json.tool` Ré-indente le json sélectionné
