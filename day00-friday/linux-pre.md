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

On dispose d’un ensemble d’images au format `png`, réunies dans le dossier BioCell, qui a été archivé et compressé sous le nom `biocell.tgz`. Les images représentent quatre types de cellules : bactéries (`Bact`), levures (`Lev`), cellules animales (`Ani`) et végétales (`Veg`) ; pour chaque type, on dispose d’une image en microscopie optique (`MOp`), une en microscopie électronique à balayage (`MEB`), une en microscopie électronique en transmission (`MET`), et un schéma (`Sch`). Le nom d’un fichier correspond à ce que représente l’image, par exemple `METLev.png` est une image de levure vue au microscope électronique à transmission, `SchVeg.png` montre un schéma de cellule végétale, _etc._

1. Commençons par créer un répertoire pour faire l'exercice. Les images sont sauvées dans un fichier [biocell.tgz](biocell.tgz) qui est dans ce répertoire. Commencez par Nous allons télécharger le ficher d'images et le décompresser à l'aide de la commande `tar`. 

```bash 
# Revenir à notre home
cd

# créer un dossier pour faire l'exercice.
mkdir exo-rangement
cd exo-rangement

# wget est une commande qui permet de télécharger directement un fichier d'internet 
wget https://github.com/rki-mf1/2023-Workshop-Madagascar-IGS/raw/main/day00-friday/biocell.tgz

tar -xvzf biocell.tgz
# vérifions ce qui a été créé
ls 
```

