# Shell

## History

`history` Historique des commandes  
`history -c` Vide l'historique  
`!!` Lance la dernière commande, en faisant en interne un replace string  
`!n` Lance la commande "n"

## Arguments
`!*` Tous les arguments  
`!:n` Argument n de la commande  
`!?string` Recherche la commande contenant la chaine de caractères _string_ et l'exécute  
`!cmd` Relance la dernière commande _cmd_  
`!5$` Dernier argument de la 5ème commande `!5^` Premier argument de la 5ème commande  
`echo !cat:*` Affiche tout les arguments de la dernière commande  
`!!:t` Prend le dernier morceau d'un _path_, _filename_  
`!!:h` Prend tout sauf la dernière partie d'un _path_, _dirname_  
`!!:q` Mets entre apostrophes les arguments  
`!!:x` Divise sur les espaces et les sauts de lignes et ajoute des apostrophes  
`!!:p` Affiche la commande

## Substitute
`!!:s/search/replace` Remplace le premier terme trouvé  
`!!:gs/search/replace` Remplace tout les termes trouvés

## Console
`Ctrl + a` Ramène le curseur au début de la commande  
`Ctrl + e` Ramène le curseur à la fin de la commande  
`Ctrl + u` Supprime tout ce qui se trouve à gauche du curseur  
`Ctrl + k` Supprime tout ce qui se trouve à droite du curseur  
`Ctrl + w` Supprime le premier mot situé à gauche du curseur  
`Ctrl + y` Restaure ce qui a été supprimé avec les commandes au-dessus  
`Alt + b` Déplacement un mot en arrière  
`Alt + f` Déplacement un mot en avant  
`Alt + d` Suppression du mot à partir du curseur  
`Alt + c` Capitalise le mot et se rend à la fin de celui-ci  
`Alt + u` Haut de casse du mot  
`Alt + l` Bas de casse du mot  
`Ctrl + f` Déplacement d'une lettre en avant  
`Ctrl + b` Déplacement d'une lettre en arrière  
`Ctrl + d` Supprime le caractère sous le curseur  
`Ctrl + h` Supprime le caractère derrière le curseur  
`Ctrl + t` Échange la lettre sous le curseur avec le précédent

## ack
`ack --php pattern` Recherche dans les fichiers _php_  
`ack -w pattern` Recherche le mot _pattern_  
`ack 'pattern(.*)' --output '$1' -h` Recherche avec expression rationnelle,  
affiche le groupe capturé et sans le nom de fichier.

## ag
…

## awk
`ls -l | awk '{print $2}'` Affiche la deuxième colonne du flux entrant

## sed
### Substitute
`sed "s/ /_/g fichier.md"` Remplace les espaces par `_` et affiche le résultat  
`sed -i "s/ /_/g fichier.md"` Remplace les espaces par `_` dans le fichier

## tree
`tree -I vendor` Ignore le dossier vendor

## Autre
`curl http://example.com/scripts/do.sh | bash` Execute le script que l'on télécharge.  
`echo '{"foo": "b"}' | python - m json.tool` Parser du json en ligne de commande avec python  
`chmod g+w,o-w rapport.txt chmod u=rwx,g=r,o=- rapport.txt` Attribuer des droits de manière sympathique
