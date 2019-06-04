# Shell

## Summary
- [History](#History)
- [Arguments](#Arguments)
- [Substitute](#Substitute)
- [Console](#Console)
- [ack](#ack)
- [awk](#awk)
- [sed](#sed)
- [tree](#tree)
- [Autre](#Autre)

## History

Historique des commandes `history`  
Vide l'historique `history -c`  
Lance la dernière commande, en faisant en interne un replace string `!!`  
Lance la commande _n_ `!n`

## Arguments
Tous les arguments `!*`  
Argument _n_ de la commande `!:n`  
Recherche la commande contenant la chaine de caractères _string_ et l'exécute `!?string`  
Relance la dernière commande _cmd_ `!cmd`  
Dernier argument de la 5ème commande `!5$`  
Premier argument de la 5ème commande `!5^`  
Affiche tout les arguments de la dernière commande `echo !cat:*`  
Prend le dernier morceau d'un _path_, _filename_ `!!:t`  
Prend tout sauf la dernière partie d'un _path_, _dirname_ `!!:h`  
Mets entre apostrophes les arguments `!!:q`  
Divise sur les espaces et les sauts de lignes et ajoute des apostrophes `!!:x`  
Affiche la commande `!!:p`

## Substitute
Remplace le premier terme trouvé `!!:s/search/replace`  
Remplace tout les termes trouvés `!!:gs/search/replace`

## Console
Ramène le curseur au début de la commande `Ctrl + a`  
Ramène le curseur à la fin de la commande `Ctrl + e`  
Supprime tout ce qui se trouve à gauche du curseur `Ctrl + u`  
Supprime tout ce qui se trouve à droite du curseur `Ctrl + k`  
Supprime le premier mot situé à gauche du curseur `Ctrl + w`  
Restaure ce qui a été supprimé avec les commandes au-dessus `Ctrl + y`  
Déplacement un mot en arrière `Alt + b`  
Déplacement un mot en avant `Alt + f`  
Suppression du mot à partir du curseur `Alt + d`  
Capitalise le mot et se rend à la fin de celui-ci `Alt + c`  
Haut de casse du mot `Alt + u`  
Bas de casse du mot `Alt + l`  
Déplacement d'une lettre en avant `Ctrl + f`  
Déplacement d'une lettre en arrière `Ctrl + b`  
Supprime le caractère sous le curseur `Ctrl + d`  
Supprime le caractère derrière le curseur `Ctrl + h`  
Échange la lettre sous le curseur avec le précédent `Ctrl + t`

## ack
Recherche dans les fichiers _php_ `ack --php pattern`  
Recherche le mot _pattern_ `ack -w pattern`  
Recherche avec expression rationnelle,  
affiche le groupe capturé et sans le nom de fichier `ack 'pattern(.*)' --output '$1' -h` 

## ag
…

## awk
Affiche la deuxième colonne du flux entrant `ls -l | awk '{print $2}'` 

## sed
### Substitute
Remplace les espaces par `_` et affiche le résultat `sed "s/ /_/g fichier.md"`  
Remplace les espaces par `_` dans le fichier `sed -i "s/ /_/g fichier.md"`

Exemple avec pour voir le `$PATH` en multi-lignes
`echo $PATH | sed "s/:/\n/g"`

## tree
Ignore le dossier vendor `tree -I vendor`

## Autre
Execute le script que l'on télécharge `curl http://example.com/scripts/do.sh | bash`  
Parser du json en ligne de commande avec python `echo '{"foo": "b"}' | python - m json.tool`  
Attribuer des droits de manière sympathique `chmod g+w,o-w rapport.txt chmod u=rwx,g=r,o=- rapport.txt`
