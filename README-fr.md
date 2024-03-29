# Windows Subsystem for Linux et le Sous-système Windows pour Linux pour les nuls
Tout ce qu'il vous faut pour maîtriser Windows Subsystem for Linux, le Sous-système Windows pour Linux, ou plus simplement, WSL.

Le mot d'ordre ici, c'est rendre la chose accessible aux plus nuls, comme moi.
Si vous ne comprenez pas, cliquez sur l'onglet Issues en haut de la page et écrivez moi.
Allez, c'est parti.

J'ai découvert WSL il y a une semaine et je ne suis pas informaticien. Voilà tout ce que j'aurais aimé savoir.
(Pourquoi je me suis lancé dedans ? Pour pouvoir compiler Android pour des smartphones ancien.)



## À quoi ça sert WSL ?
Ca vous permet d'utiliser tout l'environnement Linux depuis Windows 10.
Pour coder, mais aussi utiliser certains logiciels qui ne sont que sur Linux ou compiler des logiciels Open Source comme Android.

Plus loin je parle de distribution, dans le monde Linux, une distribution est un ensemble d'applications ajoutées au noyau (le vrai Linux). Il en existe beaucoup, les distributions les plus connues sont Ubuntu, Debian, Arch, Cinnamon ...
Je vais ici utiliser Ubuntu puisque je débute.

*NB. Dans PowerShell et l'Invite de commandes Windows, vous pouvez coller une commande en faisant un clic droit.


**Ce que vous allez apprendre ici, le plus simplement du monde**
* Utiliser Ubuntu depuis Windows
* Installer WSL avec PowerShell
* Installer WSL depuis les menus Windows
* Installer Ubuntu depuis le Windows Store
* Installer Ubuntu dans WSL sans passer par le Windows Store (installation hors ligne)
* Installer Ubuntu dans WSL sur le disque ou la partition de votre choix
* Utiliser différents Ubuntu WSL en parallèle
* Déplacer de partition une distribution WSL
* Cloner WSL, créer une copie d'une distribution WSL
* Définir la distribution par défaut
* Faire une sauvegarde de votre Ubuntu WSL
* Désinstaller une distribution WSL
* Utiliser une interface graphique sur votre Linux WSL (10 minutes)
* Maitriser toutes les commandes WSL
* Éditer les fichiers d'Ubuntu WSL avec VS Code (Visual Studio Code de Microsoft)
* Ressources intéressantes


<hr>


### Installer WSL avec PowerShell (2 minutes)
Votre Windows 10 doit être en version 1903
(Pour le savoir, cliquer sur l'icône du menu démarrer, en bas à gauche de l'écran, taper winver puis cliquer sur le raccourci affiché. Dans la fenêtre qui s'ouvre, il est indiqué 1903. Si ce n'est pas le cas, lancez les mises à jour de Windows).

Maintenant, on installe le Windows Subsystem for Linux, qui est un composant additionnel de Windows 10.
Aller dans le Menu démarrer > taper Powershell > Cliquer sur *Exécuter en tant qu'administrateur* dans la panneau droit des résultats de la recherche.