2. Afficher la liste des fichiers présents dans le répertoire. (note, vous pouvez aussi regarder les images avec l'explorateur de fichiers)
3. Trouver quel est le fichier le plus récent et le plus ancien.
4. Créer, dans le répertoire courant, un sous-répertoire nommé `Schemas`.
5. Copier en une seule commande les quatre images correspondant à des schémas dans le répertoire `Schemas` ; vérifier que l’on a bien copié les fichiers voulus et seulement eux.
6. Créer dans le répertoire courant le sous-répertoire `Bacteria` ; copier en une seule commande les quatre fichiers montrant des bactéries dans le répertoire `Bacteria` ; vérifier que l’on a bien copié les fichiers voulus et seulement eux.
7. Créer dans le répertoire courant le sous-répertoire `Electro`, puis sans changer de répertoire courant, créer à l’intérieur d’`Electro`, le répertoire `Lev3` ; copier en une seule commande les deux images de levure prises en microscopie électronique dans `Lev` ; vérifier que l’on a bien copié les fichiers voulus et seulement eux.
8. Se déplacer dans `Electro` ; y créer un répertoire nommé `VL` ; copier en une seule commande dans `VL` toutes les images de microscopie électronique de cellules végétales et de levures ; vérifier que l’on a bien copié les fichiers voulus et seulement eux.
9. Tout en restant dans `Electro`, copier en une seule commande le répertoire Lev et tout ce qu’il contient dans `BioCell`, sous le nom `LevElectro` ; vérifier que l’on a bien copié ce qu’on voulait où l’on voulait.
10. Tout en restant dans `Electro`, supprimer en une seule commande le répertoire `Lev` et tout ce qu’il contient ; vérifier.
11. Copier en une seule commande dans `Electro` toutes les images de microscopie électronique présentes dans `BioCell` ; vérifier.
12. Revenir dans `BioCell` ; y créer le répertoire `Animal` ; y déplacer en une seule commande toutes les images de cellules animales ; vérifier.
13. Renommer le répertoire `LevElectro` en `ElectroLev` ; vérifier.
14. Créer au moyen d’une commande utilisant un chemin absolu, le répertoire `Optique` dans BioCell ; y déplacer en une seule commande toutes les images de microscopie optique qui restent dans BioCell (mais pas celles qu’on a placées dans ses sous-répertoires !) ; vérifier.
15. Déplacer l’image `SchBact.png` dans le répertoire `Bacteria`, en étant prévenu si la copie doit écraser un fichier déjà présent (c’est le cas ; valider l’écrasement pour effectuer la copie) ; vérifier.
16. Déplacer en une seule commande tous les autres schémas dans le répertoire `Schemas`, en évitant d’avoir à valider l’écrasement ; vérifier.
17. Supprimer en une seule commande toutes les images qui restent dans le répertoire `BioCell` (ne pas chercher à supprimer les images des sous-répertoires de `BioCell`) ; vérifier.
18. Retourner dans le répertoire `exo-rangement` en une commande utilisant un chemin absolu ; vérifier.
19. Compresser le répertoire `BioCell` en une archive au format tgz nommée `biocell2.tgz` en vérifiant lors de l’archivage le contenu de l’archive. (Vous devrez demander de l'aide pour cette commande ou regarder comment utiliser la commande `tar` sur internet).
20. Effacer le répertoire `BioCell` et tout ce qu’il contient ; vérifier.


## 3 - Séquences non codantes

Le fichier [maripaludis_nc.tab](maripaludis_nc.tab) contient des données sur les ARN « non codants » (c’est-à-dire ne pas pour des protéines) de _Methanococcus maripaludis_. Chaque ligne du fichier contient, pour un codant ARN :

* le code de la séquence génomique d’où est extrait l’ARN (N.B. une même séquence génomique peut contenir plusieurs ARN non codants) ;

* la souche de `Methanococcus maripaludis` ;
* la position de début de l’ARN dans la séquence génomique ;
* la position de fin de l’ARN dans la séquence génomique ;
* la longueur de l’ARN (évidemment, longueur = fin – début + 1) ;
* la nature de l’ARN ;
* le pourcentage de G+C de la séquence de l’ARN (arrondi à l’unité la plus proche).

Les colonnes sont séparées par des caractères de tabulation.

**Note** : Ce fichier est donné pour s'entraîner avec les commandes linux, il n'est pas  lié aux analyses que nous feront dans les jours qui suivent.


**Préparation: tri de fichier avec la commande `sort`**:
```bash
# Trier le fichier par la première colonne en ordre lexicographique (le dictionnaire)
sort maripaludis_nc.tab

# Trier le fichier par la seconde colonne
sort -k2,2 maripaludis_nc.tab

# Trier le fichier par la longueur, est ce que ça marche ?
sort -k5,5 maripaludis_nc.tab

# Il faut trier en spécifiant des valeurs numériques avec l'option 'n'
sort -k5,5n maripaludis_nc.tab

# Trions par le pourcentage en GC
sort -k7,7n maripaludis_nc.tab

# Ca ne marche pas à cause des espaces dans la 6è colonne,
# on doit donner la tabulation comme séparateur
sort -t$'\t' -k7,7n maripaludis_nc.tab

# la commande cut permet d'extraire un ou plusieurs colonnes
cut -f 3 maripaludis_nc.tab

# pour extraire deux colonnes 
cut -f 3,5 maripaludis_nc.tab 

# On peut combiner 'cut' avec 'sort' et 'uniq' pour avoir les
# souches apparaissant
cut -f 2  maripaludis_nc.tab | sort | uniq

# le plus bas pourcentage en GC
cut -f 7 maripaludis_nc.tab | sort | head -n 2

# les deux plus haut pourcentages en GC
cut -f 7 maripaludis_nc.tab | sort | tail -n 2 

```


Donnez les commandes permettant de répondre aux questions suivantes (une seule ligne de commande suffit pour chaque question) :
1. *Préparation*: En premier lieu, sauvez le fichier dans un répertoire `exo-ncARN` que vous utiliserez comme répertoire pour faire vos analyses.
2. Commencez par visualiser les premières lignes du fichier, pour vous familiariser avec sa structure.
2. Combien d’ARN non codants comporte le fichier ? N’oubliez pas de soustraire 1 pour la ligne d’en-tête.
4. Sélectionnez les ARN non codants de la souche `DSM` à l'aide de grep. Combien y-a-t-il de lignes ? 
5. Stockez les ARN non codants dans un fichier `DSM_nc.tab`
6. Extrayez le nombre d'ANR non codants pour les souches `C5` et `C7` et stockez les dans un fichier `C5C7_nc.tab`.
7. Triez le fichier par le pourcentage en GC et stocker dans `maripaludis_nc_GCtrie.tab`
8. Quelle est le plus petit pourcentage de G+C parmi les ARN du fichier ?
9. Quelle est la longueur du plus petit ARN du fichier ?
10. Quelle est la longueur du plus grand ARN du fichier ?
11. Combien de souches différentes de M. maripaludis sont représentées dans le fichier ?
12. Combien de séquences d'ARN sont représentées pour chaque souche ?

