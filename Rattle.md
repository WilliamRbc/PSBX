title: Guide Rattle

author: Nicolas Allix & William Robache

# Rattle

Pour commencer : [vidéo d'introduction](https://www.loom.com/share/be0f87ca04374674b03f440e28132715 "Introduction du guide")

## Introduction
**Rattle** est une GUI (graphical user interface) qui dépend du package **RGtk2**.

**Rattle** est utilisé en R pour des analyses complexe et pour du data mining. Rattle présente des résumés statistiques et visuels des données, il transforme les données qui peuvent être facilement modélisées. **Rattle** permet de construire à la fois des modèles non supervisés et supervisés.

**Rattle** présente les performances des modèles sous forme graphique.

L'une des caractéristiques qui font l'intéret de **Rattle** est que les interactions de l'utilisateur sur le GUI sont enregistré en script R. Le script peut ensuite être utilisé et exécuté facilement en R indépendamment de l'interface **Rattle**.

**Rattle** utilise une grande quantité de package afin de proposer le plus de posbilité dans la création d'algorithme de Data Mining.

## Installation

Pour installer Rattle, il suffit de rentrer 3 commandes dans votre console sous Rstudio:

>install.packages('rattle', dependencies = T)

Cette commande prend plusieurs minutes à s'effectuer, en fonction de votre ordinateur.

Ensuite:

>library('rattle')

Et enfin : 

>rattle()

Cette dernière commande vous ouvre une petite fenêtre "need GTK+ ?", vous faites "OK", et la fenêtre principale de Rattle s'ouvre.



À savoir :

Pour relancer rattle sur un nouveau fichier, il suffit simplement d'éxecuter les deux dernières commandes :

>library('rattle')

>rattle()

Voir la [vidéo d'installation](https://www.loom.com/share/0957161f45ad49cfa3a540baee699672 "Loom installation Rattle")
<!--Pour utiliser **Rattle**, il faut télécharger et installer le package. 

Pour cela, il faut commencer par installer le package **RGtk2** ci-dessous.
[Package RGtk2](https://cran.r-project.org/bin/windows/contrib/3.3/RGtk2_2.20.31.zip "Package RGtk2")

Installer RGtk2 dans RStudio depuisi un dossier local avec les arguments comme indiqué ci-dessous : 
>install.packages("FILEPATH", repos = NULL, type = "win.binary")

Ensuite, il faut installer **Rattle**, en incluant le lien de dépendence:
>install.packages("rattle", dep=TRUE)

Enfin, il faut fermer et ré-ouvrir R Studio. Nous pouvons appeller **Rattle**:
>library(rattle)
[Rattle launch message]
>rattle()
___
En cas d'erreur, il suffit généralement de re-fermer R Studio et de le ré-ouvrir.
___ -->
## Commande

Rattle génére lui même du code R en fonction de ce qu'il exécute. Vous trouverez ci-dessous les différentes fonctionnalité pris en charge par Rattle.

### **calcInitialDigitDistr**

Dans le cadre de la loi de Benford, calculer la distribution des fréquences du premier chiffre des nombres fournis comme argument.
>**Remarque** : la loi de Benford, fait référence à une fréquence de distribution statistique observée empiriquement sur de nombreuses sources de données dans la vraie vie, ainsi qu'en mathématiques.

Il s'écrit :
>calcInitialDigitDistr(l, digit=1, len=1, sp=c("none", "positive", "negative"))

#### *Argument :*
l : un vecteur de nombres.

digit : le chiffre pour lequel on génère des fréquences.

len : Le nombre de chiffres.

sp : Comment diviser les chiffres.

### **listAdaVarsUsed**

Retourne une liste des variables utilisées et de leurs fréquences.

Il s'écrit :
>listAdaVarsUsed(model)

#### *Argument :*
model : un rpart Object

### **fancyRpartPlot**

Trace un arbre de décision RPart à l'aide du joli traceur rpart avec Prp.

Il s'écrit :
>fancyRpartPlot(model, main="", sub, caption, palettes, type=2, ...)

#### *Argument :*
model : un rpart object

main : Titre du graph

sub : Sous-titre du graph. A défault, le souos-titre est la date, l'heure et le nom de l'utilisateur

caption : Légende en bas à droite du graph

palettes : une liste de noms de palettes de couleur. Comme supporté par RColorBrewer::brewer.pal, les noms disponibles sont Blues BuGn BuPu GnBu Greens Oranges OrRd PuBu PuBuGn PuRd Purples RdPu Reds YlGn YlGnBu YlOrBr YlOrRd

type : le type de graphe créé (ici 2)

... : les arguments supplémentaires transmis à prp

### **ggVarImp**

Model

Il s'écrit :
>ggVarImp(model, ...)

#### *Argument :*
model : un objet

... : Les arguments transmis

### **drawTreesAda**

réalise des graphiques arbres à partir d'un modèle Ada 

Il s'écrit :
>drawTreesAda(model, trees=0, title="")

#### *Argument :*
model : un model Ada

trees : La liste des branches à dessiner. Mettre 0 pour dessiner toutes les branches

title : optionnel pour ajouter un titre

### **rescale.by.group**

Transformer un vecteur numérique en le regroupant selon les valeurs du facteur fourni, puis en le redimensionnant à l'intérieur des groupes

Il s'écrit :
>rescale.by.group(x, by=NULL, type = "irank", itop = 100)

#### *Argument :*

x : Le vecteur numérique à redimmensionner

by : Un facteur de même longueur que x utilisé pour définir les groupes

type : le type de redimmension à faire

itop : Pour un remappaging d'entier, il s'agit du nombre de groupes, de sorte que les valeurs numériques sont mises en correspondance avec les entiers de 0 à (max-1)

### **drawTreeNodes**

Dessine les nœuds d'un arbre de décision

>**Remarque** : DrawTreeNodes est une variation de draw.tree() du package maptree

Il s'écrit :
>drawTreeNodes(tree, cex = par("cex"), pch = par("pch"),
                           size = 4 * cex, col = NULL, nodeinfo = FALSE,
                           units = "", cases = "obs", 
                           digits = getOption("digits"),
                           decimals = 2,
                           print.levels = TRUE, new = TRUE)

#### *Argument :*

tree : un rpart decision tree

decimals : Nombre de chiffres décimaux à inclure dans les nœuds

>#### *exemple :*
>drawTreeNodes(rpart(Species ~ ., iris))

### **listVersions**

Génere une liste des packages utilisé. Il est utilisé pour trouver un potentiel bug ou erreur.

Il s'écrit :
>listVersions(file="", ...)

#### *Argument :*

... : write.csv

### **errorMatrix**
Génere une matrice d'erreur avec les données actuelles et les données prédictes.
Une matrice d'erreur repporte les taux de true/false et les taux positive/negative.

Il s'écrit :
>errorMatrix(actual,
                        predicted,
                        percentage=TRUE,
                        digits=ifelse(percentage,1,3),
                        count=FALSE)

#### *Argument :*

actual : le vecteur avec les valeurs "true"

predicted : le vecteur avec les valeurs prédites

percentage : pour retourner en pourcentage ou en absolue

digits : le nombre de décimal

count : pour présenter le résutat

### **rattle.print.summary.multinom**
Retourne les infomration d'un model multinomial

Il s'écrit :
>rattle.print.summary.multinom(x, digits = x$digits, ...)

#### *Argument :*

x : un rpart object

digits : le nombre de chiffre à retourner

... : Arguments supplémenetaire

### **evaluateRisk**
Résume les performance d'un modèle de data mining. En prenant les valeurs prédites, les valeurs réelles et les mesures du risque associé à chaque cas, cette fonction génére un résumé qui regroupe les valeurs prédites distinctes, en calculant le pourcentage cumulé de cas, de rappel, de risque, de précision et de mesure.

Il s'écrit :
>evaluateRisk(predicted, actual, risks)

#### *Argument :*

predicted : Un tableau numérique de probabilité (entre 0 et 1) qui représente la probabilité de chaque entité (1)

actual : un tableau numérique des classes (0 ou 1)

risks : un vecteur numérique du risque (par exemple, les montants en dollars) associé à chaque entité qui a un acutal de 1.

### **plotOptimalLine**
Trace une ligne verticale à x en haut de y1 et y2, puis une ligne horizontale à partir de cette ligne à y1 et y2. Destiné à être tracé sur un plotRisk.

Il s'écrit :
>plotOptimalLine(x, y1, y2, pr = NULL, colour = "plum", label = NULL)

#### *Argument :*

x : ligne vertical

y1 : ligne horizontal 1

y2 : ligne horizontal 2

pr : Retourne le pourcentage d'un point

colour : couleur de la ligne

label : légende en dessous de la ligne

### **modalvalue**
Calcule le mode d'un vecteur, d'un tableau ou d'une liste.
Le mode est la valeur la plus courante ou la plus modale d'une liste.

Il s'écrit :
>modalvalue(x, na.rm=FALSE)

#### *Argument :*

x : un vecteur, un tableau ou une liste

na.rm : pour supprimer les valeurs manquantes

### **setupDataset**
Cette fonction de Rattle est utilisée pour encapsuler les objets de data mining. L'environnement fourni est complété par d'autres données dérivées des données fournies, telles qu'un échantillon de données d'entraînement, une liste de variables numériques et une formule de modélisation.

Il s'écrit :
>setupDataset(env, seed=NULL)

#### *Argument :*

env : l'environnement à modifier

seed : optionnel pour régler des données dites "seed"

### **savePlotToFile**
Pour l'appareil actuel, ou pour l'appareil identifié, enregistrez d'une manière ou d'une autre le plot affiché. Celui-ci est soit enregistré dans un fichier, soit copié dans le presse-papiers pour être collé dans d'autres applications, soit envoyé à l'imprimante

Il s'écrit :
>savePlotToFile(file.name, dev.num=dev.cur())
copyPlotToClipboard(dev.num=dev.cur())
printPlot(dev.num=dev.cur())

#### *Argument :*

file.name : Chaîne de caractères désignant le fichier, y compris l'extension du nom de fichier qui est utilisée pour spécifier le type de fichier à enregistrer

dev.num : Un numéro d'appareil indiquant l'appareil vers lequel sauvegarder

### **rattleInfo**
Affiche les informations sur le système, y compris les versions de Rattle et R, le système d'exploitation et les versions d'autres packages utilisés par Rattle. Utile pour signaler des bugs mais aussi pour renvoyer de manière invisible une liste de packages qui ont des mises à jour disponibles et qui peuvent être passées à install.packages().

Il s'écrit :
>rattleInfo(all.dependencies=FALSE,
           include.not.installed=FALSE,
           include.not.available=FALSE,
           include.libpath=FALSE)

#### *Argument :*

all.dependencies : si TRUE, alors vérifiez le graphique des dépendances de Rattle et listez tous les packages (ce qui peut prendre quelques secondes à calculer), ou bien listez simplement les packages clés dont Rattle dépend et qu'il suggère.

include.not.installed : si TRUE, mentionnez alors les packages qui ne sont pas installés, mais qui sont disponibles.

include.not.available : si TRUE, mentionnez alors tout package qui n'est pas disponible auprès du CRAN.

include.libpath : si TRUE, indiquez l'emplacement de la bibliothèque où chaque paquet est installé.

### **randomForest2Rules**
Un modèle RandomForest, par défaut, se compose de 500 arbres de décision. Cette fonction parcourt chaque arbre et génère un ensemble de règles. Cette fonction prend un temps considérable et est fournie aux utilisateurs pour accéder au modèle réel, mais elle n'est pas encore utilisée dans l'interface graphique de Rattle. Il peut être utilisé uniquement pour l'exportation vers PMML ou SQL.

Il s'écrit :
>randomForest2Rules(model, models=NULL)

#### *Argument :*

model : un modèle randomForest

models : une liste d'entiers limitant les modèles dans MODEL qui sont convertis

### **asRules.rpart**
 
énumère les règles qui correspondent à l’arbre de décision rpart
 
Il s'écrit :
>asRules(model, compact=FALSE, classes=NULL, …)
 
#### *Argument :*
model : un modèle rpart
 
Compact : s'il faut lister les catégories de manière compacte (FALSE par défaut).
 
Classes : quelles classes cibles doivent être répertoriées (toutes par défaut).
 
… autres arguments passés vers ou depuis d'autres méthodes.
 
### **asRules**
 
énumère les règles qui correspondent à l’arbre de décision rpart
 
Il s'écrit :
>asRules(model, compact=FALSE, …)
 
#### *Argument :*
model : un modèle rpart
 
Compact : s'il faut lister les catégories de manière compacte (FALSE par défaut).
 
… autres arguments passés vers ou depuis d'autres méthodes.
 
### **acquireAuditData**
 
Générez le jeu de données d'audit.
 
Il s'écrit :
>acquireAuditData(write.to.file=FALSE)
 
#### *Argument :*
write.to.file : Indique s'il faut générer une collection de fichiers basée sur les données. Les fichiers générés incluent: audit.csv, audit.Rdata, audit.arf et audit \ _missing.csv
 
 
### **calculerAUC**
 
Déterminer l'aire sous une courbe (par exemple, une courbe de risque ou de rappel) d'un graphique de risque
 
Il s'écrit :
>calculateAUC(x, y)
 
#### *Argument :*
 
X : un vecteur de valeurs pour les points x.
 
Y : un vecteur de valeurs pour les points y.
 
### **centers.hclust**
 
Répertorier les centres de cluster pour un cluster hiérarchique
 
Il s'écrit :
>centers.hclust(x, object, nclust=10, use.median=FALSE)
 
#### *Argument :*
 
x : Les données utilisées pour créer le cluster.
 
object : Un objet hclust.
 
nclust : Nombre de clusters.
 
use.median : Utilisez meadion au lieu de sa signification.
 
### **comcat**
 
Écho des données sous une forme lisible par l'homme.
 
Il s'écrit :
>comcat(x, ...)
 
#### *Argument :*
 
x : objet
 
… : arguments supplémentaires transmis au format.
 
 
### **binning**
 
Effectuer un binning sur des données numériques
 
Il s'écrit :
>binning(x, bins=4, method=c("quantile", "wtd.quantile", "kmeans"),
                     labels=NULL, ordered=TRUE, weights=NULL)
 
#### *Argument :*
 
x : les données numériques à bin.
 
bins : les données numériques à bin.
 
method : s'il faut utiliser le binning "quantile", quantile pondéré "wtd.quantile" ou "kmeans".
 
labels : les étiquettes ou noms à utiliser pour chacun des bacs.
 
ordered : s'il faut construire un facteur ordonné ou non.
 
weights :  vecteur de poids numériques pour chaque observation pour le regroupement quantile pondéré.
 
### **weather**
 
Exemple de jeu de données d'observations météorologiques quotidiennes depuis l'aéroport de Canberra en Australie.
 
Il s'écrit :
>weather

#### *Format : *
 
L' weather est une base de données contenant une année d'observations quotidiennes d'une seule station météorologique (Canberra).
 
### **treeset.randomForest**
 
Générer une représentation d'un arbre dans une forêt aléatoire
 
Il s'écrit :
>treeset.randomForest(model, n=1, root=1, format="R")
 
 
#### *Argument :*
 
model : un modèle randomForest
 
n : un arbre spécifique à lister
 
root : par où commencer le stree, principalement pour un usage interne
 
format : l'un des "R", "VB"

### **printRandomForests**
 
Imprimer une représentation des modèles Random Forest sur la console
 
Il s'écrit :
>printRandomForests(model, models=NULL, include.class=NULL, format="")
 
#### *Argument :*
 
model : un modèle randomForest.
 
models : une liste d'entiers limitant les modèles dans MODEL qui sont affichés.
 
include.class : limiter la sortie à la classe spécifique.
 
format : les valeurs possibles sont "VB".
 
### **riskchart**
 
Tracer un graphique des risques
 
Il s'écrit :
>riskchart(pr,
          ac,
          ri               = NULL,
          title            = "Risk Chart",
          title.size       = 10,
          subtitle         = NULL,
          caption          = TRUE,
          show.legend      = TRUE,
          optimal          = NULL,
          optimal.label    = "",
          chosen           = NULL,
          chosen.label     = "",
          include.baseline = TRUE,
          dev              = "",
          filename         = "",
          show.knots       = NULL,
          show.lift        = TRUE,
          show.precision   = TRUE,
          show.maximal     = TRUE,
          risk.name        = "Risk",
          recall.name      = "Recall",
          precision.name   = "Precision",
          thresholds       = NULL,
          legend.horiz     = TRUE)
 
#### *Argument :*
 
pr : La classe prédite pour chaque observation.
 
ac : La classe réelle pour chaque observation.
 
ri : La classe de risque pour chaque observation.
 
title : le titre principal à placer en haut de l'intrigue.
 
title.size : taille de la police du titre principal.
 
subtitle : sous-titre sous le titre principal.
 
caption : légende pour le coin inférieur droit de l'intrigue.
 
show.legend : s'il faut afficher la légende dans le tracé.
 
optimal : une charge de travail (pourcentage ou fraction) qui représente un point de performance optimal qui est également tracé. Si à la place la valeur est TRUEalors le point optimal est identifié en interne (valeur maximale pour (recall-casload)+(risk-caseload)) et tracé.
 
optimal.label : une chaîne qui est ajoutée pour étiqueter la ligne dessinée comme le point optimal.
 
chosen : une charge de travail (pourcentage ou fraction) qui représente un point de performance optimal choisi par l'utilisateur qui est également tracé.
 
chosen.label : une chaîne qui est ajoutée pour étiqueter la ligne dessinée comme le point choisi.
 
include.baseline : si TRUE (valeur par défaut), affiche la ligne de base diagonale.
 
dev : une chaîne qui, si elle est fournie, identifie un type de périphérique comme cible du tracé. Il peut s'agir de l'un des wmf(pour générer un métafichier Windows, mais uniquement disponible sur MS / Windows) pdf, ou png.
 
filename : une chaîne nommant un fichier. Si ce devn'est pas donné, l'extension du nom de fichier est utilisée pour identifier le format d'image comme l'un de ceux reconnus par l' devargument.
 
show.knots : un vecteur de valeurs de charge de travail auquel une ligne verticale doit être tracée. Ceux-ci peuvent correspondre, par exemple, à des chemins individuels à travers un arbre de décision, illustrant l'impact de chaque chemin sur la charge de travail et les performances.
 
show.lift : s'il faut étiqueter l'axe droit avec élévation.
 
show.precision : s'il faut afficher le tracé de précision.
 
show.maximal : s'il faut afficher la ligne de performance maximale.
 
risk.name : une chaîne utilisée dans la légende du tracé qui donne un nom au risque. Souvent, le risque est un montant en dollars menacé par une fraude ou du point de vue d'un prêt bancaire, c'est donc le défaut Revenue.
 
recall.name : chaîne utilisée dans la légende du tracé qui donne un nom au rappel. Le rappel est souvent le pourcentage de cas qui sont des résultats positifs, et dans la pratique, ceux-ci peuvent correspondre à des cas connus de fraude ou d'examens où un ajustement à peut-être une déclaration de revenus ou une demande de crédit a dû être effectué lors de l'examen du dossier, et donc la valeur par défaut est Adjustments.
 
precision.name : chaîne utilisée dans la légende du tracé qui donne un nom à la précision. Un nom commun pour la précision est Strike Rate, qui est la valeur par défaut ici.
 
thresholds : s'il faut afficher les scores le long de l'axe supérieur.
 
legend.horiz : s'il faut afficher une légende horizontale.
 
### **plotRisk**
 
Tracer un graphique des risques
 
Il s'écrit :
>plotRisk(cl, pr, re, ri = NULL, title = NULL,
    show.legend = TRUE, xleg = 60, yleg = 55,
    optimal = NULL, optimal.label = "", chosen = NULL, chosen.label = "",
    include.baseline = TRUE, dev = "", filename = "", show.knots = NULL,
    show.lift=TRUE, show.precision=TRUE,
    risk.name = "Risk", recall.name = "Recall",
    precision.name = "Precision")
 
#### *Argument :*
 
cl : un vecteur de nombre de cas correspondant à différents seuils de probabilité. Peut être des pourcentages (entre 0 et 100) ou des fractions (entre 0 et 1).
 
pr : un vecteur de valeurs de précision pour chaque seuil de probabilité. Peut être des pourcentages (entre 0 et 100) ou des fractions (entre 0 et 1).
 
re : un vecteur de valeurs de rappel pour chaque seuil de probabilité. Peut être des pourcentages (entre 0 et 100) ou des fractions (entre 0 et 1).
 
ri : un vecteur de valeurs de risque pour chaque seuil de probabilité. Peut être des pourcentages (entre 0 et 100) ou des fractions (entre 0 et 1).
 
title : le titre principal à placer en haut de l'intrigue.
 
show.legend : s'il faut afficher la légende dans le tracé.
 
xleg : la coordonnée x pour le placement de la légende.
 
yleg : la coordonnée y pour le placement de la légende.
 
optimal : une charge de travail (pourcentage ou fraction) qui représente un point de performance optimal qui est également tracé. Si à la place la valeur est TRUE alors le point optimal est identifié en interne (valeur maximale pour (recall-casload)+(risk-caseload)) et tracé.
 
optimal.label : une chaîne qui est ajoutée pour étiqueter la ligne dessinée comme le point optimal.
 
chosen : une charge de travail (pourcentage ou fraction) qui représente un point de performance optimal choisi par l'utilisateur qui est également tracé.
 
chosen.label : une chaîne qui est ajoutée pour étiqueter la ligne dessinée comme le point choisi.
 
include.baseline : si TRUE (valeur par défaut), affiche la ligne de base diagonale.
 
dev : une chaîne qui, si elle est fournie, identifie un type de périphérique comme cible du tracé. Il peut s'agir de l'un des wmf(pour générer un métafichier Windows, mais uniquement disponible sur MS / Windows) pdf, ou png.
 
filename : une chaîne nommant un fichier. Si dev n'est pas donné, l'extension du nom de fichier est utilisée pour identifier le format d'image comme l'un de ceux reconnus par l’argument dev.
 
show.knots : un vecteur de valeurs de charge de travail auquel une ligne verticale doit être tracée. Ceux-ci peuvent correspondre, par exemple, à des chemins individuels à travers un arbre de décision, illustrant l'impact de chaque chemin sur la charge de travail et les performances.
 
show.lift : s'il faut étiqueter l'axe droit avec élévation.
 
show.precision : s'il faut afficher le tracé de précision.
 
risk.name : une chaîne utilisée dans la légende du tracé qui donne un nom au risque. Souvent, le risque est un montant en dollars menacé par une fraude ou du point de vue d'un prêt bancaire, c'est donc le défaut Revenue.
 
recall.name : chaîne utilisée dans la légende du tracé qui donne un nom au rappel. Le rappel est souvent le pourcentage de cas qui sont des résultats positifs, et dans la pratique, ceux-ci peuvent correspondre à des cas connus de fraude ou d'examens où un ajustement à peut-être une déclaration de revenus ou une demande de crédit a dû être effectué lors de l'examen du dossier, et donc la valeur par défaut est Adjustments.
 
precision.name : chaîne utilisée dans la légende du tracé qui donne un nom à la précision. Un nom commun pour la précision est Strike Rate, qui est la valeur par défaut ici.
 
### **weatherAUS**
 
Observations météorologiques quotidiennes de plusieurs stations météorologiques australiennes.
 
Il s'écrit :
>weatherAUS
 
#### *Format :*
 
Le weatherAUS est une base de données contenant plus de 140 000 observations quotidiennes de plus de 45 stations météorologiques australiennes.
 
### **wine**
 
Le jeu de données wine du référentiel UCI Machine Learning.
 
Il s'écrit :
>wine
 
#### *Format :*
 
Une base de données contenant 178 observations de 13 variables.
 
### **whichNumerics**
 
Renvoie une liste des noms des variables numériques dans un bloc de données.
 
Il s'écrit :
>whichNumerics(data)
 
#### *Argument :*
 
data : une trame de données.
 
### **rattle**
 
Afficher l'interface utilisateur de Rattle
 
Il s'écrit :
>rattle(csvname=NULL, dataset=NULL, useGtkBuilder=TRUE)
 
#### *Argument :*
 
csvname : le nom facultatif d'un fichier CSV à charger dans Rattle au démarrage.
 
dataset : Le nom facultatif sous forme de chaîne de caractères d'un ensemble de données à charger dans Rattle au démarrage.
 
useGtkBuilder : s'il n'est pas fourni, alors détermine automatiquement s'il faut utiliser le nouveau GtkBuilder plutôt que la libglade obsolète. Un utilisateur peut remplacer le choix heuristique par TRUE ou FALSE.
 
### **genPlotTitleCmd**
 
Générer une chaîne pour ajouter un titre à un tracé
 
Il s'écrit :
>genPlotTitleCmd(..., vector=FALSE)
 
#### *Argument :*

… : une ou plusieurs chaînes qui seront collées ensemble pour former le titre principal.
 
vector : s'il faut renvoyer un vecteur comme résultat.


# Sources

[rattle.togaware.com](https://rattle.togaware.com/ "togaware")

[Using the Rattle Package with R](https://www.dummies.com/programming/using-rattle-package-r/ "Using the Rattle Package with R")

[rattle v5.4.0](https://www.rdocumentation.org/packages/rattle/versions/5.4.0 "rattle v5.4.0")

[cran.r-project.org](https://cran.r-project.org/web/packages/rattle/vignettes/rattle.pdf "cran.r-project.org")

[Rattle - Data Mining in R](https://youtu.be/ARGfOHPVERc "Rattle - Data Mining in R")