(Windows PowerShell est un outil assez puissant qui permet de contrôler Windows en tapant simplement des commandes au lieu de se balader dans des menus. Imaginez la configuration de 1000 PCs avec seulement des clics :-( )

Faire un copier coller de la commande suivante :

```Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux```

Valider toutes les commandes de ce guide en appuyant sur la touche Entrée.

Patienter pendant l'installation du module, puis confirmer avec Y pour redémarrer le PC.

C'est fait.

<hr>

### Installer WSL depuis les menus Windows (2 minutes)
Alternative à la méthode avec PowerShell.
Cliquer sur le menu démarrer de Windows > taper *Activer ou désactiver des fonctionnalités Windows* > cliquer sur le raccourci portant ce nom.

Dans la liste, cocher le *Sous-système Windows pour Linux* et valider avec *OK*, redémarrer le PC.

<hr>

### Installer Ubuntu depuis le Windows Store
C'est la méthode la plus facile mais il y a 2 limitations : vous ne pouvez installer qu'un seul système à la fois et il sera placé sur le disque système (le plus souvent C:\, là où est installé Windows). Moi je manque d'espace disque, alors j'évite.

Cliquer sur le menu démarrer > taper Store > cliquer sur le raccourci vers le *Microsoft Store*.
Dans le Store, taper dans la barre de recherche en haut : Ubuntu 18.04 LTS.
L'installer et le lancer.

Au 1er lancement, il vous demande de choisir un nom d'utilisateur et un mot de passe pour *UNIX*, choisissez ce que vous voulez mais ne les oubliez pas !!!

Et voilà, vous êtes sous Ubuntu depuis Windows 10.

Mais où est l'interface graphique ? Voyez plus loin dans mon cours.

<hr>

### Installer Ubuntu dans WSL sans passer par le Windows Store (installation hors ligne, 30 minutes)

Cette méthode vous permet :
* d'installer plusieurs distributions en parallèle, soit des distributions différentes, soit la même mais avec des environnements différents, ce qui permet d'avoir une machine pour compiler Android 7 et une pour compiler Android 9. Yessss.
* d'installer la distribution de votre choix sur le disque de votre choix (quand vous manquez de place sur C:\)
* de se passer des sudo en installant une distribution root (si vous ne comprenez pas c'est normal, c'est pour les geeks)

Et tout ça sans quitter Windows 10.

Téléchargez les 2 éléments suivants :
1. [La dernière version d'Ubuntu 18.04](https://cloud-images.ubuntu.com/bionic/current/bionic-server-cloudimg-amd64-root.tar.xz)
1. [LxRunOffline](https://github.com/DDoSolitary/LxRunOffline/releases)

* Créer un dossier nommé *lxrunoffline* dans le dossier *Documents* de Windows (accessible depuis *Accès rapide* ou *Ce PC*).
* Dézipper le contenu de LxRunOffline dans ce dossier, et placer l'Ubuntu téléchargé dans ce dossier.
* Aller dans le Menu démarrer > taper *Invite de commandes* > Cliquer sur *Exécuter en tant qu'administrateur* dans la panneau droit des résultats de la recherche.
* Entrer la commande suivante ```cd /d C:\Users\NOMDUTILISATEUR\Documents\lxrunoffline``` (remplacer NOMDUTILISATEUR par votre identifiant Windows).
* Voilà le moment d'installer Ubuntu. Choisir le dossier où l'installer, et comment nommer le système. Ici je l'installe sur le disque O: et je l'appelle Ubuntu18 <br>
```lxrunoffline install -n Ubuntu18 -d O:\wsl\installed\Ubuntu18 -f bionic-server-cloudimg-amd64-root.tar.xz -s```

Dans cette commande, -n spécifie le nom du système (pour différencier plusieurs systèmes), -d le dossier de destination, -f le fichier d'installation d'Ubuntu (ne pas le changer) et -s va créer un raccourci vers la machine WSL sur le bureau de Windows.

Valider la commande avec Entrée puis patienter pendant l'installation.

#### Afficher les distributions installées
Avec les commandes suivantes, au choix
 * ```lxrunoffline list```, et paf, l'Invite de commandes renvoie le nom du système installé, ici Ubuntu18.
 * ou ```wsl --list --all```
 * ou ```wslconfig /list```


On peut ainsi installer autant de distributions que l'on veut.

#### Pour lancer le système avec une seule distribution installée, taper dans l'Invite de commandes
* ```wsl```, la commande officielle du WSL
* ou avec LxRunOffline ```lxrunoffline run -n Ubuntu18``` (l'Invite de commande doit être en mode administrateur ET positionné dans le dossier Documents\lxrunoffline où LxRunOffline a été dézippé. Pour se positionner dedans, entrer ```cd /d C:\Users\NOMDUTILISATEUR\Documents\lxrunoffline```).

La commande affiche alors ```root@UTILISATEURWINDOWS```, ce qui veut dire que l'on est dans Linux.

Pas convaincu ? Taper ```lsb_release -a``` et paf, le shell Affiche : Ubuntu 18.04 !!!

<hr>

#### Pour quitter ou fermer Linux/la distribution WSL
* Taper ```exit```
* ou ```wsl -t NOMDELADISTRIBUTION```


<hr>


### Utiliser différents Ubuntu ou distributions WSL en parallèle (10 minutes)

Répéter l'opération du chapitre précédent pour installer une distribution en spécifiant un autre nom et un autre dossier de destination à LxRunOffline.

Par exemple : ```lxrunoffline install -n Android9 -d O:\wsl\installed\Android9 -f bionic-server-cloudimg-amd64-root.tar.xz``` ou cloner la distribution (voir chapitres suivants).

Pour lancer le système avec plusieurs distributions installées, taper dans l'Invite de commandes
* ```lxrunoffline run -n NOMDELADISTRIBUTION``` (l'Invite de commande doit être en mode administrateur ET positionné dans le dossier Documents\lxrunoffline où LxRunOffline a été dézippé. Pour se positionner dedans, entrer ```cd /d C:\Users\NOMDUTILISATEUR\Documents\lxrunoffline```).
* ou simplement ```wsl```, qui démarrera la distribution WSL par défaut (voir les chaptitres suivants).

Pour lancer plusieurs systèmes en parallèle, il suffit d'ouvrir autant d'Invites de commandes que de systèmes à lancer, et de spécifier
* ```wsl --distribution NOMDELADISTRIBUTION```
* ou ```lxrunoffline run -n NOMDELADISTRIBUTION```

<hr>

### Déplacer une distribution WSL (dépend de la taille du système à déplacer)

LxRunOffline permet aussi de déplacer une distribution, qui prrendrait trop de place par exemple, pour libérer un disque.
Je ne répète plus comment utiliser LxRunOffline (voir les chapitres précedents).
```lxrunoffline move -n NOMDELADISTRIBUTION -d D:\WSL\Ubuntu18```

Ici avec -n NOMDELADISTRIBUTION on spécifie le système, pour moi toujours -n Ubuntu18,
avec -d on spécifie le dossier où elle sera placée : D:\WSL\Ubuntu18

<hr>

### Cloner WSL, créer une copie d'une distribution WSL (dépend de la taille du système à déplacer)

Très utile pour avoir 2 environnements différents mais avec un travail de configuration initiale identique.
```lxrunoffline duplicate -n NOMDELADISTRIBUTION -d O:\wsl\installed\Android8 -N Android8```

Où -n NOMDELADISTRIBUTION désigne le système à cloner -n Ubuntu18 dans mon cas.
-d O:\wsl\installed\Android8 le dossier où va être placé le clone
et -N Android8 le nom de ma système cloné

<hr>

### Définir la distribution par défaut (1 minute)

Si vous utilisez plusieurs machines, vous voulez changer celle qui se lance par défaut.
Pour celà, utilisez 

* ```wslconfig /setdefault NOMDELADISTRIBUTION```
* ou ```wsl --setdefault NOMDELADISTRIBUTION```
* ou avec lxrunoffline : ```lxrunoffline set-default -n NOMDELADISTRIBUTION```

<hr>

### Faire une sauvegarde d'une distribution WSL (dépend de la taille du système à déplacer)

Après un long de travail de configuration, on veut mettre le système en lieu sûr. Tout simplement avec 
```lxrunoffline export -n NOMDELADISTRIBUTION -f O:\wsl\sauvegarde Ubuntu18 wsl.tar.gz```

Où -f O:\wsl\sauvegarde Ubuntu18 wsl.tar.gz désigne le dossier et le nom de la sauvegarde, en n'oubliant pas de préciser .tar.gz à la fin.
Un fichier .xml est aussi enregistré.

En cas de besoin, ce système peut être réinstallé en 2 minutes avec le classique ```lxrunoffline install -n Ubuntu18 -d O:\wsl\installed\Ubuntu18 -f O:\wsl\sauvegarde Ubuntu18 wsl.tar.gz```

<hr>

### Désinstaller une distribution WSL (dépend de la taille du système à supprimer)

Entrer dans l'Invite de commande :

* ```wslconfig /u NOMDELADISTRIBUTION```
* ou ```wsl --unregister NOMDELADISTRIBUTION```
* Avec lxrunoffline : ```lxrunoffline uninstall -n NOMDELADISTRIBUTION```

<hr>

### Utiliser une interface graphique sur votre Linux WSL (10 minutes)

Envie de pouvoir utiliser Linux avec la souris comme sur un vrai PC ? C'est possible. Ici la démo en partant du Ubuntu installé manuellement détaillé plus haut.

* Dans l'Invite de commande avec votre Distribution active, installez la distribution Ubuntu complète : ```apt-get install ubuntu-desktop```. Le téléchargement demande 1,5 Go de fichiers. Patientez.
* On enchaine avec l'installation de du moteur de rendu XFCE4 : ```apt install xfce4```
* Maintenant, dans Windows 10, télécharger la dernière version de *VcXSrv* : https://sourceforge.net/projects/vcxsrv/files/vcxsrv/
* Dans le menu démarrer de Windows, chercher et lancer *Xlaunch*, pour l'affichage, préférer *One large window without tilebar*. Laisser les autres options par défaut. Authoriser l'accès Firewall de Windows.
* Dans l'Invite de commande avec la distribution WSL en cours, taper ```export DISPLAY=:0```
* puis ```xfce4-session```
* Dans *Xlaunch* on peut enfin prendre en main la distribution WSL avec une interface graphique !

Un grand merci à https://www.reddit.com/r/Windows10/comments/8dnyig/using_a_gui_with_wsl_on_windows_10_ubuntu_wsl/

<hr>

### Ressources intéressantes

https://www.pofilo.fr/post/20190727-terminator/

https://www.howtogeek.com/344688/how-to-set-your-default-linux-distribution-on-windows-10/

https://docs.microsoft.com/fr-fr/windows/wsl/wsl-config

https://adamtheautomator.com/windows-subsystem-for-linux/
