# 2023 Workshop IGS Genome reconstruction - Day 0



## 1 - Commandes sur les répertoires et les fichiers

Nous allons revoir les commandes linux de manipulation de fichier de base en créant quelques fichiers et en les copiant/déplaçant. 

```bash

# Imprimer le répertoire courant
pwd

# afficher le contenu du répertoire courant
ls

# afficher avec plus d'informations et des détails lisibles
ls -lh

# créer un répertoire pour travailler
mkdir igs-test

# se déplacer dans le répertoire
cd igs-test

# Exercice: construire deux sous répertoire `poemes` et `proverbes`

# Exercice: sauver une poésie dans le fichier `poemes/monpoeme.txt` et un proverbe dans le répertoire `proverbe/monproverbe.txt` (par exemple à partir de [ce site](https://www.proverbes-francais.fr/) pour les proverbes et [celui ci](https://www.mon-poeme.fr) pour les poemes)
# Tip: utilisez nano ou un éditeur de fichier

# Afficher le poeme 
cat poemes/monpoeme.txt

# copier le poeme dans le répertoire courant (igs-test) 
cp poemes/monpoeme.txt ./

# afficher le répertoire
ls 

# aller dans poemes 
cd poemes

# aller dans proverbes avec un *chemin relatif*
cd ../proverbes

# retourner dans poemes avec un *chemin absolu* (utilisateur igsw)
cd /home/igsw/igs-test/poemes

# Maintenant on copie le poeme deux fois
cp poeme.txt poesie.txt
cp poeme.txt popoeme.txt

# Utilisation du joker, `wildcard``
# Comparez ce qui est affiché
ls poe*

ls po*me.txt

# La commande head affiche les premières lignes d'un fichier
head poeme.txt

# la commande tail affiche les dernières lignes
tail poeme.txt 

```

## 2 - Exercice, rangement de fichiers



```bash 



```